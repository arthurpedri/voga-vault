### Prints
- `fmt.Print`
- `fmt.Printf`: with formatting (`%v, %d, %.2f`)
- `fmt.Println`
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
- Like slices, maps are passed by reference into functions.
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
- If `key` is in `m`, then `ok` is `true` and `elem` is the value as expected.
- If `key` is not in the map, then `ok` is `false` and `elem` is the zero value for the map's element type.
