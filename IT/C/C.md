### Comments 
```c
// Single Line
/* Multi
   Line */
```
### Char arrays
Single quotes (`'`) make `char`, not `char *`.
```c
char *charArray = "String of characters";
```
[[C Arrays]]
### Print
```c
printf("Hello, %s. You're %d years old.\n", name, age);
```
Common format specifiers are:
- `%d` – digit (integer)
- `%c` – character
- `%f` – floating point number
- `%s` – string (`char *`)
### Constants
```c
const int x = 5;
x = 10; // error
```
### Functions
```c
float add(int x, int y) {
    return (float)(x + y);
}
```
[[C Header files]]
### Increment and decrement operators
These increment (`++`) and decrement (`--`) operators can be used in two forms: postfix and prefix.

**Postfix (`x++` or `x--`):** The value of `x` is used in the expression first, and then `x` is incremented or decremented. For example:

```c
int a = 5;
int b = a++; // b is assigned 5, then a becomes 6
```

**Prefix (`++x` or `--x`):** `x` is incremented or decremented first, and then the new value of `x` is used in the expression. For example:

```c
int a = 5;
int b = ++a; // a becomes 6, then b is assigned 6
```
### Conditionals
```c
if (x > 3) {
    printf("x is greater than 3\n");
} else if (x == 3) {
    printf("x is 3\n");
} else {
    printf("x is less than 3\n");
}
```
- C uses short-circuit evaluation with logical operators.
#### Ternary Operator
```c
a > b ? a : b
```
### Sizeof
You can use `sizeof` like a function (although, technically it's a [unary operator](https://en.wikipedia.org/wiki/Unary_operation))
### For Loop
```c
for (initialization; condition; final-expression) {
    // Loop Body
}
```

### Do while Loop
Unlike the `while` loop, the `do while` loop checks the condition after executing the loop body, so the loop body is **always** executed at least once.
```c
do {
    // Loop Body
} while (condition);
```
- The most common scenario you will see a do-while loop used is in [C macros](https://gcc.gnu.org/onlinedocs/cpp/Macros.html) – they let you define a block of code and execute it exactly once in a way that is safe across different compilers, and ensures that the variables created/referenced within the macro do not leak to the surrounding environment.

[[C Structs]]

[[C Pointers]]

[[C Enums]]

[[C Unions]]

[[C Memory Allocation]]