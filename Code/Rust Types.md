## Types
### Casting
Explicit type conversion (casting) can be performed using the `as` keyword.
```rust
let decimal = 65.4321_f32;

let integer: u8 = decimal; // Error! No implicit conversion

// Explicit conversion
let integer = decimal as u8;
let character = integer as char;

// Error! There are limitations in conversion rules.
// A float cannot be directly converted to a char.
let character = decimal as char;
```
Since Rust 1.45, the `as` keyword performs a *saturating cast* when casting from float to int. If the floating point value exceeds the upper bound or is less than the lower bound, the returned value will be equal to the bound crossed.
```rust
// 300.0 as u8 is 255
println!(" 300.0 as u8 is : {}", 300.0_f32 as u8);
// -100.0 as u8 is 0
println!("-100.0 as u8 is : {}", -100.0_f32 as u8);
// nan as u8 is 0
println!("   nan as u8 is : {}", f32::NAN as u8);
```
### Literals
```rust
let a_float: f64 = 1.0;  // Regular annotation
let an_integer   = 5i32; // Suffix annotation

// Unsuffixed literals, their types depend on how they are used
let i = 1;
let f = 1.0;
```
### Inference
The type inference engine also looks at how the variable is used afterwards to infer its type, in addition to the value expression during initiatlization.
```rust
// Because of the annotation, the compiler knows that `elem` has type u8.
let elem = 5u8;

// Create an empty vector (a growable array).
let mut vec = Vec::new();
// At this point the compiler doesn't know the exact type of `vec`, it
// just knows that it's a vector of something (`Vec<_>`).

// Insert `elem` in the vector.
vec.push(elem);
// Aha! Now the compiler knows that `vec` is a vector of `u8`s (`Vec<u8>`)
```
### Aliasing
The `type` statement can be used to give a new name to an existing type. Types must have `UpperCamelCase` names, or the compiler will raise a warning. The exception to this rule are the primitive types: `usize`, `f32`, etc.
```rust
// `NanoSecond`, `Inch`, and `U64` are new names for `u64`.
type NanoSecond = u64;
type Inch = u64;
type U64 = u64;
fn main() {
    // `NanoSecond` = `Inch` = `U64` = `u64`.
    let nanoseconds: NanoSecond = 5 as U64;
}
```
- Type aliases ==don't== provide any extra type safety, because **==aliases are not new types==**.
- The main use of aliases is to reduce boilerplate.

## Conversion
- Primitive types can be converted to each other through [[#Casting]].
- Conversion between custom types is done (`struct, enum`) by using [[Rust Traits|traits]]. Generic conversions will use the `From` and `Into` traits.  
- There are specific traits for converting the more common cases, in particular converting to and from `String`.

### From and Into
```rust
impl From<i32> for Number {
    fn from(item: i32) -> Self {
        Number { value: item }
    }
}

impl Into<Number> for i32 {
    fn into(self) -> Number {
        Number { value: self }
    }
}

fn main() {
    let num = Number::from(30);
    let int = 5;
    let num: Number = int.into();
}
```

### TryFrom and TryInto
- Are generic traits for fallible conversion between types, and as such, return `Result`. 

### Converting to String
To convert any type to a `String` is as simple as implementing the [`ToString`](https://doc.rust-lang.org/std/string/trait.ToString.html) trait for the type. Rather than doing so directly, you should implement the [`fmt::Display`](https://doc.rust-lang.org/std/fmt/trait.Display.html) trait which automagically provides [`ToString`](https://doc.rust-lang.org/std/string/trait.ToString.html) and also allows printing the type as discussed in the section on [`print!`](https://doc.rust-lang.org/stable/rust-by-example/hello/print.html).
```rust
use std::fmt;

struct Circle {
    radius: i32
}

impl fmt::Display for Circle {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "Circle of radius {}", self.radius)
    }
}

fn main() {
    let circle = Circle { radius: 6 };
    println!("{}", circle.to_string());
}
```

### Parsing a String
- Can be done by specifying for type inference or using the [[Rust Turbofish|turbofish syntax]]
- The type needs to have the `FromStr` trait implemented.
```rust
fn main() {
    let parsed: i32 = "5".parse().unwrap();
    let turbo_parsed = "10".parse::<i32>().unwrap();
}
```