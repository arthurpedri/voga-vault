#### Inline errors
```go 
import "errors"
return errors.New("Error Name")
```
## Error [[Go Interfaces|Interface]]
Go programs express errors with `error` values. An Error is any type that implements the simple built-in [error interface](https://blog.golang.org/error-handling-and-go):
```go
type error interface {
    Error() string
}
```
When something can go wrong in a function, that function should return an `error` as its last return value. Any code that calls a function that can return an `error` should handle errors by testing whether the error is `nil`.
### Return Convention
- When you return a non-nil error in Go, it's conventional to return the "zero" values of all other return values.
- Error strings should not start with a capital letter because they’ll often be prefixed before printing