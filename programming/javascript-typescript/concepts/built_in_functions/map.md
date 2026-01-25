# Map (Key–Value Collection)

- Stores key–value pairs
- Keys can be **any type**
- Maintains **insertion order**
- Not the same as plain objects `{}`

## Creating a Map

### `new Map(iterable?)`

- Creates a new Map instance
- Optional iterable must be `[key, value]` pairs

## Adding & Updating

### `set(key, value)`

- adds or updates a key

## Reading & Checking

### `get(key)`

### `has(key)`

## Removing

### `delete(key)`

### `clear()`

## Size & Iteration

### `size`

### `forEach()`

## Keys, Values, Entries

### `keys()`

### `values()`

### `entries()`

## Converting

### Map → Array

## Map vs Object

| Feature | Map | Object |
|------|-----|--------|
| Key types | any | string / symbol |
| Order | preserved | not guaranteed |
| Size | `.size` | manual |
| Performance | better for frequent adds/removes | okay for static data |
