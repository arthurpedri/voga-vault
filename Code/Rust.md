[[Rust Variables]]

[[Rust Printing and Formatting]]

[[Rust Primitives]]

[[Rust Custom Types]]

[[Rust Types]]

## Expressions
- Blocks are expressions too, so they can be used as values in assignments. 
- The last expression in the block will be assigned to the place expression.
- If the last expression of the blocks ends with a semicolon, the return value will be `()`.
```rust
fn main() {
    let x = 5u32;
    let y = {
        let x_squared = x * x;
        let x_cube = x_squared * x;
        // This expression will be assigned to `y`
        x_cube + x_squared + x
    };
    let z = {
        // The semicolon suppresses this expression and `()` is assigned to `z`
        2 * x;
    };
}
```

[[Rust Control Flow]]

[[Rust Functions]]

[[Rust Modules]]

[[Rust Hash Maps]]

[[Rust Traits]]

## Arrays and Vectors
- An array in Rust is stored on the stack (meaning it can't grow or shrink, and the size needs to be known at compile time)
- A Vector is stored in the heap (where these restrictions do not apply)
## Warnings
Warnings can be allowed using the syntax `#[allow(unused_variables)]` for example.
- `let _x = 1;` will not give an unused variable warning.

