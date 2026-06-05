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


