### Prints
```go
s := fmt.Sprintf("I am %v years old", 10)
// I am 10 years old

s := fmt.Sprintf("I am %v years old", "way too many")
// I am way too many years old
```
- `fmt.Print`
- `fmt.Printf`: with formatting (`%v, %d, %.2f`)
- `fmt.Println`
- `fmt.Sprintf()`: returns formatted string
- `%v`: Prints values in the default representation
- `%s`: Strings
- `%d`: Integers
- `%f` or `%.2f`: Floats
- `%w`: Preservers the original error (Can be found even if wrapped multiple times)
## Multi-line string
You can use a backtick (`` ` ``) to create a multi-line string in Go.

[[Go Runes]]

## Strings Package
`import "strings"`
### Contains
```go
func Contains(s, substr string) bool
```
Contains reports whether substr is within s.
### Fields
```go
func Fields(s [string]) [][string](
```
Fields splits the string s around each instance of one or more consecutive white space characters, as defined by [unicode.IsSpace](https://pkg.go.dev/unicode#IsSpace), returning a slice of substrings of s or an empty slice if s contains only white space. Every element of the returned slice is non-empty. Unlike [Split](https://pkg.go.dev/strings#Split), leading and trailing runs of white space characters are discarded.
### ToLower
```go
func ToLower(s string) string
```
ToLower returns s with all Unicode letters mapped to their lower case.
### Index
```go
func Index(s, substr string) int
```
Index returns the index of the first instance of substr in s, or -1 if substr is not present in s.
### ReplaceAll
```go
func ReplaceAll(s, old, new string) string
```
ReplaceAll returns a copy of the string s with all non-overlapping instances of old replaced by new. If old is empty, it matches at the beginning of the string and after each UTF-8 sequence, yielding up to k+1 replacements for a k-rune string.

## Decoding JSON
![[Go Package encoding json#Decoding]]
## `map[string]interface{}`
Sometimes you have to deal with JSON data of unknown or varying structure in Go. In those instances `map[string]interface{}` offers a flexible way to handle it without predefined structs.

Think about it: a JSON object is a key-value pair, where the key is a string and the value can be any JSON type. `map[string]interface{}` is a map where the key is a string and the value can be any Go type.
```go
var data map[string]interface{}
jsonString := `{"name": "Alice", "age": 30, "address": {"city": "Wonderland"}}`
json.Unmarshal([]byte(jsonString), &data)
fmt.Println(data["name"])  // Output: Alice
fmt.Println(data["address"].(map[string]interface{})["city"])  // Output: Wonderland
```