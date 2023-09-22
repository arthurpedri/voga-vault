### Indentation
- Mostly ==2 spaces==, but flexible.

- When you need to access both the value and the index, you can use `.forEach()` instead of `for (;;)`. Write:
```js
const gerbils = ["Zoé", "Chloé"];
gerbils.forEach((gerbil, i) => {
  console.log(`Gerbil #${i}: ${gerbil}`);
});
```
