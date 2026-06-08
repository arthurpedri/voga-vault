```go
func sub(x int, y int) int {
    return x-y
}

func addToDatabase(hp, damage int) {
  // Parameters of the same type next to each other only needs to be declared once after the last argument
}
```
## Passing Variables by Value
Variables in Go are passed by value (except for a few data types). "Pass by value" means that when a variable is passed into a function, that function receives a _copy_ of the variable. The function is unable to mutate the caller's original data.
```go
func main() {
    x := 5
    increment(x)

    fmt.Println(x)
    // still prints 5,
    // because the increment function
    // received a copy of x
}
```
## Ignoring Return Values
A function can return a value that the caller doesn't care about. We can explicitly ignore variables by using an underscore, or more precisely, the [blank identifier `_`](https://go.dev/doc/effective_go#blank).
```go
func getPoint() (x int, y int) {
    return 3, 4
}

// ignore y value
x, _ := getPoint()
```
# Named Return Values
Return values may be given names, and if they are, then they are treated the same as if they were new variables defined at the top of the function.
- Named return values are best thought of as a way to document the purpose of the returned values.
According to the [tour of go](https://tour.golang.org/):
> A return statement without arguments returns the named return values. This is known as a "naked" return. Naked return statements should be used only in short functions. They can harm readability in longer functions.

Named return values are what enable naked returns. Use naked returns only in short functions where the purpose of the returned values is obvious.
```go
func getCoords() (x, y int) {
	// x and y are initialized with zero values

	return // automatically returns x and y
}
```
## Good for Documentation (Understanding)
- Named return parameters are great for documenting a function. We know what the function is returning directly from its signature, no need for a comment.
- Named return parameters are particularly important in longer functions with many return values.
```go
func calculator(a, b int) (mul, div int, err error) {
    if b == 0 {
      return 0, 0, errors.New("can't divide by zero")
    }
    mul = a * b
    div = a / b
    return mul, div, nil
}
```
- ==If there are multiple return statements in a function, you don't need to write all the return values each time, though you _probably_ should.==
## Functions As Values (First-Class Functions)
Go supports [first-class](https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function) and higher-order functions. Functions are just another type -- like `int`s and `string`s and `bool`s.
```go
func add(x, y int) int {
	return x + y
}

func mul(x, y int) int {
	return x * y
}
```
We can create a new `aggregate` function that accepts a function as its 4th argument:
```go
func aggregate(a, b, c int, arithmetic func(int, int) int) int {
  firstResult := arithmetic(a, b)
  secondResult := arithmetic(firstResult, c)
  return secondResult
}
```
# Anonymous Functions
Anonymous functions are true to form in that they have _no name_. They're useful when defining a function that will only be used once or to create a quick [[Closure|closure]].
Let's say we have a function `conversions` that accepts another function, `converter` as input:
```go
// using a named function
	newX, newY, newZ := conversions(double, 1, 2, 3)
	// newX is 2, newY is 4, newZ is 6

    // using an anonymous function
	newX, newY, newZ = conversions(func(a int) int {
	    return a + a
	}, 1, 2, 3)
```
# Defer
The `defer` keyword is a fairly unique feature of Go. It allows a function to be executed automatically _just before_ its enclosing function returns. The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding function returns.

Deferred functions are typically used to clean up resources that are no longer being used. Often to close database connections, file handlers and the like.
```go
func GetUsername(dstName, srcName string) (username string, err error) {
	// Open a connection to a database
	conn, _ := db.Open(srcName)

	// Close the connection *anywhere* the GetUsername function returns
	defer conn.Close()
```
It's called:
```go
// here
return "", err
// or here
return username, nil
```
## Multiple Defers
The location of a `defer` statement inside a function matters. The deferred call is registered at the point where `defer` is executed, and it will run when the function returns. If you have multiple `defer` statements in a single function, they are executed in **last-in, first-out** order (the last deferred call runs first).

For example, you'd want to close a file before trying to remove it:
```go
func CreateTempFile() {
	f, _ := os.Create("temp-42.txt")
	defer os.Remove(f.Name()) // executed second
	defer f.Close()           // executed first

	fmt.Fprintln(f, "How many roads must a man walk down?")
}
```
# Block Scope
Unlike Python, Go is _not_ function-scoped, it's [block-scoped](https://go.dev/ref/spec#Declarations_and_scope). Variables declared inside a block are only accessible within that block (and its nested blocks). There's also the package scope. We'll talk about packages later, but for now, you can think of it as the outermost, nearly global scope.

Blocks are defined by curly braces `{}`. New blocks are created for:

- Functions
- Loops
- If statements
- Switch statements
- Select statements
- Explicit blocks
```go
package main

import "fmt"

func main() {
    {
        // explicit block
        age := 19
        // this is okay
        fmt.Println(age)
    }

    // this is not okay
    // the age variable is out of scope
    fmt.Println(age)
}
```

## Variatic functions
- Variatic functions can take an arbitrary number of FINAL arguments by using the spread operator
- A variadic function receives the variadic arguments as a [[Go Arrays and Slices#Spread Operator|slice]].
```go
func Println(a ...interface{}) (n int, err error) 
```
