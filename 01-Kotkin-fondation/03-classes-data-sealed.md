# Classes, data classes and sealed types

## Introduction
You model your app's world with classes. Data classes hold UI state; sealed types model "one of several possibilities" such as Loading / Success / Error.

## Learning outcomes
- Write classes with properties and methods.
- Use data classes and `copy`.
- Model states with `enum` and `sealed interface`.
- Use `object` and `companion object`.

## Lesson

### Classes
```kotlin
class Student(val name: String, var grade: Int) {
    fun isPassing() = grade >= 50
}
val s = Student("Ada", 72)
println(s.isPassing())
```

### Data classes
```kotlin
data class User(val name: String, val email: String)

val u = User("Ada", "ada@example.com")
val renamed = u.copy(name = "Ada L.")   // new object, one field changed
println(u)                              // User(name=Ada, email=ada@example.com)
```
You'll use `copy` constantly: Compose state is replaced, not mutated.

### Enums
```kotlin
enum class Level { BEGINNER, INTERMEDIATE, ADVANCED }
```

### Sealed types
```kotlin
sealed interface LoadState {
    data object Loading : LoadState
    data class Success(val items: List<String>) : LoadState
    data class Error(val message: String) : LoadState
}

fun render(state: LoadState) = when (state) {
    LoadState.Loading -> "Loading..."
    is LoadState.Success -> "Got ${state.items.size} items"
    is LoadState.Error -> "Oops: ${state.message}"
}
```
Because the interface is sealed, `when` must cover every case, and the compiler tells you if you miss one.

### object and companion object
```kotlin
object Config { const val BASE_URL = "https://api.example.com" }

class Api {
    companion object { const val TIMEOUT = 30 }
}
```

### Interfaces
```kotlin
interface Greeter { fun greet(): String }
class English : Greeter { override fun greet() = "Hello" }
```

## Practice
`projects/kotlin-exercises/exercises/03_classes_sealed.kt`: model a quiz question and a `LoadState`.

## Knowledge check
- What does `copy` do and why is it useful for UI state?
- Why must a `when` over a sealed type be exhaustive?
- When would you use `object` instead of `class`?

## Additional resources
- [Classes](https://kotlinlang.org/docs/classes.html)
- [Data classes](https://kotlinlang.org/docs/data-classes.html)
- [Sealed classes and interfaces](https://kotlinlang.org/docs/sealed-classes.html)

Previous: [Control flow and null safety](02-control-flow-null-safety.md) · Next: [Collections and lambdas](04-collections-lambdas.md)
