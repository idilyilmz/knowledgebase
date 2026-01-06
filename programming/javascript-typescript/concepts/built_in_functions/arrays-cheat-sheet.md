# JS Array Methods - Cheat Sheet

## Adds / Remove Elements

| Method        | Mutates? | Description            | Example              |
| ------------- | -------- | ---------------------- | -------------------- |
| `push()`      | ✅        | Add to end             | `arr.push(4)`        |
| `pop()`       | ✅        | Remove from end        | `arr.pop()`          |
| `unshift()`   | ✅        | Add to start           | `arr.unshift(1)`     |
| `shift()`     | ✅        | Remove from start      | `arr.shift()`        |
| `splice()`    | ✅        | Insert / remove        | `arr.splice(1,2)`    |
| `toSpliced()` | ❌        | Immutable `splice()`   | `arr.toSpliced(1,2)` |
| `delete`      | ✅        | Removes value only (❌) | `delete arr[1]`      |

## Access / Search

| Method        | Mutates? | Description                | Example                     |
| ------------- | -------- | -------------------------- | --------------------------- |
| `at()`        | ❌        | Index (supports negatives) | `arr.at(-1)`                |
| `indexOf()`   | ❌        | Find index                 | `arr.indexOf(3)`            |
| `includes()`  | ❌        | Check existence            | `arr.includes(3)`           |
| `find()`      | ❌        | First match                | `arr.find(x => x > 5)`      |
| `findIndex()` | ❌        | Index of match             | `arr.findIndex(x => x > 5)` |


## Iteration / Transformation 

| Method      | Mutates? | Returns     | Use Case     |
| ----------- | -------- | ----------- | ------------ |
| `forEach()` | ❌        | `undefined` | Side effects |
| `map()`     | ❌        | New array   | Transform    |
| `filter()`  | ❌        | New array   | Remove items |
| `reduce()`  | ❌        | Any value   | Sum / group  |
| `some()`    | ❌        | Boolean     | Any match    |
| `every()`   | ❌        | Boolean     | All match    |

## Copy / Combine / Convert

| Method         | Mutates? | Description      | Example             |
| -------------- | -------- | ---------------- | ------------------- |
| `slice()`      | ❌        | Copy portion     | `arr.slice(1,3)`    |
| `concat()`     | ❌        | Merge arrays     | `a.concat(b)`       |
| `flat()`       | ❌        | Flatten          | `arr.flat(2)`       |
| `join()`       | ❌        | To string        | `arr.join(",")`     |
| `toString()`   | ❌        | CSV string       | `arr.toString()`    |
| `Array.from()` | ❌        | Iterable → array | `Array.from("abc")` |

## Sort / Reorder

| Method         | Mutates? | Description            | Example                |
| -------------- | -------- | ---------------------- | ---------------------- |
| `sort()`       | ✅        | Sort (strings default) | `arr.sort((a,b)=>a-b)` |
| `reverse()`    | ✅        | Reverse                | `arr.reverse()`        |
| `toSorted()`   | ❌        | Immutable sort         | `arr.toSorted()`       |
| `toReversed()` | ❌        | Immutable reverse      | `arr.toReversed()`     |
| `copyWithin()` | ✅        | Copy inside array      | `arr.copyWithin(0,2)`  |

## Utility

| Method            | Mutates? | Description       | Example              |
| ----------------- | -------- | ----------------- | -------------------- |
| `length`          | ❌        | Size              | `arr.length`         |
| `fill()`          | ✅        | Fill values       | `arr.fill(0)`        |
| `with()`          | ❌        | Immutable replace | `arr.with(1,9)`      |
| `Array.isArray()` | ❌        | Check array       | `Array.isArray(arr)` |
