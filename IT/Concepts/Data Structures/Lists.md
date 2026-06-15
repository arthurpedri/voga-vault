- **Append**: Appending an element to the end of a list, e.g. `cars.append("ford")` is (on average) `O(1)`. We go directly to the end and add the element.
- **Index**: Accessing an element by index, e.g. `cars[2]` is `O(1)`. We go directly to the index and return the element.
- **Delete**: Removing an element from the middle of a list, e.g. `cars.pop(2)` is `O(n)`. We have to shift all the elements after the deleted element down one index.
- **Search**: Searching for an element in a list, e.g. `cars.index("ford")` is `O(n)`. We have to iterate over the list until we find the element.

In other words, lists start to struggle in two primary areas:

1. When you need to frequently delete elements from the middle of the list
2. When you need to frequently search for specific elements in the entire list