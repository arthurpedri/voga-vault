- ### Generics Reduce Repetitive Code
- ### Generics Are Used More Often in Libraries and Packages
## Type Parameters
The type parameters of a function appear between brackets, before the function's arguments.
```go
func Index[T comparable](s []T, x T) int
```
Put simply, generics allow us to use variables to refer to specific types. This is an amazing feature because it allows us to write abstract functions that drastically reduce code duplication.
```go
func splitAnySlice[T any](s []T) ([]T, []T) {
    mid := len(s)/2
    return s[:mid], s[mid:]
}
```
In the example above, `T` is the name of the type parameter for the `splitAnySlice` function, and we've said that it must match the `any` constraint, which means it can be anything. This makes sense because the body of the function _doesn't care_ about the types of things stored in the slice.
```go
firstInts, secondInts := splitAnySlice([]int{0, 1, 2, 3})
fmt.Println(firstInts, secondInts)
```
# Constraints
Constraints are just interfaces that allow us to write generics that only operate within the constraints of a given interface type. 
- The `any` constraint is the same as the empty interface because it means the type in question can be _anything_.
## Creating a Custom Constraint
Let's take a look at the example of a `concat` function. It takes a slice of values and concatenates the values into a string. This should work with _any type that can represent itself as a string_, even if it's not a string under the hood. For example, a `user` struct can have a `.String()` that returns a string with the user's name and age.
```go
type stringer interface {
    String() string
}

func concat[T stringer](vals []T) string {
    result := ""
    for _, val := range vals {
        // this is where the .String() method
        // is used. That's why we need a more specific
        // constraint instead of the any constraint
        result += val.String()
    }
    return result
}
```
## Interface Type Lists
When generics were released, a new way of writing interfaces was also released at the same time!
- Traditional interfaces in Go are **method-based**: a type satisfies an interface if it has the required methods.
- With generics, we also got **type-set (type-list) interfaces**. Instead of listing methods, they list the concrete (or underlying) types that are allowed. These are mostly used as **constraints on type parameters**.
For example, to use `<` and `>` on a type parameter `T`, the compiler must know `T` is ordered. A type-list interface spells out exactly which types count as ordered:
```go
// Ordered matches any type that supports <, <=, >, and >=.
type Ordered interface {
    ~int | ~int8 | ~int16 | ~int32 | ~int64 |
        ~uint | ~uint8 | ~uint16 | ~uint32 | ~uint64 | ~uintptr |
        ~float32 | ~float64 |
        ~string
}

// Because T is constrained by Ordered, the compiler knows
// that < is valid for any T used with this function.
func Min[T Ordered](a, b T) T {
    if a < b {
        return a
    }
    return b
}
```
## Parametric Constraints
Your interface definitions, which can later be used as constraints, can accept [type parameters](https://go.dev/tour/generics/1) as well.
```go
// The store interface represents a store that sells products.
// It takes a type parameter P that represents the type of products the store sells.
type store[P product] interface {
	Sell(P)
}
```