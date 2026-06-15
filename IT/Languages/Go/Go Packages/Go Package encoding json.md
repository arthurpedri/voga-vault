[`encoding/json`](https://pkg.go.dev/encoding/json)
Uses tags to map JSON fields to struct fields.
## Decoding
- Struct fields must be exported (capitalized) to decode JSON.
```go
type Issue struct {
	Id       string `json:"id"`
	Title    string `json:"title"`
	Estimate int    `json:"estimate"`
}
```
After receiving the response, we can decode it into a slice of `Issue`s with the "address of" operator `&`:
```go
// res is a successful `http.Response`

var issues []Issue
decoder := json.NewDecoder(res.Body)
if err := decoder.Decode(&issues); err != nil {
    fmt.Println("error decoding response body")
    return
}
```
If no error occurs, we can use the slice of items in our program.
```go
for _, issue := range issues {
    fmt.Printf("Issue – id: %v, title: %v, estimate: %v\n", issue.Id, issue.Title, issue.Estimate)
    // Issue – id: 001-a, title: Unspaghettify code, estimate: 9001
}
```
## Unmarshal JSON