# 1. JavaScript Basics

## 1.1 What is JavaScript?
JavaScript is a high-level, dynamic, interpreted programming language used mainly for the web.
### Runs in:
- Browsers (client-side)
- Servers (via Node.js)
### Supports:
- Functional programming
- Object-oriented programming
- Event-driven programming

## 1.2 Variables
`const` - Block-scoped, cannot be reassigned (but objects inside it can change).
`let` - Block-scoped variable that can be reassigned.
`var` - Function-scoped, old keyword — avoid unless maintaining legacy code.
### Example:
```
let age = 20;
const name = "Alex";
var oldWay = true;
```

## 1.3 Data Types
### Primitive Types
- string
- number
- boolean
- null
- undefined
- symbol
- bigint
### Reference Type
object (includes arrays, functions)
### Check type:
```
typeof "text"; // 'string'
``` 

## 1.4 Operators
### Arithmetic
`+ - * / % **`

### Comparison

`==` vs `===`
- `==` → checks value, allows type coercion
- `===` → checks value + type (use this)

### Logical
`&&`, `||`, `!`

## 1.5 Conditionals
```
if (age > 18) {
  console.log("Adult");
} else if (age === 18) {
  console.log("Just became adult");
} else {
  console.log("Minor");
}
```

### Switch
```
switch (color) {
  case "red":
    break;
  default:
}
```

## 1.6 Functions
### Function declaration
```
function add(a, b) {
  return a + b;
}
```

### Function expression
```
const add = function(a, b) {};
```
### Arrow function
```
const add = function(a, b) {};
```

## 1.7 Arrays
Create
```
const nums = [ 1, 2, 3]
```

Common methods
```
nums.push(4);     // add
nums.pop();       // remove
nums.map(x => x * 2);
nums.filter(x => x > 1);
nums.reduce((a, b) => a + b, 0);
```


## 1.8 Objects
```
const user = {
  name: "Idil",
  age: 22,
  isStudent: true
}
```

Access:
```
user.name
user["age"]
```

## 1.9 Loops
### For
```
for (let i = 0; i < 5; i++) {}
```

### For...of (arrays)
```
for (const value of nums) {}
```

### For...in (objects)
```
for (const key in user) {}
```

### While
```
while (count < 5) {}
```

## 1.10 Basic Console Usage
```
console.log("Hello");
console.error("Error!");
console.table({ name: "Alex", age: 21 });
```

## 1.11 Comments
```
// Single-line comment

/*
  Multi-line
  comment
*/
```