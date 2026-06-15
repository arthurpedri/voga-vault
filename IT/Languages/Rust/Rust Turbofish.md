## `::<SomeType>`
```rust
fn main() {
    let numbers: Vec<i32> = vec![
        1, 2, 3, 4, 5, 6, 7, 8, 9, 10,
    ];

    let even_numbers = numbers
        .into_iter()
        .filter(|n| n % 2 == 0)
        .collect(); // Error, compilator doesn't know what type 
                    // you are trying to collect
        .collect::<Vec<i32>>(); // This will work, even
                                // Vec<_> will infer correctly

    println!("{:?}", even_numbers);
}
```

## When it can't be used
- When the type signature of a function does not have a generic type
```rust
fn collect<B>(self) -> B // Can use turbofish
fn into(self) -> T // Can NOT use turbofish
```