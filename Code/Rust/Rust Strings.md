Rust has two string types, a string slice (`&str`) and an owned string (`String`).



### Useful Methods
- `replace`: replaces all matches of a pattern with another string
- `trim`: returns a string slice with leading and trailing whitespace removed


## Format macro
the `format!` macro creates a `String` using interpolation of runtime expressions
```rust
format!("test");                             // => "test"
format!("hello {}", "world!");               // => "hello world!"
format!("x = {}, y = {val}", 10, val = 30);  // => "x = 10, y = 30"
let (x, y) = (1, 2);
format!("{x} + {y} = 3");                    // => "1 + 2 = 3"
```