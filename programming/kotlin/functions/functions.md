# Kotlin

## 1 Functions

### `mutableStateOf`
In Kotlin, `mutableStateOf` is a function from Jetpack Compose's **State management** system. It is used to create an **observable state** that automatically triggers recomposition when its value changes.

#### How `mutableStateOf` Works:
- It wraps a value in a **MutableState** object.
- When the value changes, any **Composable** function that reads it **recomposes** automatically.
- It is **similar to a variable**, but it notifies the UI when updated.

**Example**:
```
import androidx.compose.runtime.*

@Composable
fun CounterApp() {
    var count by remember { mutableStateOf(0) }

    Button(onClick = { count++ }) {
        Text("Count: $count")
    }
}
```

#### Breaking it Down:
- `remember { mutableStateOf(0) }`
    - **remember**: Keeps the state alive during recomposition.
    - **mutableStateOf(0)**: Creates a state holding `0` initially.
- `var count by mutableStateOf(0)`
    - Uses **property delegation** (`by`) to avoid `count.value` every time.
- When `count` is updated (`count++`), **the UI updates automatically**.

#### When to Use mutableStateOf:
- When managing **local UI state** in Jetpack Compose.
- When you need a simple state variable that updates the UI.
- For state inside a `@Composable` function (use `remember` to persist it).

## 2. Navigation

### 2.1 `popBackStack()`

`popBackStack()` is a function used with Jetpack Navigation to navigate back in the navigation stack. If you use `popBackStack()` in a Floating Action Button (FAB), it typically means that when the FAB is clicked, the app will navigate back to the previous destination in the navigation stack.

**Example Usage**:
```
FloatingActionButton(
    onClick = {
        navController.popBackStack()
    }
) {
    Icon(Icons.Default.ArrowBack, contentDescription = "Back")
}
```

#### How `popBackStack()` Works:
- It removes the **top** destination from the back stack and navigates to the previous one.
- If there is no previous destination, the app may exit (depending on how the navigation graph is set up).
- You can optionally specify a destination and whether to **include** it in the pop action.

#### Additional Options:
- If you want to pop back to a specific destination, you can do:
```
navController.popBackStack(destinationId, inclusive = false)
```
- `destinationId`: The ID of the destination to pop back to.
- `inclusive = true`: Also removes the specified destination from the stack.