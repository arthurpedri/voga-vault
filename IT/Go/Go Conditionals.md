## The Initial Statement of an If Block
An `if` conditional can have an "initial" statement. The variable(s) created in the initial statement are _only_ defined within the scope of the `if`, `else if`, and `else` blocks.
```go
if INITIAL_STATEMENT; CONDITION {
}
```
- ==The opening bracket must be on the same line as the if statement==
## Switch
```go
    switch os {
    case "linux":
        creator = "Linus Torvalds"
    case "windows":
        creator = "Bill Gates"

    // all three of these cases will set creator to "A Steve"
    case "macOS":
        fallthrough
    case "Mac OS X":
        fallthrough
    case "mac":
        creator = "A Steve"

    default:
        creator = "Unknown"
    }
```