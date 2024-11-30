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

// Iterate from 0-9 without tracking i
for _ = range 10 {} 

// Iterate values from channel until channel is closed
for valueFromChannel := range aChannel {}
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
```go
var p *int
myString := "hello"
myStringPtr := &myString
```
- Empty pointers are `nil` pointers
- Unlike `C`, go has no pointer arithmetic
```go
msgTotal := *analytics.MessagesTotal // This creates an error
// Using selector expressions
msgTotal := analytics.MessagesTotal // Shorthand for (*analytics).MessagesTotal
```
This approach is shorthand for `(*analytics).MessagesTotal` and is the recommended, simplest way to access struct fields in Go.
- `nil` pointers will panic (runtime error) if dereferenced, check for `nil` before dereferencing them
```go
// Pointer receiver
func (c *car) setColor(color string) {
	c.color = color
}
// Non-pointer receiver
func (c car) setColor(color string) {
	c.color = color
}

c.setColor("blue") // Will change with pointer receiver only
```
- Since methods often need to modify their receiver, ==pointer receivers are more common than value receivers==
- Methods with pointer receivers don't require that a pointer is used to call the method. The pointer will automatically be derived from the value.

## Packages
- `package main` has an entrypoint at the `main()` function
- A `main` package is compiled into an executable program
- A package with any other name is a "library package" and they simply export functionality to be used by other packages
### Naming
- By *convention* a package's name is the same as the last element of its import path
```go
// for math/rand
package rand
```
### One package per directory
- A directory of Go code can have **at most** one package. All `.go` files in a directory must belong to the same package, this is true for main and library packages
- If they have more than one package the compiler will throw an error

### Clean Packages
Rules of thumb for clean, small and reusable packages.
#### Hide internal logic
- Basically [[Encapsulation]] from OOP
- Only expose the functions that need to be exported, not the internal logic
#### Don't change APIs
- Not changing exported function's signatures
- Unexported functions can and should change often, for various reasons
#### Don't export functions from the main package
- A `main` package isn't a library, there's no need to export functions from it
#### Packages shouldn't know about dependents
- A package should never have specific knowledge about a particular application that uses it
## Modules
A mule is a collection of Go packages that are released together
### One module per repo (usually)
A file named `go.mod` at the root of a project declares the module. It contains:
- The module path
- The version of the Go language your project requires
- Optionally, any external package dependencies your project has
```
module github.com/bootdotdev/exampleproject

go 1.23.0

require github.com/google/examplepackage v1.3.0
```
- Each module's path not only serves as an import path prefix for the packages within but _also indicates where the go command should look to download it_
### Standard library modules
- Modules in the standard library do not have prefixes

### Exporting
- Only **capitalized** names are exported
- Uncapitalized names are private

## Concurrency
```go
go doSomething()
```
- The `go` keyword is used to spawn a new *goroutine* and then continues executing the code concurrently

### Channels
Channels are a typed, thread-safe queue, they allow different goroutines to communicate with each other
#### Create a channel
Like maps and slices, channels must be created _before_ use. They also use the same `make` keyword:
```go
ch := make(chan int)
bufferedCh := make(chan int, 100)
```
- A buffer allows the channel to hold a fixed number of values before blocking
#### Send data to a channel
```go
ch <- 69
```
The `<-` operator is called the _channel operator_. Data flows in the direction of the arrow. This operation will ==_block_ until another goroutine is ready to receive the value==
#### Receive data from a channel
```go
v := <-ch
```
This reads and removes a value from the channel and saves it into the variable `v`. This operation will ==_block_ until there is a value in the channel to be read==
#### Receive anything on channel
```go
<-ch
```
This will block until it pops a single item off the channel, then continue, discarding the item
#### Closing channels
```go
close(ch)
```
- Channels can be checked using the same `ok` syntax:
 ```go
 v, ok := <-ch // false if the channel is empty and closed
```
- ==Sending on a closed channel will cause a panic==
- Closing isn't necessary, they will still be garbage collected if the're unused
- Close channels to indicate explicitly to a receiver that nothing else is going to come across
