## Control Flow
### If/Else
- The boolean condition doesn't need to be surrounded by parenthesis.
```rust
if n < 0 {
    print!("{} is negative", n);
} else if n > 0 {
    print!("{} is positive", n);
} else {
    print!("{} is zero", n);
}
```
### Loop
- `loop` keyword indicates an infinite loop. `break` and `continue` work as usual.
- Loops can have a return value after the `break`: 
```rust
let result = loop {
        counter += 1;
        if counter == 10 {
            break counter * 2;
        }
    };
```
### Labels
- `for` and `loop` loops can be broken out of with labels from an inner loop with a `'label` annotation.
```rust
fn main() {
    'outer: loop {
        println!("Entered the outer loop");
        'inner: loop {
            println!("Entered the inner loop");
            // This breaks the outer loop
            break 'outer;
        }
        println!("This point will never be reached");
    }
    println!("Exited the outer loop");
}
```
### While
```rust
let mut n = 1;
while n < 101 {
    n += 1;
}
```
### For and ranges
- `for in` can be used to iterate through an [[Rust Traits#Iterators|iterator]]
- An easy way to create an iterator is to use the range notation `a..b`. This yields values from `a`(inclusive) to `b`(exclusive)
- The range notation can alternatively be used as `a..=b` so the range is inclusive on both ends
```rust
// `n` will take the values: 1, 2, ..., 100 in each iteration
for n in 1..=100 {
    if n % 15 == 0 {
        println!("fizzbuzz");
    } else if n % 3 == 0 {
        println!("fizz");
    } else if n % 5 == 0 {
        println!("buzz");
    } else {
        println!("{}", n);
    }
}
```
#### For and iterators
`into_iter`, `iter` and `iter_mut` all handle the conversion of a collection into an iterator in different ways, by providing different views on the data within.
- `iter` - This borrows each element of the collection through each iteration. Thus leaving the collection untouched and available for reuse after the loop.
```rust
fn main() {
    let names = vec!["Bob", "Frank", "Ferris"];

    for name in names.iter() {
        match name {
            &"Ferris" => println!("There is a rustacean among us!"),
            _ => println!("Hello {}", name),
        }
    }
    println!("names: {:?}", names);
}
```
- `into_iter` - This consumes the collection so that on each iteration the exact data is provided. Once the collection has been consumed it is no longer available for reuse as it has been 'moved' within the loop.
```rust
fn main() {
    let names = vec!["Bob", "Frank", "Ferris"];

    for name in names.into_iter() {
        match name {
            "Ferris" => println!("There is a rustacean among us!"),
            _ => println!("Hello {}", name),
        }
    }
    println!("names: {:?}", names); // This line will give a borrow of moved value error
}
```
- `iter_mut` - This mutably borrows each element of the collection, allowing for the collection to be modified in place.
```rust
fn main() {
    let mut names = vec!["Bob", "Frank", "Ferris"];

    for name in names.iter_mut() {
        *name = match name {
            &mut "Ferris" => "There is a rustacean among us!",
            _ => "Hello",
        }
    }
    println!("names: {:?}", names);
}
```
In the above snippets note the type of `match` branch, that is the key difference in the types of iteration. The difference in type then of course implies differing actions that are able to be performed.

### Match
Pattern matching with the `match` keyword, functions similarly to `switch` in C. 
```rust
fn main() {
    let number = 13;
    match number {
        // Match a single value
        1 => println!("One!"),
        // Match several values
        2 | 3 | 5 | 7 | 11 => println!("This is a prime"),
        // Match an inclusive range
        13..=19 => println!("A teen"),
        // Handle the rest of cases
        _ => println!("Ain't special"),
    }

    let boolean = true;
    // Match is an expression too
    let binary = match boolean {
        // The arms of a match must cover all the possible values
        false => 0,
        true => 1,
    };
}
```
Match blocks can be [[Rust Destructuring|destructured]] in a variety of ways.
#### Guards
- `match` guards can be added to filter the arm.
- The compiler won't take guard conditions into account when checking if all patterns are covered by the match expression.
```rust
fn main() {
    let number: u8 = 4;

    match number {
        i if i == 0 => println!("Zero"),
        i if i > 0 => println!("Greater than zero"),
        _ => unreachable!("Should never happen."), // If this was not added the compiler would throw a non-exhaustive patterns error
    }
}
```
#### Binding
Indirectly accessing a variable makes it impossible to branch and use that variable without re-binding. `match` provides the `@` sigil for binding values to names:
```rust
match age() {
    0             => println!("I haven't celebrated my first birthday yet"),
    // Could `match` 1 ..= 12 directly but then what age
    // would the child be? Instead, bind to `n` for the
    // sequence of 1 ..= 12. Now the age can be reported.
    n @ 1  ..= 12 => println!("I'm a child of age {:?}", n),
    n @ 13 ..= 19 => println!("I'm a teen of age {:?}", n),
    // Nothing bound. Return the result.
    n             => println!("I'm an old person of age {:?}", n),
}
```
You can also use binding to "destructure" `enum` variants, such as `Option`:
```rust
fn some_number() -> Option<u32> {
    Some(42)
}

fn main() {
    match some_number() {
        // Got `Some` variant, match if its value, bound to `n`,
        // is equal to 42.
        Some(n @ 42) => println!("The Answer: {}!", n),
        // Match any other number.
        Some(n)      => println!("Not interesting... {}", n),
        // Match anything else (`None` variant).
        _            => (),
    }
}
```

### If let
The `if let` construct reads: "if `let` destructures `number` into `Some(i)`, evaluate the block (`{}`).
```rust
fn main() {
    // All have type `Option<i32>`
    let number = Some(7);
    let letter: Option<i32> = None;
    let emoticon: Option<i32> = None;

    // The `if let` construct reads: "if `let` destructures `number` into
    // `Some(i)`, evaluate the block (`{}`).
    if let Some(i) = number {
        println!("Matched {:?}!", i);
    }

    // If you need to specify a failure, use an else:
    if let Some(i) = letter {
        println!("Matched {:?}!", i);
    } else {
        // Destructure failed. Change to the failure case.
        println!("Didn't match a number. Let's go with a letter!");
    }

    // Provide an altered failing condition.
    let i_like_letters = false;

    if let Some(i) = emoticon {
        println!("Matched {:?}!", i);
    // Destructure failed. Evaluate an `else if` condition to see if the
    // alternate failure branch should be taken:
    } else if i_like_letters {
        println!("Didn't match a number. Let's go with a letter!");
    } else {
        // The condition evaluated false. This branch is the default:
        println!("I don't like letters. Let's go with an emoticon :)!");
    }
}
```
- Also works for enums, and can be used even in cases where the enum doesn't implement `PartialEq`
```rust
// This enum purposely neither implements nor derives PartialEq.
// That is why comparing Foo::Bar == a fails below.
enum Foo {Bar}

fn main() {
    let a = Foo::Bar;

    // Variable a matches Foo::Bar
    if let Foo::Bar == a {
    // ^-- this causes a compile-time error without `let`.
        println!("a is foobar");
    }
}
```

### Let-else
- With `let`-`else`, a refutable pattern can match and bind variables in the surrounding scope like a normal `let`, or else diverge (e.g. `break`, `return`, `panic!`) when the pattern doesn't match.
```rust
fn get_count_item(s: &str) -> (u64, &str) {
    let mut it = s.split(' ');
    let (Some(count_str), Some(item)) = (it.next(), it.next()) else {
        panic!("Can't segment count item pair: '{s}'");
    };
    let Ok(count) = u64::from_str(count_str) else {
        panic!("Can't parse integer: '{count_str}'");
    };
    (count, item)
}
```
- The scope of name bindings is the main thing that makes this different from `match` or `if let`-`else` expressions. You could previously approximate these patterns with an unfortunate bit of repetition and an outer `let`:
```rust
let (count_str, item) = match (it.next(), it.next()) {
    (Some(count_str), Some(item)) => (count_str, item),
    _ => panic!("Can't segment count item pair: '{s}'"),
};
let count = if let Ok(count) = u64::from_str(count_str) {
    count
} else {
    panic!("Can't parse integer: '{count_str}'");
};
```

### While let
Similar to `if let`, `while let` can make awkward `match` sequences more tolerable. Consider the following sequence that increments `i`:
```rust
// Make `optional` of type `Option<i32>`
let mut optional = Some(0);

// This reads: "while `let` destructures `optional` into
// `Some(i)`, evaluate the block (`{}`). Else `break`.
while let Some(i) = optional {
    if i > 9 {
        println!("Greater than 9, quit!");
        optional = None;
    } else {
        println!("`i` is `{:?}`. Try again.", i);
        optional = Some(i + 1);
    }
    // ^ Less rightward drift and doesn't require
    // explicitly handling the failing case.
}
// ^ `if let` had additional optional `else`/`else if`
// clauses. `while let` does not have these.
```