# Asynchronous JavaScript — Basics & Core Concepts

JavaScript is single-threaded, meaning it can run only one thing at a time.
But thanks to the browser and Node.js environment, it can handle tasks like:
- network requests
- timers
- reading files - 
without blocking the main thread.

This is where asynchronous JavaScript comes in.

## 1. The Event Loop (Core Idea)

Even though JS is single-threaded, the browser/Node provides:

- Web APIs (timers, fetch, DOM events)
- A callback/task queue

The Event Loop decides when JS should run a callback after an async task finishes.

Simply put:
1. JS sends async task to browser API
2. Browser handles it in the background
3. When done, callback is queued
4. Event loop runs it when the call stack is free

This allows JS to stay fast and non-blocking.

## 2. Callbacks (Oldest async method)
```
setTimeout(() => {
  console.log("Done!");
}, 1000);
```

Used heavily before Promises existed.

Problems:

- Hard to read
- Error handling is messy
- “Callback hell”

## 3. Promises (Modern async foundation)

A Promise represents a value that will be available in the future.
```
const promise = new Promise((resolve, reject) => {
  resolve("Success!");
});
```

Consume it with .then and .catch:
```
promise
  .then(value => console.log(value))
  .catch(error => console.error(error));
```

Promise states:
- pending
- fulfilled
- rejected

## 4. Fetch API (Practical example)
```
fetch("https://api.example.com/data")
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

Fetch returns a Promise.

## 5. Async/Await (The modern standard)

`async/await` makes async code look like synchronous code.
```
async function getData() {
  try {
    const res = await fetch("https://api.example.com/data");
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error("Error:", err);
  }
}
```

### Why it’s better:
- Cleaner
- Easier to read
- Works on top of Promises

## 6. Parallel vs Sequential Execution
### Sequential (one after another)
```
await task1();
await task2();
```

### Parallel (run at the same time)
```
await Promise.all([task1(), task2()]);
```

## 7. Microtasks vs Macrotasks (Important detail)

Two async queues:

### Microtasks (higher priority):
- `.then()`
- `catch`
- `async/await` resolution

### Macrotasks (lower priority):
- `setTimeout`
- `setInterval`
- DOM events

Example:
```
setTimeout(() => console.log("timeout"), 0);

Promise.resolve().then(() => console.log("promise"));

```
Output:
```
promise
timeout
```

Because microtasks run before macrotasks.

## 8. Common Async Patterns
### Retry logic

Run again if a request fails.

### Debouncing / Throttling

Useful for search inputs, scroll events.

### Promise.all()

Run tasks in parallel.

### Promise.race()

Returns the first promise to finish.