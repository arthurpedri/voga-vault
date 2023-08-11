## Is an object that contains an address
- Implementation varies, but it is meant to store a memory address.
## Operators
Can vary in different programming languages, but the concepts are the same.
- **int \*pX = &x**
    - *Integer pointer pX is set to the address of x.*
    - Asterisk modifies the type to a pointer when near it.
    - Ampersand gives the address of the variable.
- **int y = \*pX**
    - *Integer y is set to the thing pointed to by pX.*
    - Asterisk without a type will [[Reference#Dereferencing|dereference]] the variable.
## Null pointers
- A null pointer or a null [[Reference|reference]] is a value saved for indicating that the pointer or reference does not refer to a valid object.
### Null pointer error
- An attempt to access the data stored at the (invalid) memory location of ==**(dereferencing) the null pointer**== can cause a run-time error or immediate program crash.
- One of the most common types of software weaknesses, has been referred to as a "billion dollar mistake".