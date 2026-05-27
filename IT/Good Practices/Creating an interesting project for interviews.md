## How to build the project
- A project that resonates with employers
- Follow a design pattern (For example MVC)
- Clean / Professional UI (For example bootstrap template)
- Database (With CRUD)
- Authentication (Login) (For example Auth0)
- Authorization (Permissions) (For example Auth0)
- Solve a business problem
- Make Software requirements
- Separate requirements into sprints
- Example: [[Issue Tracker project]]

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
