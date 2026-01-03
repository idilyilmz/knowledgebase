# Vue

## Directives

### 1. `v-on`

The `v-on` directive is used to bind event listeners to DOM elements. It listens for events like `click`, `input`, `submit`, etc., and triggers a specified method or JavaScript expression when the event occurs.

#### Syntax:

```
<button v-on:click="handleClick">Click Me</button>
```
#### Shortcut:
You can use the shorthand @ instead of v-on:

```
<button @click="handleClick">Click Me</button>
```

#### How it works:

When the button is clicked, the method `handleClick` in your Vue component is executed.

#### `$event` with `v-on`
In Vue.js, `$event` is a special variable that represents the event object in event handlers. It is automatically available when using Vue's event binding (`v-on` or `@` shorthand).

##### When to Use `$event`

You use `$event` to access details about the event that triggered a method or handler, such as the type of event, the target element, or any additional data the event provides.

##### Example Usage
1. **Passing `$event` to a Method**

You can pass the `$event` object to a method if you need to handle the event explicitly:

```
<template>
  <button @click="handleClick($event)">Click Me</button>
</template>

<script>
export default {
  methods: {
    handleClick(event) {
      console.log(event); // Logs the event object
      console.log(event.target); // Logs the element that triggered the event
    },
  },
};
</script>
```
2. **Using `$event` in Inline Handlers**

You can use `$event` directly in an inline event handler to access properties of the event:

```
<template>
  <input @input="value = $event.target.value" />
  <p>You typed: {{ value }}</p>
</template>

<script>
export default {
  data() {
    return {
      value: '',
    };
  },
};
</script>
```

3. **When `$event` Is Necessary**

When passing multiple arguments to a method, `$event` is explicitly required to pass the event object:
```
<template>
  <button @click="handleClick('argument', $event)">Click Me</button>
</template>

<script>
export default {
  methods: {
    handleClick(arg, event) {
      console.log(arg); // "argument"
      console.log(event); // The event object
    },
  },
};
</script>
```

##### When `$event` Isn't Needed

If you're simply binding a method without additional arguments, Vue automatically passes the event object to the method, so `$event` isn't explicitly required:

```
<template>
  <button @click="handleClick">Click Me</button>
</template>

<script>
export default {
  methods: {
    handleClick(event) {
      console.log(event); // The event object
    },
  },
};
</script>
```

##### Summary

`$event` is a way to explicitly pass the event object in Vue.js. It's most useful when:
- You need to access event details in a method.
- You're passing multiple arguments to a method and still need the event object.

### 2. `v-model`

The `v-model` directive creates a **two-way data binding** between a form input element and a data property. This means that changes in the input will update the data property, and changes in the data property will update the input.

#### Syntax:
```
<input v-model="message" />
<p>{{ message }}</p>
```

#### How it works:
- typing into the input box updates the `message` property in real-time
- if you programmatically change the `message` property, the input box updates accordingly.

### `v-model` with `defineModel`

### 3. `v-for`

The `v-for` directive is used to render a list of items by iterating over an array or an object. It dynamically generates DOM elements for each item in the collection.

#### Syntax:
```
<ul>
  <li v-for="item in items" :key="item.id">
    {{ item.name }}
  </li>
</ul>
```

#### How it works:
- the `items` array is iterated over, and for each `item`, a `<li>` element is created
- the `:key` attribute is required for tracking each item uniquely, improving performance and avoiding rendering issues.

#### Example items array:
```
data() {
  return {
    items: [
      { id: 1, name: 'Apple' },
      { id: 2, name: 'Banana' },
      { id: 3, name: 'Cherry' }
    ]
  };
}
```

## Comparison Table 
| Directive    | Purpose                                   |   Example                                         |
|--------------|-------------------------------------------|---------------------------------------------------|
| `v-on`       | Binds event listeners to DOM elements     |`<button v-on:click="doSomething"></button>`       |
|`v-model`     | Creates two-way binding with form inputs  | `<input v-model="value" />`                       |
| `v-for`      | Renders a list by iterating over data     | `<li v-for="item in items" :key="item.id"></li>`  |

### 4. `v-bind`

The `v-bind` directive in Vue.js is used to **dynamically bind an attribute**, a **class**, or a **style** to **an expression or data property**. It allows you to make attributes reactive, so their values change automatically when the underlying data changes.

#### Common Use Cases for `v-bind`

##### 1. Binding Attributes:
- you can bind any attribute (e.g., `src`, `alt`, `href`, etc.) to a dynamic value.

**Example**:

```<img v-bind:src="imageUrl" v-bind:alt="imageDescription" />
```
- if `imageUrl = 'path/to/image.jpg'` and `imageDescription = 'A beautiful view'`, the resulting HTML will be:

```<img src="path/to/image.jpg" alt="A beautiful view" />
```

##### 2. Binding Classes:
- dynamically add or remove CSS classes.

**Example**:

```<div v-bind:class="{ active: isActive, error: hasError }"></div>
```
- if `isActive = true` and `hasError = false`, the resulting class will be:

```<div class="active"></div>
```

##### 3. Binding Inline Styles:
- dynamically apply inline styles.

**Example**:

```
<div v-bind:style="{ color: textColor, fontSize: fontSize + 'px' }"></div>
```

- if `textColor = 'red'` and `fontSize = 14`, the resulting inline style will be:

```
<div style="color: red; font-size: 14px;"></div>
```