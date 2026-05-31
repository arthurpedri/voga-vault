A garbage collector is a program (or part of a program) that automatically frees memory that is no longer in use. 
- Automatic memory management can be a huge productivity boost for developers (less code, and sometimes fewer memory-related bugs) but it typically comes with a performance cost.

# Refcounting
One of the simplest ways to implement a garbage collector is to use a [reference counting](https://en.wikipedia.org/wiki/Garbage_collection_\(computer_science\)#Reference_counting) algorithm. It goes something like this:
- All objects keep track of a `reference_count` integer.
- When that object is referenced, its reference count is incremented.
- When an object is garbage collected, the reference count of any object it references is decremented.
- When any object's reference count reaches zero, the object is garbage collected.
### Cyclic Reference
We create a `first` array, and shove the `second` array inside of it. Everything here works as expected. The trouble arises when we introduce a cycle: for example, `first` contains `second`, but `second` also contains `first`... In other words, we have a **cycle**, and our simple reference counting garbage collector can't handle it.

# Mark and Sweep
To solve our cyclic reference issue we're going to implement a [Mark and Sweep](https://en.wikipedia.org/wiki/Tracing_garbage_collection#Na%C3%AFve_mark-and-sweep) garbage collector.
## Pros of MaS
- Can detect cycles, and thus prevent memory leaks in certain cases
- Less on-demand bookkeeping (Remember: all work done by the GC is "wasted" – it doesn't make your ~~GPT-4 wrapper~~ custom AI product run any faster)
- Reduces potential performance degradation in highly multithreaded programs (refcounting requires atomic updates for thread safety)
## Cons of MaS
- More complex to implement 
- Can cause "stop-the-world" pauses when lots of objects exist and must be freed (resulting in poor performance)
- Higher memory overhead
- Less predictable performance
## The Algorithm

Mark and Sweep garbage collection was first described by John McCarthy in 1960, primarily for managing memory in `((lisp))`. It's a two-phase algorithm:

1. **Mark Phase:** Traverses the object graph, marking all reachable objects.
2. **Sweep Phase:** Scan memory, collecting all unmarked objects, which are considered garbage.

Note! We don't keep track of how many times a particular object is referenced, like we did with reference counting! Instead, we keep track of which objects are referenced in each `stack frame` and then traverse our container objects looking for any other referenced objects. That's what "traverse the object graph" means – a fancy way of saying "look for objects".
