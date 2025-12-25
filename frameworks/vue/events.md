# Vue

## Understanding Events and Methods in Vue.js

In Vue.js, **events** and **methods** work together to create dynamic, interactive applications. Events allow you to detect and respond to user actions, while methods define the logic to execute when an event occurs.

### 1. What Are Events in Vue?
- events are user interactions with the DOM, such as:
    - **mouse events**: `click`, `dblclick`, `mouseover`, `mouseout`
    - **keyboard events**: `keydown`, `keyup`, `keypress`
    - **form events**: `input`, `change`, `submit`, `focus`
    - **custom events**: Defined and emitted by Vue components.
- vue handles these events using the `v-on` directive (or its shorthand `@`).

**Example**:

```
<template>
  <button @click="handleClick">Click Me</button>
</template>

<script>
export default {
  methods: {
    handleClick() {
      alert("Button clicked!");
    },
  },
};
</script>
```

### 2. What Are Methods in Vue?
- methods are reusable JavaScript functions defined inside the `methods` option of a Vue component. They are primarily used to:
    - handle events.
    - encapsulate business logic or UI interactions.
    - manipulate component data or trigger actions.
- defining methods:
```
<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    increment() {
      this.count++;
    },
    resetCount() {
      this.count = 0;
    },
  },
};
</script>
```
### 3. Using Events and Methods Together

Events trigger the execution of methods. For example:

***Example***: Counter Component

```
<template>
  <div>
    <p>Count: {{ count }}</p>
    <button @click="increment">Increment</button>
    <button @click="resetCount">Reset</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    increment() {
      this.count++;
    },
    resetCount() {
      this.count = 0;
    },
  },
};
</script>
```
### 4. Passing Parameters to Methods

You can pass arguments to methods when binding them to events.

**Example**:

```
<template>
  <button @click="greet('Vue')">Say Hello</button>
</template>

<script>
export default {
  methods: {
    greet(name) {
      alert(`Hello, ${name}!`);
    },
  },
};
</script>
```
### 5. Accessing the Event Object

If you need access to the native DOM event object, you can pass it as an argument using `$event`.

**Example**:
```
<template>
  <input @input="handleInput($event)" placeholder="Type something" />
</template>

<script>
export default {
  methods: {
    handleInput(event) {
      console.log(event.target.value); // Logs the input value
    },
  },
};
</script>
```
### 6. Inline Methods vs. Defined Methods

You can use inline expressions directly in the template for simple logic:
```
<template>
  <button @click="count++">Increment</button>
</template>
```

However, for more complex logic, define a method:
```
<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    increment() {
      this.count++;
    },
  },
};
</script>
```
### 7. Event Modifiers

Vue provides event modifiers to simplify common event-handling patterns.

| Modifier   | Description                                                       | Example                                 |
|------------|-------------------------------------------------------------------|-----------------------------------------|
| `.stop`    | Stops event propagation (like `event.stopPropagation()`)          | `<button @click.stop="handleClick">`    |
| `.prevent` | Prevents default browser behavior (like `event.preventDefault()`) | `<form @submit.prevent="handleSubmit">` |
| `.capture` | Adds the event listener in capture mode.                          | `<div @click.capture="handleClick">`    |
| `.self`    | Triggers the event only on the element itself.                    | `<div @click.self="handleClick">`       |
| `.once`    | Ensures the handler is executed only once.                        | `<button @click.once="logOnce">`        |

### 8. Lifecycle of Events and Methods
1. **Event Occurs**:
A user interacts with the application (e.g., clicks a button).

2. **Event Handler**:
The `v-on` directive binds the event to a specific method.

3. **Method Executes**:
The bound method is executed, performing any logic (e.g., updating data, making API calls).

4. **Reactivity Updates**:
If the method modifies reactive data, the DOM automatically updates.

### 9. Example: Putting It All Together

Interactive Form Example
```
<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <input v-model="name" placeholder="Enter your name" />
      <button type="submit">Submit</button>
    </form>
    <p v-if="submitted">Hello, {{ name }}!</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      submitted: false,
    };
  },
  methods: {
    handleSubmit() {
      this.submitted = true;
    },
  },
};
</script>
```

### 10. Summary
- **Events**: Detect user actions (e.g., `click`, `input`) and bind them to logic using `v-on` or `@`.
- **Methods**: Define the logic to handle events or perform reusable actions.
- Combine events and methods to create dynamic, interactive features.
- Use event modifiers for better control over event behavior.