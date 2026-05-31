The stack is where local variables are stored. When a function is called, a new **stack frame** is created in memory to store the function's parameters and local variables. When the function returns, its entire stack frame is deallocated.
The stack is aptly named: it is a **[[Stacks]]** (the "Last In, First Out" data structure) of memory frames. Each time a function is called, a new frame is pushed onto the stack. When the function returns, its frame is popped off the stack.
# Why a Stack?

Allocating memory on the stack is preferred when possible because the stack is faster and simpler than the heap:
- **Efficient Pointer Management:** Stack "allocation" is just a quick increment or decrement of the stack pointer, which is extremely fast. Heap allocations require more complex bookkeeping.
- **Cache-Friendly Memory Access:** Stack memory is stored in a contiguous block, enhancing cache performance due to spatial locality. Related values live next to each other in memory, the CPU can load and access them more quickly.
- **Automatic Memory Management:** Stack memory is managed automatically as functions are called and as they return.
- **Inherent Thread Safety:** Each thread has its own stack. Heap allocations require synchronization mechanisms when used concurrently, potentially introducing overhead.
# Stack Overflow

So the stack is great and all, but one of the downsides is that it has a limited size. If you keep pushing frames onto the stack without popping them off, you'll eventually run out of memory and get a [**stack overflow**](https://en.wikipedia.org/wiki/Stack_overflow). 

That's one of the reasons recursion without [tail-call optimization](https://en.wikipedia.org/wiki/Tail_call) can be dangerous. Each recursive call pushes a new frame onto the stack, and if you have too many recursive calls, you'll run out of stack space.