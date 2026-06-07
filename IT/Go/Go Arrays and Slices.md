### Arrays
Arrays are fixed in size, like `[10]int`, you can't add more elements, while slices are dynamically-sized
## Slice
The zero value of slice is `nil`
- Slices hold references to an underlying array, and if you assign one slice to another, both refer to the **same** array
-  If a function takes a slice argument, any changes it makes to the elements of the slice _will be visible to the caller_, analogous to passing a [pointer](https://en.wikipedia.org/wiki/Pointer_%28computer_programming%29) to the underlying array.
- The `make` function can create a slice filled with the zero value of the type
```go
// func make([]T, len, cap) []T
mySlice := make([]int, 5, 10)

// the capacity argument is usually omitted and defaults to the length
mySlice := make([]int, 5)
```
- A slice literal is similar to an array but without the size inside the square brackets
```go
myArray := [3]int{1, 2, 3}
myOtherArray := [5]int{}
mySlice := []int{1, 2, 3}
```
- Different from arrays, slices will **automatically grow as needed**
-  The `append()` function only creates a new array when there isn't any capacity left, so if we use append on different slices it can cause the underlying array to be overwritten. To avoid bugs like this, you should always use the `append` function on the same slice the result is assigned to:
```go
mySlice := []int{1, 2, 3}
mySlice = append(mySlice, 4)
```
### Fixed underlying array consequences
A Read function can **accept a slice argument rather than a pointer and a count**; the length within the slice sets an upper limit of how much data to read.
```go
func (f *File) Read(buf []byte) (n int, err error)
```
### Creating slices from arrays
- `slice := array[inclusive:exclusive]` or `array[:]` or `array[2:]`, etc..
### Length
The length of a slice is simply the number of elements it contains. It is accessed using the built-in `len()` function:
```go
mySlice := []string{"I", "love", "go"}
fmt.Println(len(mySlice)) // 3
```
### Capacity
The capacity of a slice is the number of elements in the underlying array, counting from the first element in the slice. It is accessed using the built-in `cap()` function:
```go
mySlice := []string{"I", "love", "go"}
fmt.Println(cap(mySlice)) // 3
```
Generally speaking, unless you're hyper-optimizing the memory usage of your program, you don't need to worry about the capacity of a slice because it will automatically grow as needed.