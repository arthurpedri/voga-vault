# Goroutines
```go
go doSomething()
```
- The `go` keyword is used to spawn a new *goroutine* and then continues executing the code concurrently
- If a program exits before its goroutines have completed, those goroutines will be killed silently.

# Channels
Channels are a typed, thread-safe queue, they allow different goroutines to communicate with each other
- Channels are reference types (Passed by reference by default)
#### Create a channel
Like maps and slices, channels must be created _before_ use. They also use the same `make` keyword:
```go
ch := make(chan int)
bufferedCh := make(chan int, 100)
```
- A buffer allows the channel to hold a fixed number of values before blocking
#### Send data to a channel
```go
ch <- 69
```
The `<-` operator is called the _channel operator_. Data flows in the direction of the arrow. This operation will ==_block_ until another goroutine is ready to receive the value==
#### Receive data from a channel
```go
v := <-ch
```
This reads and removes a value from the channel and saves it into the variable `v`. This operation will ==_block_ until there is a value in the channel to be read==
#### Receive anything on channel
```go
<-ch
downloadDoneCh <- struct{}{}
```
This will block until it pops a single item off the channel, then continue, discarding the item
- An empty struct can be passed as a signal to the channel, when only the signal is important, not the data
#### Closing channels
```go
close(ch)
```
- Channels can be checked using the same `ok` syntax:
```go
 v, ok := <-ch // false if the channel is empty and closed
```
- ==Sending on a closed channel will cause a panic==
- Closing isn't necessary, they will still be garbage collected if the're unused
- Close channels to indicate explicitly to a receiver that nothing else is going to come across
#### Buffered Channels
```go
ch := make(chan int, 100)
```
A buffer allows the channel to hold a fixed number of values before sending blocks. This means sending on a buffered channel only blocks when the buffer is full, and receiving blocks only when the buffer is empty.
#### Range Channel
Similar to slices and maps, channels can be ranged over.
```go
for item := range ch {
    // item is the next value received from the channel
}
```
This example will receive values over the channel (blocking at each iteration if nothing new is there) and will exit only when the channel is closed.
### Read-Only Channels
A channel can be marked as read-only by casting it from a `chan` to a `<-chan` type. For example:
```go
func main() {
    ch := make(chan int)
    readCh(ch)
}

func readCh(ch <-chan int) {
    // ch can only be read from
    // in this function
}
```
### Write-Only Channels
The same goes for write-only channels, but the arrow's position moves.
```go
func writeCh(ch chan<- int) {
    // ch can only be written to
    // in this function
}
```
### Ignoring Channels
Sometimes you want to ignore a channel's value. You can do this by not binding it to a variable:
```go
select {
case <-ch: // or case _ = <-ch:
    // event received; value ignored
default:
    // so do something else
}
```
## Select
Sometimes we have a single goroutine listening to multiple channels and want to process data in the order it comes through each channel.

A `select` statement is used to listen to multiple channels at the same time. It is similar to a `switch` statement but for channels.
```go
select {
case i, ok := <-chInts:
	if ok {
		fmt.Println(i)
	}
case s, ok := <-chStrings:
	if ok {
		fmt.Println(s)
	}
}
```
The first channel with a value ready to be received will fire and its body will execute. If multiple channels are ready at the same time then one is chosen randomly. In the example above, the `ok` variable is a boolean. It is `true` while the channel is open, and `false` when the channel is closed by the sender.
### Select Default Case
The `default` case in a `select` statement executes _immediately_ if no other channel has a value ready. A `default` case stops the `select` statement from blocking.
```go
select {
case v := <-ch:
    // use v
default:
    // receiving from ch would block
    // so do something else
}
```

## Tickers
- [time.Tick()](https://golang.org/pkg/time/#Tick) is a standard library function that returns a channel that sends a value on a given interval.
- [time.After()](https://golang.org/pkg/time/#After) sends a value once after the duration has passed.
- [time.Sleep()](https://golang.org/pkg/time/#Sleep) blocks the current goroutine for the specified duration of time.
The functions take a [`time.Duration`](https://pkg.go.dev/time#Duration) as an argument. For example:
```go
time.Tick(500 * time.Millisecond)
```
If you don't add `time.Millisecond` (or another unit), it will default to nanoseconds. 

## Channel Extras
### A Declared but Uninitialized Channel Is Nil Just Like a Slice
```go
var s []int       // s is nil
var c chan string // c is nil

var s = make([]int, 5) // s is initialized and not nil
var c = make(chan int) // c is initialized and not nil
```
### A Send to a Nil Channel Blocks Forever
```go
var c chan string        // c is nil
c <- "let's get started" // blocks
```
### A Receive from a Nil Channel Blocks Forever
```go
var c chan string // c is nil
fmt.Println(<-c)  // blocks
```
### A Send to a Closed Channel Panics
```go
var c = make(chan int, 100)
close(c)
c <- 1 // panic: send on closed channel
```
### A Receive from a Closed Channel Returns the Zero Value
```go
var c = make(chan int, 100)
close(c)
fmt.Println(<-c) // 0
```
Any buffered values are received first. Once the buffer is empty, receives return the zero value.
# Mutexes
[[Mutual Exclusion (Mutex)|Mutexes]] allow us to _lock_ access to data. This ensures that we can control which goroutines can access certain data at which time.
- The zero value for a Mutex is an unlocked mutex.
Go's standard library provides a built-in implementation of a mutex with the [sync.Mutex](https://pkg.go.dev/sync#Mutex) type and its two methods:
- [.Lock()](https://golang.org/pkg/sync/#Mutex.Lock)
- [.Unlock()](https://golang.org/pkg/sync/#Mutex.Unlock)
We can protect a block of code by surrounding it with a call to `Lock` and `Unlock` as shown on the `protected()` function below.
```go
mu := &sync.Mutex{}

func protected(mu *sync.Mutex){
    mu.Lock()
    defer mu.Unlock()
    // the rest of the function is protected
    // any other calls to `mu.Lock()` will block
}
```
- It's good practice to structure the protected code within a function so that `defer` can be used to ensure that we never forget to unlock the mutex.
## RW Mutex
The standard library also exposes a [sync.RWMutex](https://golang.org/pkg/sync/#RWMutex)
The `sync.RWMutex` also has these methods for concurrent reads:
- [RLock()](https://pkg.go.dev/sync#RWMutex.RLock)
- [RUnlock()](https://pkg.go.dev/sync#RWMutex.RUnlock)
The `sync.RWMutex` improves performance in read-intensive processes. Multiple goroutines can safely read from the map simultaneously, as many `RLock()` calls can occur at the same time. However, only one goroutine can hold a `Lock()`, and during this time, all `RLock()` operations are blocked.