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
## Spread Operator
- The spread `...` operator allows us to pass a slice _into_ a [[Go Functions#Variatic|variatic]] function. The spread operator consists of three dots following the slice in the function call.
```go 
names := []string{"bob", "sue", "alice"}
printStrings(names...)
```
## Append
The built-in append function is used to dynamically add elements to a slice:
```go
func append(slice []Type, elems ...Type) []Type
```
If the underlying array is not large enough, `append()` will create a new underlying array and point the returned slice to it.

Notice that `append()` is variadic, the following are all valid:
```go
slice = append(slice, oneThing)
slice = append(slice, firstThing, secondThing)
slice = append(slice, anotherSlice...)
```
The `append()` function changes the underlying array of its parameter AND returns a new slice. This means that using `append()` on anything other than itself is usually a BAD idea.
```go
// don't do this!
someSlice = append(otherSlice, element)
```
The `append()` function only creates a new array when there isn't any capacity left.

Again, to avoid bugs like this, you should ==always== use the `append` function on the same slice the result is assigned to:
```go
mySlice := []int{1, 2, 3}
mySlice = append(mySlice, 4)
```
## Range
Go provides syntactic sugar to iterate easily over elements of a slice:
```go
for INDEX, ELEMENT := range SLICE {
}
```
The element is a copy of the value at that index.
```go
fruits := []string{"apple", "banana", "grape"}
for i, fruit := range fruits {
    fmt.Println(i, fruit)
}
// 0 apple
// 1 banana
// 2 grape
```
## Slice of Slices
Slices can hold other slices, effectively creating a [matrix](https://en.wikipedia.org/wiki/Matrix_\(mathematics\)), or a 2D slice.
```go
rows := [][]int{}
rows = append(rows, []int{1, 2, 3})
rows = append(rows, []int{4, 5, 6})
fmt.Println(rows)
// [[1 2 3] [4 5 6]]
matrix := make([][]int, rows)
	for i := 0; i < rows; i++ {
		matrix[i] = make([]int, cols)
		for j := 0; j < cols; j++ {
			matrix[i][j] = i * j
		}
	}
```