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