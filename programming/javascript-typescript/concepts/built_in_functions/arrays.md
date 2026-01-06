# Basic Array Methods

## Adding & Removing

### `push()`

- It **adds** element(s) to the end
- It changes the original array

```
let arr = [1, 2];
arr.push(3); // [1, 2, 3]
```

### `pop()`

- **removes** the **last** element
- changes original array
- returns the removed value

```
arr.pop(); // returns 3
```

### `shift()`

- **adds** element(s) to the **start**
- changes original array

```
arr.unshift(0); // [0, 1, 2]
```

### `unshift()`

- **removes** the **first** element
- changes original array

```
arr.shift(); // removes 0
```

## Finding & Checking Elements

### `indexOf()`

- returns index of first match
- returns `-1` if not found

```
[1, 2, 3].indexOf(2); // 1
```

### `includes()`

- checks if value exists → `true` / `false`

```
[1, 2, 3].includes(2); // true
```

### `find()`

- returns **first element** that matches a condition

```
[5, 10, 15].find(n => n > 9); // 10
```

### `findIndex()`

- same as `find()` but returns the **index**

```
[5, 10, 15].findIndex(n => n > 9); // 1
```

## Copying & Extracting

### `slice(slice, end)`

- extracts part of array
- doesn't change original

```
let arr = [1, 2, 3, 4];
arr.slice(1, 3); // [2, 3]
```

### `splice(start, deleteCount, ...items)`

- removes / inserts elements
- changes original array

```
arr.splice(1, 2); // removes 2 elements from index 1
```

## Combining & Converting

### `concat()`

- combines arrays
- doesn't change original

```
[1, 2].concat([3, 4]); // [1, 2, 3, 4]
```

### `join(seperator)`

- converts array to string

```
["a", "b", "c"].join("-"); // "a-b-c"
```

## Looping & Transforming 

### `forEach()`

- runs function on each element
- returns nothing

```
[1, 2, 3].forEach(n => console.log(n));
```

### `map()`

- transforms each element
- returns **new array**

```
[1, 2, 3].map(n => n * 2); // [2, 4, 6]
```

### `filter()`

- keeps elements that pass a test

```
[1, 2, 3, 4].filter(n => n % 2 === 0); // [2, 4]
```

### `reduce()`

- reduces array to a single value 

```
[1, 2, 3].reduce((sum, n) => sum + n, 0); // 6
```

## Testing Conditions

### `some()`

- returns `true` if **any** element passes

```
[1, 2, 3].some(n => n > 2); // true
```

### `every()`

- returns `true` if **all** elements pass

```
[1, 2, 3].every(n => n > 0); // true
```

## Sorting & Reordering

### `sort()`

- sorts array **as strings by default**
- changes original array

```
[10, 2, 5].sort((a, b) => a - b); // [2, 5, 10]
```

### `reverse()`

- reverses array
- changes original

```
[1, 2, 3].reverse(); // [3, 2, 1]
```

## Utility Methods

### `length`

- number of elements

```
[1, 2, 3].length; // 3
```

### `flat(depth)`

- flattens nested arrays

```
[1, [2, [3]]].flat(2); // [1, 2, 3]
```

### `fill(value, start, end)`

- fills array with value

```
[1, 2, 3].fill(0); // [0, 0, 0]
```

### `Array.isArray()`

- checks if value is an array

```
Array.isArray([1, 2]); // true
```

### `Array.from()`

- converts iterable to array

```
Array.from("abc"); // ["a", "b", "c"]
```

## Less common ones

### `toString()`

- converts the array into a **comma-seperated string**
- same result as `join(",")`

### `at(index)`

- returns element at given index
- supports **negative indexing**

### `delete()`

- deletes an element **but does NOT reindex**
- leaves an **empty slot (hole)**

### `copyWithin()`

- copies part of the array **within itself**
- overwrites existing elements

### `toSpliced()`

- **Non-mutating version of** `splice()`
- returns a new array 
- ES2023+