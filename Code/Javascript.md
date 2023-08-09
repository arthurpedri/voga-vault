Template literals: `` -> can be used for multi-line strings and string interpolation

String interpolation: `Some string ${}`

  

undefined -> not assigned

  

truthy and falsy

  falsy: 0, empty strings, null, undefined, NaN

  

short-circuit evaluation:

  let value = truthy_expression || expression_that_will_never_run

  value is equal to the return of truthy_expression

  

ternary operator:

  condition ? if_true_expression : if_false_expression

  

switch (condition) {

  case 'something':

    break; // only if you want to stop evaluating

  default:

    break;

}

  

default parameters: (var = 'default value')

  

function expression:

  const foo = function(arg) { expression; };

  foo(arg);

  

arrow functions:

  const foo = (arg) => { expression; };

  arg => arg.length // implicit return

  () => {};

  do not establish scope but const and let are limited to expressions they are declared in

  

Array literal: []

  const can be used to change elements in the array but not to reassign the array

  array is a class and can be instanced with new Array()

  

for of:

  for (const item of array) {  // also works with strings and [key, value]

    item;

  }

  

break; and continue; work normally

  

don't confuse maps with objects, even though setting object properties works for maps, it will use

the feature of the generic object, and won't be able to use map methods

  

destructuring

  { key } = object gets the element with key from object

  [h, ...t] = array deconstructing

  

Object literal: {}

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

  

for..in operates over the keys of an object

  

inheritance

  class extends superclass

  constructor call super() for the super constructor

  'this.' won't work before super is called on the constructor

  

static methods can be called from class, but not from instances

  static method()

  

modules

  exporting and importing code

  in node, we use module.exports and require() instead of the import/export syntax

  export { resourceToExport, otherResource }

  import {resource} from './place'

  you can only use import and export inside modules, not regular scripts

  modules use strict mode automatically

  default export don't need braces

    export default function -> {function as default}

    import whateverName from 'module' -> same as import {default as whateverName} from 'module'

    values inside the default can't be extract directly with an import, they must be taken after the default is imported

  export foo as bar

  import foo as bar

  better to rename in imports and leave modules as they are

  import to object, creating own namespace

    import * as Module from 'module'

    Module.function();

  classes can be imported and exported as well

  modules can be aggregated

    export {x} from 'modules/x'

    export {y} from 'modules/y'

    import {x, y} from 'modules/aggregator'