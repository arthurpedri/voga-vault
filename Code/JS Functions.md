## Functions
### Default parameters
```js
function x(var = 'default value')
```

###  Function expression
```js
const foo = function(arg) { expression; };
foo(arg);
```

### Arrow functions
```js
const foo = (arg) => { expression; };
arg => arg.length // implicit return
() => {};
```
- Fat arrow separates parameters from body.
- Does not establish scope but const and let are limited to expressions they are declared in.
- They do not have their own bindings to `this` or `super`, and should not be used as methods.
- They cannot be used as constructors.
- They cannot use `yield`, within its body.
- They cannot use the special `arguments` keyword.

  factory functions work by returning an object created using the parameters

    property value shorthand (destructuring):

      const foo = (name, age) => {

        return {

          name,

          age

        }

      };

  destructured assignment:

    const { key } = object

    key is now the value of that key in the object

  

functions are first class objects

  they can have properties and methods

  higher-order functions are those that accept functions as parameters or returns a function

  functions that are passed as parameters are callback functions