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
- `array[inclusive:exclusive]` or `array[:]` or `array[2:]`, etc..
- Slices hold references to an underlying array, and if you assign one slice to another, both refer to the **same** array
-  If a function takes a slice argument, any changes it makes to the elements of the slice _will be visible to the caller_, analogous to passing a [pointer](https://en.wikipedia.org/wiki/Pointer_%28computer_programming%29) to the underlying array.
- The `make` function can create a slice filled with the zero value of the type
- A slice literal is similar to an array but without the size inside the square brackets
```go
myArray := [3]int{1, 2, 3}
mySlice := []int{1, 2, 3}
```
- Different from arrays, slices will **automatically grow as needed**

### Foreach
Go has a `foreach`-like syntax. It supports arrays/slices, maps and channels.

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
