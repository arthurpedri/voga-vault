Interfaces are just collections of method signatures. A type "implements" an interface if it has methods that match the interface's method signatures.

In the following example, a "shape" must be able to return its area and perimeter. Both `rect` and `circle` fulfill the interface.
```go
type shape interface {
  area() float64
  perimeter() float64
}

type rect struct {
    width, height float64
}
func (r rect) area() float64 {
    return r.width * r.height
}
func (r rect) perimeter() float64 {
    return 2*r.width + 2*r.height
}

type circle struct {
    radius float64
}
func (c circle) area() float64 {
    return math.Pi * c.radius * c.radius
}
func (c circle) perimeter() float64 {
    return 2 * math.Pi * c.radius
}
```
When a type implements an interface, it can then be used as that interface type.
```go
func printShapeData(s shape) {
	fmt.Printf("Area: %v - Perimeter: %v\n", s.area(), s.perimeter())
}
```
### Empty Interface
Because [the empty interface](https://go.dev/tour/methods/14) doesn't require a type to have any methods at all, every type automatically implements the empty interface, written as:
```go
interface{}
```
## Interface Implementation
==Interfaces are implemented _implicitly_.==
- A type never declares that it implements a given interface. If an interface exists and a type has the proper methods defined, then the type automatically fulfills that interface.
- A quick way of checking whether a struct implements an interface is to declare a function that takes an interface as an argument. If the function can take the struct as an argument, then the struct implements the interface.
## Naming Interface Parameters
We can name interface parameters to make them more clear for later implementation, but this is optional
## Type Assertions
A _type assertion_ provides access to an interface value's underlying concrete value.
```go
func printShapeInfo(s shape) {
	c, ok := s.(circle)
	if ok {
		radius := c.radius
		fmt.Printf("s is a circle, radius: %v\n", radius)
		return
	}
}
```
### Type Switches
A type switch is similar to a regular switch statement, but the cases specify _types_ instead of _values_.
```go
func printNumericValue(num interface{}) {
	switch v := num.(type) {
	case int:
		fmt.Printf("%T\n", v)
	case string:
		fmt.Printf("%T\n", v)
	default:
		fmt.Printf("%T\n", v)
	}
}
```