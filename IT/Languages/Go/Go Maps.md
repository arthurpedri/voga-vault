- The zero value of a map is `nil`.
- We can create a map by using a literal or by using the `make()` function:
- Like slices, maps are passed by reference into functions and hold references to an underlying data structure.
- The `len()` function works on a map, it returns the total number of key/value pairs.
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
delete(m, key) // Delete (Safe even if key is already absent from the map)
elem, ok := m[key] // Check if a key exists
```
- ==Comma ok== idiom will help with checking if a key exists in the map:
- If `key` is in `m`, then `ok` is `true` and `elem` is the value as expected.
- If `key` is not in the map, then `ok` is `false` and `elem` is the zero value for the map's element type.
#### Key types
- Map keys may be of any type that is comparable
    - Slices, maps and functions cannot be compared using `==` and may not be used as map keys
- Structs can be useful as map keys
### For, if optional arguments
- `For` and `if` statements can have more or less arguments depending on their use
- `if` statements can declare and check the condition of the variable created in the arguments of the `if`:
```go
names := map[string]int{}
missingNames := []string{}

if _, ok := names["Denna"]; !ok {
    // if the key doesn't exist yet,
    // append the name to the missingNames slice
    missingNames = append(missingNames, "Denna")
}
```
## Missing Keys
An attempt to fetch a map value with a key that is not present in the map ==will return the zero value for the type== of the entries in the map. For instance, if the map contains integers, looking up a non-existent key will return 0. 
- Using the comma ok idiom can handle if the value exists instead of returning the zero value for the map value
## Sets
We could use a map with boolean values, but a more efficient map will use empty structs, which don't take up memory space:
```go
// make(map[string]struct{})
attended := map[string]struct{}{
    "Ann": {},
    "Joe": {},
    ...
}

if _, ok := attended[person]; ok {
    fmt.Println(person, "was at the meeting")
}
attended["name"] = struct{}{} // uses 0 bytes for the empty struct
```
## Maps are not [[Thread Safety|thread-safe]]
Maps are **not** safe for concurrent use! If you have multiple goroutines accessing the same map, and at least one of them is writing to the map, you must lock your maps with a [[Go Concurrency#Mutexes|mutex]]. 
- They are only safe for concurrent read access
