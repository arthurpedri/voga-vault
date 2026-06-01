[[Go IO]]
[[Go Variables]]
[[Go Runes]]
[[Go Errors]]
## Comments
```go
// This is a single line comment

/*
  This is a multi-line comment
*/
```

[[Go Slices]]

[[Go Functions]]
[[Go Conditionals]]
[[Go Loops]]
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

[[Go Maps]]

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

[[Go Pointers]]
[[Go Packages]]

[[Go Concurrency]]