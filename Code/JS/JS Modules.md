### In node.js
- We use `module.exports` and `require()` instead of the `import/export` syntax.
- Node requires a special configuration option in `package.json'` to use import syntax or using the `.mjs` extension.
## Basics
```js
export { resourceToExport, otherResource }
import {resource} from './place'
```
- Modules use [[JS Strict Mode|strict mode]] automatically.
- default export doesn't need braces.
```js
export default function
import whateverName from 'module'
import {default as whateverName} from 'module' // This is the exact same as the line above
```
- Better to rename in imports and leave modules as they are.
### Import to object, creating own namespace
```js
import * as Module from 'module'
Module.function();
```
- Classes can be imported and exported as well.
### Modules can be aggregated
 ```js
export {x} from 'modules/x'
export {y} from 'modules/y'
import {x, y} from 'modules/aggregator'
```