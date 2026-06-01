### Foreach
Go has a `foreach`-like syntax. It supports arrays/slices, maps and channels.
The element is a copy of the value at that index

Iterate over an **array** or a **slice**:
```go
// index and value
for i, v := range slice {}

// index only
for i := range slice {}

// value only
for _, v := range slice {}

// Iterate from 0-9 without tracking i
for _ = range 10 {} 

// Iterate values from channel until channel is closed
for valueFromChannel := range aChannel {}
```

Iterate over a **map**:
```go
// key and value
for key, value := range theMap {}

// key only
for key := range theMap {}

// value only
for _, value := range theMap {}
```
