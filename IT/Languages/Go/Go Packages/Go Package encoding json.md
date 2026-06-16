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
We can decode JSON bytes (or strings) into a Go struct using [`json.Unmarshal`](https://pkg.go.dev/encoding/json#Unmarshal) or a [`json.Decoder`](https://pkg.go.dev/encoding/json#Decoder).

The `Decode` method of `json.Decoder` streams data from an [`io.Reader`](https://pkg.go.dev/io#Reader) into a Go struct, while `json.Unmarshal` works with data that's already in `[]byte` format. Using a `json.Decoder` can be more memory-efficient because it doesn't load all the data into memory at once. `json.Unmarshal` is ideal for small JSON data you already have in memory. When dealing with HTTP requests and responses, you will likely use `json.Decoder` since it works directly with an `io.Reader`.
```go
// res is an http.Response
defer res.Body.Close()

data, err := io.ReadAll(res.Body)
if err != nil {
	return nil, err
}

var issues []Issue
if err := json.Unmarshal(data, &issues); err != nil {
    return nil, err
}
```
## Marshal JSON
If there is a way to [unmarshal](https://pkg.go.dev/encoding/json#Unmarshal) JSON data, there must be a way to marshal it as well. The [`json.Marshal`](https://pkg.go.dev/encoding/json#Marshal) function converts a Go struct into a slice of bytes representing JSON data.
```go
type Board struct {
	Id       int    `json:"id"`
	Name     string `json:"name"`
	TeamId   int    `json:"team"`
	TeamName string `json:"team_name"`
}

board := Board{
	Id:       1,
	Name:     "API",
	TeamId:   9001,
	TeamName: "Backend",
}

data, err := json.Marshal(board)
if err != nil {
	log.Fatal(err)
}
fmt.Println(string(data))
// {"id":1,"name":"API","team":9001,"team_name":"Backend"}
```
![[Go IO#`map[string]interface{}`]]