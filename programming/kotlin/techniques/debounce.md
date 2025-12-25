# Kotlin

## Techniques

### Debounce

In Kotlin, **debounce** is a technique used to limit the rate at which a function is executed, especially in situations where a certain action is triggered multiple times in quick succession, like typing in a search bar or scrolling. It helps prevent unnecessary or excessive calls to the function and improves performance.

#### How Debounce Works:

Debouncing ensures that a function is only called after a specified delay, and only if there are no additional calls within that delay period. If the function is called multiple times within the delay window, the previous calls are ignored, and only the last one triggers the action after the delay.

#### Example of Debouncing with Kotlin:

To implement debouncing, you can use `CoroutineScope` with `delay` and `Job` to cancel previous invocations if a new one occurs before the delay expires.
```
import kotlinx.coroutines.*

fun main() {
    val scope = CoroutineScope(Dispatchers.Main)
    var debounceJob: Job? = null

    fun debounce(action: () -> Unit, delayMillis: Long = 300) {
        debounceJob?.cancel() // Cancel any previous job
        debounceJob = scope.launch {
            delay(delayMillis) // Wait for the delay time
            action() // Run the action
        }
    }

    // Simulating rapid calls
    for (i in 1..5) {
        debounce({
            println("Action triggered at ${System.currentTimeMillis()}")
        })
    }
}
```
#### In this example:
- The `debounce` function cancels any previous jobs if they haven't finished executing yet, and then delays the execution by the specified amount of time (`delayMillis`).
- After all rapid calls, only the last one will execute.

Debouncing is useful in scenarios like:
- **Search input fields**: Avoid querying the backend with every keystroke.
- **Button clicks**: Prevent multiple clicks in a short period from triggering the same action multiple times.