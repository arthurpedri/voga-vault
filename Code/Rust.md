[[Rust Variables]]

## Data Types
### Numbers
- Signed and Unsigned integers from 8 to 128 bits and architecture size
    - Default is `i32`
    - Signed `i8, i16, i32, i64, i128, isize`
    - Unsigned `u8, u16, u32, u64, u128, usize`
    - Architecture size is the size of a *word* in the architecture
- Float default is `f64` but can also be set to `f32`
- 

## Warnings
Warnings can be allowed using the syntax `#[allow(unused_variables)]` for example.
- `let _x = 1;` will not give an unused variable warning.

