## Type Sizes
Integers, [uints](https://www.cs.utah.edu/~germain/PPS/Topics/unsigned_integer.html#:~:text=Unsigned%20Integers,negative%20\(zero%20or%20positive\).), [floats](https://techterms.com/definition/floatingpoint), and [complex](https://byjus.com/maths/complex-numbers/) numbers all have type sizes.
- **Signed integers** (no decimal)
```go
int  int8  int16  int32  int64
```
- **Unsigned integers** (non-negative numbers/no decimal)
```go
uint uint8 uint16 uint32 uint64 uintptr
```
- **Signed decimal numbers**
```go
float32 float64
```
- **Complex numbers** (a complex number has a real and imaginary part)
```go
complex64 complex128
```
### Preferred sizes
The "standard" types that should be used unless you have a specific performance need (e.g. using less memory) are:
- `bool`
- `string`
- `int`
- `uint`
- `byte`
- `rune`
- `float64`
- `complex128`
## Converting Between Types
Some types can be easily converted like this:
```go
temperatureFloat := 88.26
temperatureInt := int64(temperatureFloat)
```
Casting a float to an integer in this way [truncates](https://techterms.com/definition/truncate) the floating point portion.
## [[Go Interfaces#Type Assertions|Type Assertions (Interfaces)]]

## Type Definitions
The closest thing we have to a union type is a [type definition](https://go.dev/ref/spec#Type_definitions):
```go
type sendingChannel string

const (
    Email sendingChannel = "email"
    SMS   sendingChannel = "sms"
    Phone sendingChannel = "phone"
)

func sendNotification(ch sendingChannel, message string) {
    // send the message
}
```
It's a _bit_ safer than using a plain old `string` in Go, but it's not completely safe. Go will stop us from doing this:
```go
sendingCh := "slack"
sendNotification(sendingCh, "hello") // string is not sendingChannel
```
But it _will not_ stop us from doing this:
```go
// "slack" is automatically implied as a sendingChannel
sendNotification("slack", "hello")
```
And will also _not stop_ us from doing this:
```go
sendingCh := "slack"
convertedSendingCh := sendingChannel(sendingCh)
sendNotification(convertedSendingCh, "hello")
```
The `sendingChannel` type is just a wrapper for `string`, and because we made some constants of that type, most developers will just use those constants: we've made it easy to do the right thing. That said, Go still doesn't _force_ us to do the right thing.
## Iota
Go has a language feature, that when used with a type definition (and if you squint really hard), kinda looks like an enum (but it's not). It's called `iota`.
```go
type sendingChannel int

const (
    Email sendingChannel = iota
    SMS
    Phone
)
```
The `iota` keyword is a special keyword in Go that creates a sequence of numbers. It starts at 0 and increments by 1 for each constant in the `const` block. So in the example above, `Email` is 0, `SMS` is 1, and `Phone` is 2.

Go developers sometimes use `iota` to create a sequence of constants to represent a set of related values, much like you would with an enum in other languages. _But remember, it's not an enum. It's just a sequence of numbers._