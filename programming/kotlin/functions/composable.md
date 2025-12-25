# Composable

In Kotlin, a **Composable function** is a special type of function used with Jetpack Compose, the modern UI toolkit for building Android apps. A Composable function is responsible for describing the UI components of your app in a declarative way.

## Key points about Composable functions:

1. Annotation: A Composable function is marked with the `@Composable` annotation.

Example:
```
@Composable
fun Greeting(name: String) {
    Text(text = "Hello, $name!")
}
```

2. **Declarative UI**: Composables define the UI hierarchy and behavior in a declarative manner. This means you describe *what* the UI should look like rather than *how* to update it.

3. **Recomposition**: When data changes, Jetpack Compose will automatically recompose the parts of the UI that are affected, ensuring the UI stays in sync with the app's state.

4. **Composable functions can be nested**: You can call other Composable functions inside a Composable function, allowing you to build complex UI hierarchies.

**Example**:
```
@Composable
fun UserProfile(name: String, age: Int) {
    Column {
        Greeting(name = name)
        Text(text = "Age: $age")
    }
}
```

5. **State management**: Jetpack Compose works seamlessly with state by using `remember`, `mutableStateOf`, and other tools to manage UI state.

In summary, a Composable function is used to define and display UI elements in Jetpack Compose, providing a simple, reactive way to create Android UIs.