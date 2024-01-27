## Variables
Variables in Rust are immutable by default, and must be explicitly made mutable.
```rust
let x: i32 = 10;
let mut y: i32 = 10;
y += 1;
```
- `let` is used to declare variables
- `mut` is used to make a variable *[[Mutability|mutable]]*
- Type can be declared after the variable name
### Shadowing
You can declare a new variable with the same name as a previous variable, here we can say **the first one is shadowed by the second one.**
```rust
fn main() {
    let mut x: i32 = 1;
    x = 7;
    // Shadowing and re-binding
    let x = x; 
    x += 3; // This will not work because x is no longer mutable
   
    let y = 4;
    // Shadowing
    let y = "I can also be bound to text!"; 
}
```

### Destructuring
- The `mut` keyword can be used when destructuring 
```rust
let (mut x, y) =  (1, 2);
x += 2;

let (x, y);
(x, ..) = (3, 4);
[.., y] = [1, 2];
assert_eq!([x,y], [3, 2]);
```