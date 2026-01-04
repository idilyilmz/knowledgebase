# JavaScript Functions — Basics & Core Concepts
## 1. What Is a Function?

A <strong>function</strong> is a reusable block of code that performs a task.
Functions help:
- Organize your code
- Avoid duplication
- Make logic reusable
- Encapsulate behavior

## 2. Function Declaration
``` 
function greet(name) {
  return `Hello, ${name}!`;
}
``` 

Characteristics:
- Can be called before they are defined → hoisted
- Readable, good for most use cases

## 3. Function Expression
``` 
const greet = function(name) {
  return `Hello, ${name}`;
};
``` 

Characteristics:
- Assigned to a variable
- Not hoisted (cannot call before defined)
- Useful for callbacks

## 4. Arrow Functions
``` 
const greet = (name) => {
  return `Hello, ${name}`;
};
``` 

Short form:
``` 
const double = n => n * 2;
``` 

Key differences:
- Do not have their own `this`
- No `arguments` object
- Cleaner syntax, especially for callbacks

## 5. Parameters vs Arguments
``` 
function add(a, b) {  // parameters
  return a + b;
}

add(3, 4); // arguments
``` 
- Parameters → variables in the function definition
- Arguments → actual values you pass

## 6. Default Parameters
``` 
function greet(name = "stranger") {
  return `Hello, ${name}`;
}
``` 

## 7. Rest Parameters (`...args`)
``` 
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}

sum(1, 2, 3); // 6
``` 
## 8. Return Values
``` 
function multiply(a, b) {
  return a * b;
}
``` 

If no `return` is used → returns `undefined`.

## 9. Anonymous Functions

Functions without names, often used for callbacks:
``` 
setTimeout(function() {
  console.log("Hello!");
}, 1000);
``` 

Arrow version:
``` 
setTimeout(() => console.log("Hi"), 1000);
``` 
## 10. Callback Functions

A function passed into another function:
``` 
function processUser(name, callback) {
  callback(name);
}

processUser("Pookie", (n) => console.log(`Hello ${n}`));
``` 

Used heavily in:
- Event handlers
- Array methods
- Promises
- Async code

## 11. Higher Order Functions

A function that:
- <i>takes a function as an argument</i>
- <i>or returns a function</i>

Example:
``` 
function makeMultiplier(x) {
  return function(n) {
    return n * x;
  };
}

const double = makeMultiplier(2);
double(5); // 10
``` 

This pattern is very powerful.

## 12. Immediately Invoked Function Expression (IIFE)

Runs instantly:
``` 
(function() {
  console.log("Runs immediately");
})();
``` 

Useful for:
- Creating isolated scope
- Avoiding global variables

## 13. `this` in Functions (Basic)
In regular functions → `this` depends on how they are called
```
const user = {
  name: "Ella",
  show() {
    console.log(this.name);
  }
};
```

user.show(); // "Pookie"

In arrow functions → `this` is taken from outer scope
``` 
const user = {
  name: "Pookie",
  show: () => {
    console.log(this.name); // NOT "Pookie"
  }
};
``` 

## 14. Functions as Objects

Functions in JavaScript are first-class citizens.
This means:
- You can store them in variables
- Pass them as arguments
- Return them from other functions
- Attach properties to them

Example:
``` 
function greet() {}
greet.description = "Says hello";
``` 

