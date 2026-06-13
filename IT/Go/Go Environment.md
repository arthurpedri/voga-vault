## Directory Structure
To recap how packages and modules work in your project directory structure:
- You will have many _git repositories_ on your machine (typically one per project).
- Each repository is typically a single _module_.
- Each module contains one or more _packages_
- Each package consists of one or more _Go source files_ in a single directory.
The path to a package's directory determines its _import path_ and where it can be downloaded from if you decide to host it on a remote version control system like [GitHub](https://github.com/) or [GitLab](https://gitlab.com/).
## A Note About GOPATH
The `$GOPATH` environment variable will be set by default somewhere on your machine (typically in the home directory, `~/go`). Since we will be working in the new "Go modules" setup, you _don't need to worry about that_. If you read something online about setting up your `GOPATH`, that documentation is probably out of date.
- These days you should _avoid_ storing your projects in `$GOPATH`. Again, that's the old way of doing things and can cause unexpected issues, so better to just avoid it.
# Go Mod
`go mod init {REMOTE}/{USERNAME}/module`
Creates a `go.mod` file that specifies the go version and uses the specified module
## A Note on “replace”
Be aware that using the "replace" keyword like we did in the last assignment _is not advised_, but can be useful to get up and running quickly. The _proper_ way to create and depend on modules is to publish them to a remote repository. When you do that, the "replace" keyword can be dropped from the `go.mod`:

This only works for local-only development:
```go
replace github.com/wagslane/mystrings v0.0.0 => ../mystrings
```
## Go Get
`go get {REMOTE}/{USERNAME}/module`
Requires module on `go.mod` indirectly
# Go Run
`go run main.go`
Quickly compiles and runs a Go package. The compiled binary is ==not saved== in your working directory
- Useful for local testing, scripting and debugging
# Go Build
`go build`
Compiles go code into a single, statically linked executable program
- If it isn't a `main` package, it won't build an executable, however it will still compile the package and save it to our local build cache
    - Useful for checking compile errors
# Go Install
`go install`
Compiles and installs a package or packages on your local machine.
- Installs the package's compiled binary in the `GOBIN` directory
