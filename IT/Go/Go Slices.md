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
