The basic loop in Go is written in standard C-like syntax:
```go
for INITIAL; CONDITION; AFTER{
  // do something
}
for i := 0; i < 10; i++ {
  fmt.Println(i)
}
```
- `INITIAL` is run once at the beginning of the loop and can create  
variables within the scope of the loop.
- `CONDITION` is checked before each iteration. If the condition doesn't pass  
then the loop breaks.
- `AFTER` is run after each iteration.
## Omitting Conditions from a for Loop in Go
Loops in Go can omit sections of a for loop. For example, the `CONDITION` (middle part) can be omitted which causes the loop to run forever.
```go
for INITIAL; ; AFTER {
  // do something forever
}
```
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
### Continue
The `continue` keyword stops the current iteration of a loop and continues to the next iteration. `continue` is a powerful way to use the [guard clause](https://www.boot.dev/blog/computer-science/guard-clauses/) pattern within loops.
### Break
The `break` keyword stops the current iteration of a loop and exits the loop.