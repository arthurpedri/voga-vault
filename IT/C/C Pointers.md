## Getting a Variable's Address
In C, you can print the address of a variable by using the address-of-operator: `&`. Here's an example:
```c
#include <stdio.h>

int main() {
  int age = 37;
  printf("The address of age is: %p\n", &age);
  return 0;
}

// The address of age is: 0xfff8
```
## Syntax
A pointer is declared with an asterisk (`*`) after the type. For example, `int *`.
```c
int age = 37;
int *pointer_to_age = &age;
```
## Dereferencing Pointers

Oftentimes we have a pointer, but we want to get access to the data that it points to. Not the address itself, but the value stored at _that_ address.
We can use an asterisk (`*`) to do it. The `*` operator dereferences a pointer.
```c
int meaning_of_life = 42;
int *pointer_to_mol = &meaning_of_life;
int value_at_pointer = *pointer_to_mol;
// value_at_pointer = 42
```
_The asterisk symbol is used for two different things:_
1. Declaring a pointer type: `int *pointer_to_thing;`
2. Dereferencing a pointer value: `int value = *pointer_to_thing;` (retrieving the value) or `*pointer_to_thing = 20;` (modifying the value)
## Pointers to Structs
As you know, when you have a struct, you can access the fields with the dot (`.`) operator:
```c
coordinate_t point = {10, 20, 30};
printf("X: %d\n", point.x); // X: 10
```
However, when you're working with a _pointer to a struct_, you need to use the arrow (`->`) operator:
```c
coordinate_t point = {10, 20, 30};
coordinate_t *ptrToPoint = &point;
printf("X: %d\n", ptrToPoint->x); // X: 10
```
It effectively dereferences the pointer and accesses the field in one step. To be fair, you can also use the dereference and dot operator (`*` and `.`) to achieve the same result (it's just more verbose and less common):
```c
coordinate_t point = {10, 20, 30};
coordinate_t *ptrToPoint = &point;
printf("X: %d\n", (*ptrToPoint).x); // X: 10
```
## Order of Operations
The `.` operator has a higher precedence than the `*` operator, so parentheses are _necessary_ when using `*` to dereference a pointer before accessing a member... which is another reason why the arrow operator is so much more common.

## Void Pointers
A `void *` "void pointer" tells the compiler that this pointer could point to **anything**. This is why void pointers are also known as a "generic pointer". Since void pointers do not have a specific data type, they cannot be directly dereferenced or used in pointer arithmetic without casting them to another pointer type first.
```c
int number = 42;
void *generic_ptr = &number;

// This doesn't work
printf("Value of number: %d\n", *generic_ptr);

// This works: Cast to appropriate type before dereferencing
printf("Value of number: %d\n", *(int*)generic_ptr);
```