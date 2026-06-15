A function together with the variables from its surrounding scope that it remembers and can continue using even after that scope has finished executing.
```
Function + Captured Environment
```
- The inner function ==**closes over**== the environment where it is created. This remembered environment is the **closure**.
## What actually gets stored?
It stores something like:
```
Function:    parameter: name
Captured variables:    greeting = "Hello"
```
## Private State
Closures are often used to create private variables.
```js
function createCounter() {
    let count = 0;

    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();

console.log(counter());
console.log(counter());
console.log(counter());
```
The variable survives because the closure still references it.
- Nobody can directly do:
```js
count = 999;
```
because `count` isn't visible outside the closure
## Function factories
Closures let you pre-configure behavior.
This pattern appears everywhere:
- Logging functions
- Validation functions
- Database query builders
- API clients
## Event handlers
The callback is a closure.
Suppose:
```js
let userName = "Arthur";

button.addEventListener("click", () => {
    console.log(userName);
});
```
The callback remembers `userName`.
When the click happens 10 minutes later, the variable is still available.
Without closures, event-driven programming would be much more awkward.
## Keeping state between calls
```js
function createPeakTracker() {
    let highest = 0;

    return function(value) {
        if (value > highest)
            highest = value;

        return highest;
    };
}
const tracker = createPeakTracker();

tracker(10); // 10
tracker(7);  // 10
tracker(20); // 20
```
The closure stores the history.
This is common in:
- Audio processing
- Statistics
- Signal analysis
- Games
## Dependency injection
```js
function createApiClient(baseUrl) {
    return {
        getSong(id) {
            return fetch(baseUrl + "/songs/" + id);
        }
    };
}
const api =
    createApiClient("https://api.example.com");
```
Now every method remembers `baseUrl`.
This pattern is used heavily in:
- Backend services
- DevOps tooling
- SDKs
- Database libraries
### Other Examples
- LINQ and lambdas in C#
- Delayed execution
## Useful Intuition
>If a class would only have one or two fields and one method, a closure is often a lightweight alternative.
```cs
class Counter
{
    private int count;

    public int Next()
    {
        count++;
        return count;
    }
}
```
```js
function createCounter() {
    let count = 0;

    return function() {
        return ++count;
    };
}
```