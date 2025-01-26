## Required
- When two statements are on the same line.
```js
var i = 0; i++ // <-- semicolon obligatory 
               // (but optional before newline) 
var i = 0 // <-- semicolon optional 
i++       // <-- semicolon optional
```
## Optional 
- After statements.
```js
var i;                        // variable declaration
i = 5;                        // value assignment
i = i + 1;                    // value assignment
i++;                          // same as above
var x = 9;                    // declaration & assignment
var fun = function() {...};   // var decl., assignmt, and func. defin.
alert("hi");                  // function call
```
## Avoid
- After a closing curly bracket (except for assignment statements seen [[#Optional|above]]).
```js
// NO semicolons after }:
if  (...) {...} else {...}
for (...) {...}
while (...) {...}

// BUT:
do {...} while (...);

// function statement: 
function (arg) { /*do this*/ } // NO semicolon after }
```