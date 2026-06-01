- The zero value of a map is `nil`.
- We can create a map by using a literal or by using the `make()` function:
- Like slices, maps are passed by reference into functions and hold references to an underlying data structure.
- We can use a map of bools to act as a set.
- Map keys may be of any type that is comparable.
```go
ages := make(map[string]int)
ages["John"] = 37
// or
ages = map[string]int{
  "John": 37,
  "Mary": 21,
}
```
#### Mutations:
```go
m[key] = elem // Insertion
elem = m[key] // Get element
delete(m, key) // Delete
elem, ok := m[key] // Check if a key exists
```
- ==Comma ok== idiom will help with checking if a key exists in the map:
- If `key` is in `m`, then `ok` is `true` and `elem` is the value as expected.
- If `key` is not in the map, then `ok` is `false` and `elem` is the zero value for the map's element type.
#### Key types
- Map keys may be of any type that is comparable
    - Slices, maps and functions cannot be compared using `==` and may not be used as map keys
- Structs can be useful as map keys