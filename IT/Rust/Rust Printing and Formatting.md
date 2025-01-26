## Comments
- _Regular comments_ which are ignored by the compiler:
    - `// Line comments which go to the end of the line.`
    - `/* Block comments which go to the closing delimiter. */`
- _Doc comments_ which are parsed into HTML library [documentation](https://doc.rust-lang.org/stable/rust-by-example/meta/doc.html):
    - `/// Generate library docs for the following item.`
    - `//! Generate library docs for the enclosing item.`

## Formatted print
Printing is handled by a series of [`macros`](https://doc.rust-lang.org/stable/rust-by-example/macros.html) defined in [`std::fmt`](https://doc.rust-lang.org/std/fmt/)
- Lots of options to format print, but mostly `{}` will be replaced with arguments, it can be used with integers or even named arguments to specify which argument should be used, in addition to lots of other options: `{0}, {1}, {verb}, {number:0>5}, {:b}`
## Debug 
To use the formatting traits types require an implementation to be printable. Automatic implementations are only for types such as in the `std` library, other must be implemented manually.
- All types can `derive` (automatically create) the `fmt:Debug` implementation. `fmt:Display` must by manually implemented.
```rust
// This structure cannot be printed either with `fmt::Display` or with `fmt::Debug`. 
struct UnPrintable(i32); 
// The `derive` attribute automatically creates the implementation required to make this `struct` printable with `fmt::Debug`. 
#[derive(Debug)] 
struct DebugPrintable(i32);
fn main() {
    // Printing with `{:?}` is similar to with `{}`.
    println!("{:?} months in a year.", 12);
    println!("{1:?} {0:?} is the {actor:?} name.",
             "Slater",
             "Christian",
             actor="actor's");
    // `Structure` is printable!
    println!("Now {:?} will print!", Structure(3));
    // The problem with `derive` is there is no control over how the results look. What if I want this to just show a `7`?
    println!("Now {:?} will print!", Deep(Structure(7))); // output: Now Deep(Structure(7)) will print!

    let peter = Person { name, age };
    // Pretty print
    println!("{:#?}", peter);
    /* Will print
    Person {  
        name: "Peter",  
        age: 27,  
    }
    */
}
```

## Display
Implementing `fmt::Display`, which uses the `{}` print marker allows us to customize the output appearance.
```rust
// Import (via `use`) the `fmt` module to make it available.
use std::fmt;
// Define a structure for which `fmt::Display` will be implemented. This is
// a tuple struct named `Structure` that contains an `i32`.
struct Structure(i32);

// To use the `{}` marker, the trait `fmt::Display` must be implemented
// manually for the type.
impl fmt::Display for Structure {
    // This trait requires `fmt` with this exact signature.
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        // Write strictly the first element into the supplied output
        // stream: `f`. Returns `fmt::Result` which indicates whether the
        // operation succeeded or failed. Note that `write!` uses syntax which
        // is very similar to `println!`.
        write!(f, "{}", self.0)
    }
}
```

## `?` operator
The `?` operator can be used to implement the display of a vector, since each `write!` generates a `fmt:Result`.
```rust
// Try `write!` to see if it errors. If it errors, return the error. Otherwise continue.
write!(f, "{}", value)?;
```


