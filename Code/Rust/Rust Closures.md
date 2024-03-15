## Closures
- Closures are functions that can capture the enclosing environment.
- Calling a closure is exactly like calling a function. However, both input and return types _can_ be inferred and input variable names _must_ be specified.
- They use `||` instead of `()` around input variables.
```rust
fn main() {
    let outer_var = 42;
    // A regular function can't refer to variables in the enclosing environment
    // Closures are anonymous, here we are binding them to references.
    // Annotation is identical to function annotation but is optional
    // as are the `{}` wrapping the body. These nameless functions
    // are assigned to appropriately named variables.
    let closure_annotated = |i: i32| -> i32 { i + outer_var };
    let closure_inferred  = |i     |          i + outer_var  ;

    println!("closure_annotated: {}", closure_annotated(1));
    println!("closure_inferred: {}", closure_inferred(1));
    // Once closure's type has been inferred, it cannot be inferred again with another type.
    
    // A closure taking no arguments which returns an `i32`.
    // The return type is inferred.
    let one = || 1;
    println!("closure returning one: {}", one());
}
```

Still missing all pages for closures https://doc.rust-lang.org/stable/rust-by-example/fn/closures/capture.html