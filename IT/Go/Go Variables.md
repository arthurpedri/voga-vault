```go
// create a new variable, it defaults to 0
// (the "zero value" for ints)
var mySkillIssues int

// Short variable declaration:
myVariable := 42
```
The walrus operator, `:=`, declares a new variable and assigns a value to it in one line. Go can infer the type.
## When to Use the Walrus Operator
The `:=`, (walrus operator) should be used instead of [var](https://go.dev/tour/basics/9) style declarations basically anywhere possible. The limitation is that `:=` can't be used outside of a function (in the [global/package scope](https://dave.cheney.net/2017/06/11/go-without-package-scoped-variables))
[[Go Types]]
### Same Line Declarations
You can declare multiple variables on the same line:
```go
mileage, company := 80276, "Toyota"
```
# Constants
Constants are declared with the `const` keyword. They can't use the `:=` short declaration syntax.
```go
const pi = 3.14159
```
Constants can be primitive types like strings, integers, booleans and floats. They _cannot_ be more complex types like slices, maps and structs
## Go-Style Syntax
Go's declarations are clear, you just read them left to right, just like you would in English.
```go
x int
p *int
a [3]int
```
It's nice for more complex signatures, it makes them easier to read.
```go
f func(func(int,int) int, int) int
```
