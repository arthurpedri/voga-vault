```go
var p *int
myString := "hello"
myStringPtr := &myString
```
- Empty pointers are `nil` pointers
- Unlike `C`, go has no pointer arithmetic
## Fields of Pointers
```go
msgTotal := *analytics.MessagesTotal // This creates an error
// Using selector expressions
msgTotal := analytics.MessagesTotal // Shorthand for (*analytics).MessagesTotal
```
This approach is shorthand for `(*analytics).MessagesTotal` and is the recommended, simplest way to access struct fields in Go.
## Nil Pointers
`nil` pointers will panic (runtime error) if dereferenced, check for `nil` before dereferencing them
## Pointer Receiver
**Methods with pointer receivers don't require that a pointer is used to call the method**. The pointer will automatically be derived from the value.
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
