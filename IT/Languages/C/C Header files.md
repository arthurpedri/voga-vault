### Header files
- `.c` files contain the implementation (c code).
- `.h` files are header files that contain the function prototypes.

To import code from another file, you include the `.h` file.
- `exercise.c` includes `exercise.h`.
- `main.c` includes `exercise.h`.
This allows `main.c` to call the functions implemented in `exercise.c`.
## Pragma Once and Header Guards

If the same header file gets included more than once, you can end up with some nasty errors caused by redefining things like functions or structs.
### Pragma Once
Adding this line to the top of a header file tells the compiler to include the file only once, even if it's referenced multiple times across your program.
```c
// my_header.h

#pragma once

struct Point {
    int x;
    int y;
};
```
### Header Guards
Another common way to avoid multiple inclusions is with include guards, which use preprocessor directives like this:
```c
#ifndef MY_HEADER_H
#define MY_HEADER_H

// some cool code

#endif
```
This method works by defining a unique [macro](https://gcc.gnu.org/onlinedocs/cpp/Macros.html) for the header file. If it's already been included, the guard prevents it from being processed again.

 - `#pragma once` is quicker and less error-prone than traditional include guards, and it works well with most modern compilers.
