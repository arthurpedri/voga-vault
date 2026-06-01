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