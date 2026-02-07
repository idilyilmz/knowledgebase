# `ref`

## When to use `ref`

In **TypeScript (especially with React, Vue, or vanilla TS/JS)**, `ref` is used when you need a **mutable reference** to something that should persist across re-renders (in React) or reactive changes (in Vue).

Here’s a breakdown of common cases:

### 🔹 In **React (TypeScript + React)**

You use `useRef<T>()` when:

1. **Accessing DOM elements directly**

   ```tsx
   const inputRef = useRef<HTMLInputElement>(null);

   return <input ref={inputRef} />;
   // Later: inputRef.current?.focus();
   ```

   * Here, `ref` gives you a reference to the DOM node.

2. **Storing mutable values that don’t trigger re-renders**

   ```tsx
   const timerRef = useRef<number | null>(null);

   useEffect(() => {
     timerRef.current = window.setInterval(() => console.log("tick"), 1000);
     return () => clearInterval(timerRef.current!);
   }, []);
   ```

   * Unlike `useState`, updating `ref.current` does **not** cause a re-render.

3. **Exposing methods in custom components**

   ```tsx
   type InputHandle = {
     focus: () => void;
   };

   const CustomInput = React.forwardRef<InputHandle>((props, ref) => {
     const inputRef = useRef<HTMLInputElement>(null);

     React.useImperativeHandle(ref, () => ({
       focus: () => inputRef.current?.focus(),
     }));

     return <input ref={inputRef} {...props} />;
   });
   ```

### 🔹 In **Vue (TypeScript + Vue 3)**

You use `ref()` from Vue’s reactivity system when:

1. **Defining reactive primitives**

   ```ts
   import { ref } from "vue";

   const count = ref<number>(0);
   count.value++; // reactive
   ```

2. **Referencing DOM elements**

   ```vue
   <template>
     <input ref="inputEl" />
   </template>

   <script setup lang="ts">
   import { ref, onMounted } from "vue";

   const inputEl = ref<HTMLInputElement | null>(null);

   onMounted(() => {
     inputEl.value?.focus();
   });
   </script>
   ```

### 🔹 In **Vanilla TypeScript (no framework)**

You’d rarely need `ref`, but a similar concept is keeping a **mutable object reference**:

```ts
let countRef: { current: number } = { current: 0 };
countRef.current++;
```

✅ **Rule of Thumb:**

* Use `ref` when you need a **persistent, mutable value** across renders/reactivity cycles.
* Use `state` (React) or `reactive` (Vue) when you want changes to trigger UI updates.
