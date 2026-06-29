[`net/http`](https://pkg.go.dev/net/http)
# Making a Simple Request
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
# GET Requests

There are two basic ways to make a Get request in Go.
1. The simple but less powerful way: [`http.Get`](https://pkg.go.dev/net/http#Get)
2. The verbose but more powerful way: [`http.Client`](https://pkg.go.dev/net/http#Client), [http.NewRequest](https://pkg.go.dev/net/http#NewRequest), and [http.Client.Do](https://pkg.go.dev/net/http#Client.Do)

If all you need to do is make a simple `GET` request to a URL, `http.Get` will work:
```go
resp, err := http.Get("https://jsonplaceholder.typicode.com/users")
```

If you need to customize things like headers, cookies, or timeouts, you'll want to create a custom [`http.Client`](https://pkg.go.dev/net/http#Client), and [`http.NewRequest`](https://pkg.go.dev/net/http#NewRequest), then use the client's [`Do`](https://pkg.go.dev/net/http#Client.Do) method to execute it.

```go
client := &http.Client{
	Timeout: time.Second * 10,
}

req, err := http.NewRequest("GET", "https://jsonplaceholder.typicode.com/users", nil)
if err != nil {
	log.Fatal(err)
}

resp, err := client.Do(req)
```
# Post Requests
Like `http.Get`, the standard library's [`http.Post`](https://pkg.go.dev/net/http#Post) function can be used to send simple `POST` requests.
- It can also be further elaborated using custom `http.Client` and `http.NewRequest`
```go
    // create a new request
	req, err := http.NewRequest("POST", url, bytes.NewBuffer(jsonData))
	if err != nil {
		return Comment{}, err
	}

    // set request headers
	req.Header.Set("Content-Type", "application/json")
    req.Header.Set("X-API-Key", apiKey)

    // create a new client and make the request
	client := &http.Client{}
	res, err := client.Do(req)
	if err != nil {
		return Comment{}, err
	}
	defer res.Body.Close()
```

# Put Requests
Unlike `GET` and `POST`, there is no `http.Put` function. You will have to create a raw `http.Request` that an `http.Client` can [`Do`](https://pkg.go.dev/net/http#Client.Do).
# Response
- `http.Response.StatusCode` is a property that contains the status code of the response.