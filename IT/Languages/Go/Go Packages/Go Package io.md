[`io`](https://pkg.go.dev/io)
## ReadAll
```go
func ReadAll(r Reader) ([]byte, error)
```
ReadAll reads from r until an error or EOF and returns the data it read. A successful call returns err == nil, not err == EOF. Because ReadAll is defined to read from src until EOF, it does not treat an EOF from Read as an error to be reported.