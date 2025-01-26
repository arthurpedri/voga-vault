## Template literals
- Can be used for multi-line strings and string interpolation.

### String interpolation
```js
`Some string ${}`
```

## Truthy and Falsy
- Falsy: 0, empty strings, null, undefined, NaN

## Short-circuit evaluation
```js
let value = truthy_expression || expression_that_will_never_run
```
-  Value is equal to the return of `truthy_expression`.

## Ternary operator
```js
condition ? if_true_expression : if_false_expression
```

## Switch
```js
switch (condition) {

  case 'something':

    break; // only if you want to stop evaluating

  default:

    break;

}
```
  
[[JS Functions]]
## Array literal: []
- `const` can be used to change elements in the array but not to reassign the array
- array is a class and can be instanced with new Array()
### for of
```js
for (const item of array) {  // also works with strings and [key, value]
    item;
}
```
- break and continue work normally

## Maps vs Objects
- Don't confuse maps with objects, even though setting object properties works for maps, it will use the feature of the generic object, and won't be able to use map methods and have map qualities.

  

## Destructuring
- `{ key }` : object gets the element with key from object
- `[h, ...t]` : array deconstructing

## Object literal: {}

  delete object.key // deletes the key value pair of key

  methods are key: value pairs with anonymous functions

  es6 syntax allows defining methods by omitting the colon and function keyword:

    const object = {

      foo () {

        bar();

      }

    };

  objects are passed by reference

  'this' refers to the calling object

    'this' doesn't quite work on arrow functions

  base js doesn't have privacy, so the convention is to use _ before the name of a property

    new syntax has # to define privacy

  getters and setters:

    const object = {

      get foo(){

        expressions...

        return whatever

      },

      set bar(value){

        expressions...

        this.value = value

      }

    }

    console.log(object.foo) // both look like accessing a property

    object.bar = 30

  



  

for..in operates over the keys of an object

  

inheritance

  class extends superclass

  constructor call super() for the super constructor

  'this.' won't work before super is called on the constructor

  

static methods can be called from class, but not from instances

  static method()

  

[[JS Modules]]