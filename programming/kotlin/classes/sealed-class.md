# Classes

## Sealed Class

A **sealed class** in Kotlin is a special type of class that restricts which other classes can inherit from it. It allows you to define a limited set of subclasses, ensuring that all subclasses are known at compile time. This is useful in situations where you want to represent a restricted hierarchy of types, such as representing different states or outcomes.

Here are some key points about sealed classes in Kotlin:
1. **Restricted Inheritance**: All subclasses of a sealed class must be defined within the same file. This ensures that the compiler can know all possible subclasses at compile time.
2. **Use Case**: Sealed classes are commonly used in situations like representing a set of possible states, such as success, error, or loading states in a UI.
3. **Pattern Matching**: Sealed classes work well with `when` expressions, as the compiler can ensure all possible subclasses are covered, making your code more robust and preventing errors.

### Example:
```
sealed class Result

data class Success(val data: String) : Result()
data class Error(val exception: Exception) : Result()
object Loading : Result()

fun handleResult(result: Result) {
    when (result) {
        is Success -> println("Data: ${result.data}")
        is Error -> println("Error: ${result.exception}")
        Loading -> println("Loading...")
    }
}
```

In the example above, `Result` is a sealed class, and it has three subclasses: `Success`, `Error`, and `Loading`. When using `when`, Kotlin knows that all subclasses are covered because they are defined within the same file.

Sealed classes provide both safety (compile-time checking) and clarity when dealing with a fixed set of types.