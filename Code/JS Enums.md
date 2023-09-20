## No support for native [[Enumerated type|enum]] type
- A workaround is made using `Object.freeze()`.
```js
const directions = Object.freeze({ 
  north: 0,
  south: 1,
  east: 2,
  west: 3
});
let d = directions.north;
Object.keys(directions).forEach((direction) =>
  console.log('direction:', direction)
);
/* 
Prints:
direction: north
direction: south
direction: east
direction: west
*/
```
