The `net/url` package is part of Go's standard library. You can instantiate a [URL struct](https://pkg.go.dev/net/url#Parse) using `url.Parse`:
```go
parsedURL, err := url.Parse("https://homestarrunner.com/toons")
if err != nil {
	fmt.Println("error parsing url:", err)
	return
}
```
And then you can [extract just the hostname](https://pkg.go.dev/net/url#URL.Hostname):
```go
parsedURL.Hostname()
// homestarrunner.com
```