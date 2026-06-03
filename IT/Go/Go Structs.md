```go
type car struct {
	brand      string
	model      string
	doors      int
	mileage    int
}
```
The fields of a struct can be accessed using the dot `.` operator.
# Anonymous Structs
An anonymous struct is just like a normal struct, but it is defined without a name and therefore cannot be referenced elsewhere in the code.
To create an anonymous struct, just instantiate the instance immediately using a second pair of brackets after declaring the type:
```go
myCar := struct {
  brand string
  model string
} {
  brand: "Toyota",
  model: "Camry",
}
```
You can even nest anonymous structs as fields within other structs:
```go
type car struct {
  brand string
  model string
  doors int
  mileage int
  // wheel is a field containing an anonymous struct
  wheel struct {
    radius int
    material string
  }
}

var myCar = car{
  brand:   "Rezvani",
  model:   "Vengeance",
  doors:   4,
  mileage: 35000,
  wheel: struct {
    radius   int
    material string
  }{
    radius:   35,
    material: "alloy",
  },
}
```
# Embedded Structs
Go is not an [object-oriented](https://en.wikipedia.org/wiki/Object-oriented_programming) language. However, embedded structs provide a kind of _data-only_ inheritance that can be useful at times. Keep in mind, Go doesn't support classes or inheritance in the _complete_ sense, but embedded structs are a way to elevate and **share fields between struct definitions.**
```go
type car struct {
  brand string
  model string
}

type truck struct {
  // "car" is embedded, so the definition of a
  // "truck" now also additionally contains all
  // of the fields of the car struct
  car
  bedSize int
}
```
## Embedded vs. Nested
- Unlike nested structs, an embedded struct's fields are accessed at the top level like normal fields.
- Like nested structs, you assign the promoted fields with the embedded struct in a [composite literal](https://golang.org/ref/spec#Composite_literals).
```go
lanesTruck := truck{
  bedSize: 10,
  car: car{
    brand: "Toyota",
    model: "Tundra",
  },
}

fmt.Println(lanesTruck.brand) // Toyota
fmt.Println(lanesTruck.model) // Tundra
```
In the example above, `car` is an embedded struct within `truck`. You can see that both `brand` and `model` are accessible from the top-level, while the nested equivalent to this object would require you to access these fields via a nested `car` struct: `lanesTruck.car.brand` or `lanesTruck.car.model`.
# Struct Methods in Go
While Go is **not** object-oriented, it does support methods that can be defined on structs. Methods are just functions that have a receiver. A receiver is a special parameter that syntactically goes _before_ the name of the function.
```go
type rect struct {
  width int
  height int
}

// area has a receiver of (r rect)
// rect is the struct
// r is the placeholder
func (r rect) area() int {
  return r.width * r.height
}

var r = rect{
  width: 5,
  height: 10,
}

fmt.Println(r.area())
// prints 50
```
A receiver is just a special kind of function parameter. In the example above, the `r` in `(r rect)` could just as easily have been `rec` or even `x`, `y` or `z`. By convention, Go code will often use the first letter of the struct's name.
- Receivers are important because they will allow us to define interfaces that our structs (and other types) can implement.
## [[Memory Layout]]
In Go, structs sit in memory in a contiguous block, with fields placed one after another as defined in the struct.
- the order of fields in a struct can have a big impact on memory usage.
- If you have a specific reason to be concerned about memory usage, aligning the fields by size (largest to smallest) can help. You can also use the [reflect package](https://pkg.go.dev/reflect) to debug the memory layout of a struct:
```go
typ := reflect.TypeOf(stats{})
fmt.Printf("Struct is %d bytes\n", typ.Size())
```
## Empty Structs
Empty structs are used in Go as a unary value.
```go
// anonymous empty struct type
empty := struct{}{}

// named empty struct type
type emptyStruct struct{}
empty := emptyStruct{}
```
The cool thing about empty structs is that they're the smallest possible type in Go: they take up **zero bytes of memory**.