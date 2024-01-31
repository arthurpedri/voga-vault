## Scalar Types
- Signed integers: `i8`, `i16`, `i32`(default), `i64`, `i128` and `isize` (pointer size)
    - Architecture size or pointer size is the size of a *word* in the architecture
- Unsigned integers: `u8`, `u16`, `u32`, `u64`, `u128` and `usize` (pointer size)
- Floating point: `f32`, `f64`(default)
- `char` Unicode scalar values like `'a'`, `'α'` and `'∞'` (4 bytes each)
- `bool` either `true` or `false`
- The unit type `()`, whose only possible value is an empty tuple: `()`
    - Despite the value of a unit type being a tuple, it is not considered a compound type because it does not contain multiple values.
## Compound Types
- Arrays like `[1, 2, 3]`
- Tuples like `(1, true)`
```rust
let a_float: f64 = 1.0;  // Regular annotation
let an_integer   = 5i32; // Suffix annotation
```
### Tuples
- Can be destructured
- Values can be extracted from tuples using tuple indexing
    - `tuple.0 + tuple.1`
- One element tuples require a comma to tell them apart from literals surrounded by parentheses
    - `(5u32,)` or `(true,)`
### Arrays
- Arrays are stored in contiguous memory
- Their **length, which is know at compile time**, is part of their type signature `[T; length]`.
- Out of bound indexing on array causes **compile time error**.
```rust
// Fixed-size array (type signature is superfluous).
let ys: [i32; 500] = [0; 500]; // All elements can be initialized to the same value.
ys.len(); // length
// Arrays are stack allocated.
println!("Array occupies {} bytes", mem::size_of_val(&ys));

// Arrays can be safely accessed using `.get`, which returns an
// `Option`. This can be matched as shown below, or used with
// `.expect()` if you would like the program to exit with a nice
// message instead of happily continue.
for i in 0..xs.len() + 1 { // Oops, one element too far!
    match xs.get(i) {
        Some(xval) => println!("{}: {}", i, xval),
        None => println!("Slow down! {} is too far!", i),
    }
}
```
### Slices
- Similar to arrays, but their **length is not know at compile time**
- A slice is a two-word object; the first word is a pointer to the data, the second word is the length of the slice
- Slices can be used to **borrow a section of an array** and have the type signature `&[T]`.
- Out of bound indexing on slice causes **runtime error**.
```rust
// Arrays can be automatically borrowed as slices.
foo(&ys);
// Slices can point to a section of an array.
// They are of the form [starting_index..ending_index].
// `starting_index` is the first position in the slice.
// `ending_index` is one more than the last position in the slice.
println!("Borrow a section of the array as a slice.");
analyze_slice(&ys[1 .. 4]);
```