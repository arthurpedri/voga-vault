## Packages
- `package main` has an entrypoint at the `main()` function
- A `main` package is compiled into an executable program
- A package with any other name is a "library package" and they simply export functionality to be used by other packages
### Naming
- By *convention* a package's name is the same as the last element of its import path
```go
// for math/rand
package rand
```
### One package per directory
- A directory of Go code can have **at most** one package. All `.go` files in a directory must belong to the same package, this is true for main and library packages
- If they have more than one package the compiler will throw an error

### Clean Packages
Rules of thumb for clean, small and reusable packages.
#### Hide internal logic
- Basically [[Encapsulation]] from OOP
- Only expose the functions that need to be exported, not the internal logic
#### Don't change APIs
- Not changing exported function's signatures
- Unexported functions can and should change often, for various reasons
#### Don't export functions from the main package
- A `main` package isn't a library, there's no need to export functions from it
#### Packages shouldn't know about dependents
- A package should never have specific knowledge about a particular application that uses it
## Modules
A module is a collection of Go packages that are released together
### One module per repo (usually)
A file named `go.mod` at the root of a project declares the module. It contains:
- The module path
- The version of the Go language your project requires
- Optionally, any external package dependencies your project has
```
module github.com/bootdotdev/exampleproject

go 1.23.0

require github.com/google/examplepackage v1.3.0
```
- Each module's path not only serves as an import path prefix for the packages within but _also indicates where the go command should look to download it_
### Standard library modules
- Modules in the standard library do not have prefixes

### Exporting
- Only **capitalized** names are exported
- Uncapitalized names are private