## Concurrency
```go
go doSomething()
```
- The `go` keyword is used to spawn a new *goroutine* and then continues executing the code concurrently

### Channels
Channels are a typed, thread-safe queue, they allow different goroutines to communicate with each other
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
```
This will block until it pops a single item off the channel, then continue, discarding the item
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
