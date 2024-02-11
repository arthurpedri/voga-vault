## Structures
There are three types of structures ("structs") that can be created using the `struct` keyword:
- Tuple structs, which are, basically, named tuples.
- The classic [C structs](https://en.wikipedia.org/wiki/Struct_(C_programming_language))
- Unit structs, which are field-less, are useful for generics.
```rust
struct Person {
    name: String,
    age: u8,
}

// A unit struct
struct Unit;

// A tuple struct
struct Pair(i32, f32);
```
- New instances can be created from other instances with struct update syntax:
```rust
let user2 = User {
    active: user1.active,
    username: user1.username,
    email: String::from("another@example.com"),
    sign_in_count: user1.sign_in_count,
};
// is the same as:
let user2 = User {
    email: String::from("another@example.com"),
    ..user1
};
```
## Enums
```rust
// Create an `enum` to classify a web event. Note how both
// names and type information together specify the variant:
// `PageLoad != PageUnload` and `KeyPress(char) != Paste(String)`.
// Each is different and independent.
enum WebEvent {
    // An `enum` variant may either be `unit-like`,
    PageLoad,
    PageUnload,
    // like tuple structs,
    KeyPress(char),
    Paste(String),
    // or c-like structures.
    Click { x: i64, y: i64 },
}
let pressed = WebEvent::KeyPress('x');
```
### Alias and use scoping
```rust
enum VeryVerboseEnumOfThingsToDoWithNumbers {
    Add,
    Subtract,
}
impl VeryVerboseEnumOfThingsToDoWithNumbers {
    fn run(&self, x: i32, y: i32) -> i32 {
        match self {
            Self::Add => x + y,
            Self::Subtract => x - y,
        }
    }
}

enum Status {
    Rich,
    Poor,
}

// Creates a type alias
type Operations = VeryVerboseEnumOfThingsToDoWithNumbers;

fn main() {
    // We can refer to each variant via its alias, not its long and inconvenient
    // name.
    let x = Operations::Add;
    
    use crate::Operations::*;
    use crate::Status::{Poor, Rich};

    // Equivalent to `Status::Poor`.
    let status = Poor;
    match status {
        // Note the lack of scoping because of the explicit `use` above.
        Rich => println!("The rich have lots of money!"),
        Poor => println!("The poor have no money..."),
    }
}
```
- The most common place where aliases are used in in the `impl` block using the `self` alias
- Enums can also be used as C-like enums
```rust
// enum with implicit discriminator (starts at 0)
enum Number {
    Zero,
    One,
    Two,
}

// enum with explicit discriminator
enum Color {
    Red = 0xff0000,
    Green = 0x00ff00,
    Blue = 0x0000ff,
}

fn main() {
    // `enums` can be cast as integers.
    println!("zero is {}", Number::Zero as i32);
    println!("one is {}", Number::One as i32);

    println!("roses are #{:06x}", Color::Red as i32);
    println!("violets are #{:06x}", Color::Blue as i32);
}
```

## Constants
Rust has two different types of constants which can be declared in any scope including global. Both require explicit type annotation:
- `const`: An unchangeable value (the common case).
- `static`: A possibly mutable variable with [`'static`](https://doc.rust-lang.org/stable/rust-by-example/scope/lifetime/static_lifetime.html) lifetime. The static lifetime is inferred and does not have to be specified. Accessing or modifying a mutable static variable is [`unsafe`](https://doc.rust-lang.org/stable/rust-by-example/unsafe.html).