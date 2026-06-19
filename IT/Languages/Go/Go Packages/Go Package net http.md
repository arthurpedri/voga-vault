[`net/http`](https://pkg.go.dev/net/http)
# Making a Request
```go
import (
	"fmt"
	"io"
	"net/http"
)

func getProjects() ([]byte, error) {
	res, err := http.Get("https://api.jello.com/projects")
	if err != nil {
		return nil, fmt.Errorf("error making request: %w", err)
	}
	defer res.Body.Close()

	data, err := io.ReadAll(res.Body)
	if err != nil {
		return nil, fmt.Errorf("error reading response: %w", err)
	}
	return data, nil
}
```
- `http.Get` uses the `http.DefaultClient` to make a request to the given `url`
- `res` is the HTTP response that comes back from the server
- `defer res.Body.Close()` ensures that the response body is properly closed after reading. Not doing so can cause memory issues.
- `io.ReadAll` reads the response body into a slice of bytes `[]byte` called `data`
# Headers
We can access headers through the `Header` type, which is essentially a map of string slices (`map[string][]string`). This allows us to perform various actions on our request and response headers such as retrieving, setting, and removing them.

```go
// creating a new request
req, err := http.NewRequest("GET", "https://api.example.com/users", nil)
if err != nil {
	fmt.Println("error creating request: ", err)
	return
}

// setting a header on the new request
req.Header.Set("x-api-key", "123456789")

// making the request
client := http.Client{}
res, err := client.Do(req)
if err != nil {
	fmt.Println("error making request: ", err)
	return
}
defer res.Body.Close()

// reading a header from the response
header := res.Header.Get("last-modified")
fmt.Println("last modified: ", header)

// deleting a header from the response
res.Header.Del("last-modified")
```