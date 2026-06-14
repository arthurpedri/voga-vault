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