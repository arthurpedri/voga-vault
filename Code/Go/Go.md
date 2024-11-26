### Prints
- `fmt.Print`
- `fmt.Printf`: with formatting (`%v, %d, %.2f`)
- `fmt.Println`

### Runes
- 32-bit integer values that represent ==Unicode code points==
- Similar to a *character* in C or any other language
- Runes are bigger than characters from other languages, they were made to represent many different types of characters, not just those in the alphabet
- The way indexing and len() work on runes are in line with runes (or int32) and not on bytes, like how `string`s work
- When you convert from `string` to `[]rune`, each utf-8 char in that string becomes a `rune`.
- Similarly, in the reverse conversion, when converting from `[]rune` to `string`, each `rune` becomes a utf-8 char in the `string`.
#### Range with strings and runes
- In strings, the `range` keyword helps by breaking out individual Unicode code points by parsing the UTF-8
```go
for pos, char := range "日本語" {
    fmt.Printf("character %c starts at byte position %d\n", char, pos)
}
// Prints
character 日 starts at byte position 0
character 本 starts at byte position 3
character 語 starts at byte position 6
// Getting first rune in a string:
s := "Hello, 世界" 
firstRune := []rune(s)[0] // Convert string to rune slice and get the first rune
```
### Errors
#### Inline errors
 ```go 
import "errors"
return errors.New("Error Name")
```

### Slices
- `array[inclusive:exclusive]` or `array[:]` or `qrray[2:]`, etc..
- Slices hold references to an underlying array, and if you assign one slice to another, both refer to the **same** array
-  If a function takes a slice argument, any changes it makes to the elements of the slice _will be visible to the caller_, analogous to passing a [pointer](https://en.wikipedia.org/wiki/Pointer_%28computer_programming%29) to the underlying array.
- The `make` function can create a slice filled with the zero value of the type
- A slice literal is similar to an array but without the size inside the square brackets
```go
myArray := [3]int{1, 2, 3}
mySlice := []int{1, 2, 3}
```
- Different from arrays, slices will **automatically grow as needed**
-  The `append()` function only creates a new array when there isn't any capacity left, so if we use append on different slices it can cause the underlying array to be overwritten. To avoid bugs like this, you should always use the `append` function on the same slice the result is assigned to:
```go
mySlice := []int{1, 2, 3}
mySlice = append(mySlice, 4)
```

### Foreach
Go has a `foreach`-like syntax. It supports arrays/slices, maps and channels.
The element is a copy of the value at that index

Iterate over an **array** or a **slice**:
```go
// index and value
for i, v := range slice {}

// index only
for i := range slice {}

// value only
for _, v := range slice {}
```

Iterate over a **map**:
```go
// key and value
for key, value := range theMap {}

// key only
for key := range theMap {}

// value only
for _, value := range theMap {}
```

### Spread Operator
- The spread `...` operator allows us to pass a slice _into_ a [[#Variatic]] function. The spread operator consists of three dots following the slice in the function call.
```go 
names := []string{"bob", "sue", "alice"}
printStrings(names...)
```

### Variatic 
- Variatic functions can take an arbitrary number of FINAL arguments by using the spread operator
```go
func Println(a ...interface{}) (n int, err error) 
```

### Maps
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

### For, if optional arguments
- `For` and `if` statements can have more or less arguments depending on their use
- A `for` argument with only a condition is the `while` in go
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

## Pointers
