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
# Go Run
`go run main.go`
Quickly compiles and runs a Go package. The compiled binary is ==not saved== in your working directory
- Useful for local testing, scripting and debugging
# Go Build
`go build`
Compiles go code into a single, statically linked executable program
# Go Install
`go install`
Compiles and installs a package or packages on your local machine.
- Installs the package's compiled binary in the `GOBIN` directory
