In multi-threaded computer programming, a function is thread-safe when it can be invoked or accessed concurrently by multiple threads without causing unexpected behavior, race conditions, or data corruption.
## Levels of thread safety
Different vendors use slightly different terminology for thread-safety, but the most commonly used thread-safety terminology are:
- Not thread safe: Data structures should not be accessed simultaneously by different threads.
- Thread safe, serialization: Uses a single mutex for all resources to guarantee the thread to be free of race conditions when those resources are accessed by multiple threads simultaneously.
- Thread safe, MT-safe: Uses a mutex for every single resource to guarantee the thread to be free of race conditions when those resources are accessed by multiple threads simultaneously.