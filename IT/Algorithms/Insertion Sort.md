# Why Use Insertion Sort?

- **Fast**: for very small data sets (even faster than merge sort and quick sort, which we'll cover later)
- **Adaptive**: Faster for partially sorted data sets
- **Stable**: Does not change the relative order of elements with equal keys
- **In-Place**: Only requires a constant amount of memory
- **Inline**: Can sort a list as it receives it

## Why Is Insertion Sort Fast for Small Lists?

Many production sorting implementations use insertion sort for very small inputs under a certain threshold (very small, like `10`-ish), and switch to something like quicksort for larger inputs. They use insertion sort because:

- There is no recursion overhead
- It has a tiny memory footprint
- It's a stable sort as described above
## Algorithm
1. For each index in the input list, starting with the second element:
    1. Set a `j` variable to the current index
    2. While `j` is greater than `0` and the element at index `j-1` is greater than the element at index `j`:
        1. Swap the elements at indices `j` and `j-1`
        2. Decrement `j` by `1`
2. Return the list
