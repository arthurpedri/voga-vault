## Malloc
```c
void* malloc(size_t size);
```
- `size`: The number of bytes to allocate.
- Returns: A pointer to the allocated memory or `NULL` if the allocation fails.
## Free
The [`free`](https://en.cppreference.com/w/c/memory/free) function deallocates memory that was previously allocated by [`malloc`](https://en.cppreference.com/w/c/memory/malloc), [`calloc`](https://en.cppreference.com/w/c/memory/calloc), or [`realloc`](https://en.cppreference.com/w/c/memory/realloc).

**IMPORTANT:** `free` does not change the **value** stored in the memory, and it doesn't even change the address stored in the pointer. Instead, it simply informs the Operating System that the memory can be used again.
- Forgetting to call `free` leads to a [[Memory Leaks|memory leak]].