Pros:

- **Very fast**: At least it is in the average case
- **In-Place**: Saves on memory, doesn't need to do a lot of copying and allocating

Cons:

- **Typically unstable**: changes the relative order of elements with equal keys
- **Recursive**: can incur a performance penalty in some implementations
- **Pivot sensitivity**: if the pivot is poorly chosen, it can lead to poor performance

## Pseudocode
- Select a "pivot" element - We'll arbitrarily choose the last element in the list
- Move through all the elements in the list and swap them around until all the numbers less than the pivot are on the left, and the numbers greater than the pivot are on the right. **The pivot stays where it is, they are moved around using other counters (for example: Current and middle)**
- Move the pivot between the two sections where it belongs
- Recursively repeat for both sections

# Fixing Quick Sort

While the version of quicksort that we implemented is almost always able to perform at speeds of `O(n*log(n))`, its Big O is still technically `O(n^2)` due to the worst-case scenario. We can fix this by altering the algorithm slightly.

Two of the approaches are:

- Shuffle input randomly before sorting. This can trivially be done in `O(n)` time.
- Actively find the median of a sample of data from the partition, this can be done in `O(1)` time.

## Random Approach

The random approach is easier to code, which is nice if you're the one writing the code.

The function simply shuffles the list into random order before sorting it, which is an `O(n)` operation. The likelihood of shuffling a large list into sorted order is so low that it's not worth considering.

## Median Approach

Another popular solution is to use the "median of three" approach. Three elements (for example: the first, middle, and last elements) of each partition are chosen and the median is found between them. That item is then used as the pivot.

This approach has less overhead, and also doesn't require randomness to be injected into the function, meaning it can remain deterministic and _pure_.

Boots

Spellbook

Lessons

![Boots](https://www.boot.dev/_nuxt/new_boots_profile.DriFHGho.webp)

**Need help?** I, Boots the Incredibly Fluffy, can assist... _for a price_.

What does shuffling quick sort's input do?

1

Slows down the algorithm

2

Practically ensures a runtime of O(n*log(n))

3

Makes the algorithm unsafe for production use

4

Makes it really slow