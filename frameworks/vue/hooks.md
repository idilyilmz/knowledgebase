# Hooks

In **Vue 3**, when people talk about a *hook*, they usually mean a **reusable function built with the Composition API** that encapsulates logic you want to share across components.

Think of it like this:

* In React, there are official *hooks* (e.g., `useState`, `useEffect`).
* In Vue 3, you can create your own **"composable" functions**, often called *hooks*, that start with `use...`.

### Example scenario

You said you have a **dialog** and a **page** that both use the same logic. Instead of duplicating code, you can move that logic into a hook.

---

### Without a hook (duplicate logic in two components)

```vue
<script setup>
import { ref } from 'vue'

const isOpen = ref(false)

function open() {
  isOpen.value = true
}

function close() {
  isOpen.value = false
}
</script>
```

You might copy this into both your **Dialog.vue** and **Page.vue**.

---

### With a hook (shared logic)

Create a composable file, e.g. `useDialog.js`:

```js
// composables/useDialog.js
import { ref } from 'vue'

export function useDialog() {
  const isOpen = ref(false)

  function open() {
    isOpen.value = true
  }

  function close() {
    isOpen.value = false
  }

  return {
    isOpen,
    open,
    close
  }
}
```

Now in both your **Dialog.vue** and **Page.vue**:

```vue
<script setup>
import { useDialog } from '@/composables/useDialog'

const { isOpen, open, close } = useDialog()
</script>
```