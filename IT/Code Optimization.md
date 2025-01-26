## Doing less
from [going fast is about doing less](https://www.youtube.com/watch?v=5rb0vvJ7NCY)
- Start with brute force recursion.
- Use a cache to reduce rework. [[Memoization]]
- More caching by removing values used on keys and putting them on values so we can compare similar states and remove ones that may be fundamentally less useful. In the example of the video, the same state while having less time elapsed is always better. 
- Reduce size of keys to reduce the hashing overhead and improves the hash function by copying the keys more efficiently.
- Domain knowledge can be use to set maximum bounds on branches and remove the branches that have a maximum that is less than what has already been achieved by other branches.
- More domain knowledge can be used to remove branches that contain results that try to maximize some value that is not relevant to the result. In the video, there is a maximum number of other robots that will not increase the final result even if they are increased. In this case it's possible to remove branches that try to go over this number, as they are unnecessary and possibly ineffectual.
- At this point, the algorithm and domain knowledge are so optimized that the cache hit rate is very low, making the hashmap the bottleneck in the program, and removing it will increase the speed.
## More assumptions
More assumptions about the data will produce faster and more efficient code.

## [[Hash Tables|Hash Functions]]
- Computers like reading consistently and dislike looping, making hash functions that are based on predetermined pieces of the key instead of having to loop through the key much more efficient.
- The data is never random, making assumptions will help improve the function and your code in general.

## Single instruction, multiple data (SIMD)
- Very useful for data that can be vectorized, such as multimedia applications.
- Processors have SIMD registers (or vector registers) that will optimize this kind of instruction.
- Mostly done on GPUs nowadays.
- Removing conditionals and jumping will make the code much faster, such as using math instead of if statements.