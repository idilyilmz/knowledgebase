http://vuetifyjs.com/en/components/virtual-scroller/#usage

## v-virtual-scroll (Vuetify)

`v-virtual-scroll` renders **large or infinite lists efficiently** by only mounting the items needed to fill the visible viewport, reusing DOM nodes as the user scrolls. It’s a performant alternative to pagination.

* **Introduced:** Vuetify v3.2.0 (Orion)
* **Scroll direction:** Vertical
* **Item sizing:** Supports both fixed and dynamic heights
* **Styling:** Renderless / unstyled (intended to be wrapped with components like `v-list-item`, `v-card`, etc.)

### How it works

* Only visible items are rendered
* Existing item components are **rehydrated with new data** during scroll
* Great for thousands of records with minimal DOM overhead

### Core API

* `items`: Array of data to render
* `height`: Required scroll container height

  * Must be a number or unit value (`px`, `vh`)
  * **Percentages (%) are not supported**
* `item-height` (optional):

  * Use when all items have a **uniform height** for better performance
  * Omit for **dynamic-height** items (auto-measured)

### Slots

* **Default slot** only
  Receives `{ item }` for rendering list content

### Layout requirements

* The component **does not define its own height**
* Height must be provided via:

  * `height` prop, or
  * A parent container with `display: flex`

### Renderless mode

* Does not auto-generate DOM nodes
* You must manually bind `itemRef` for virtualization to work

### When to use

* Large datasets (hundreds → thousands of items)
* Infinite scrolling UIs
* Performance-critical list rendering
