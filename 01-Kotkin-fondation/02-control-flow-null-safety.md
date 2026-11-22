# Control flow and null safety

## Introduction
Decisions (`if`, `when`) and repetition (`for`, `while`) drive every app. Null safety is the feature that prevents the most common crash in Java-style Android code.

## Learning outcomes
- Use `if` and `when` as expressions.
- Loop with `for` and ranges.
- Handle nullable values safely with `?.`, `?:` and `let`.

## Lesson

### if is an expression
```kotlin
val label = if (score >= 50) "Pass" else "Fail"
```

### when
```kotlin
fun grade(score: Int): String = when {
    score >= 70 -> "A"
    score >= 60 -> "B"
    score >= 50 -> "C"
    else -> "F"
}

when (day) {
    "Sat", "Sun" -> println("Weekend")
    else -> println("Weekday")
}
```

### Loops and ranges
```kotlin
for (i in 1..5) println(i)            // 1 to 5
for (i in 5 downTo 1 step 2) println(i)
var n = 3
while (n > 0) { println(n); n-- }
```

### Null safety
A type is non-null by default. Add `?` to allow null.
```kotlin
var nickname: String? = null
// nickname.length          // compile error
nickname?.length            // safe call: null if nickname is null
val len = nickname?.length ?: 0   // elvis: default when null
nickname?.let { println("Hi $it") }   // runs only if not null
```
Avoid `!!` (it throws if null). If you write `!!`, ask what could make it null.

### Smart casts
```kotlin
fun describe(x: Any) = when (x) {
    is String -> "text of length ${x.length}"
    is Int -> "number ${x + 1}"
    else -> "unknown"
}
```

## Practice
`projects/kotlin-exercises/exercises/02_control_flow_nullability.kt`: write a grading function and a safe email-domain extractor.

## Knowledge check
- Why is `val x = if (...) a else b` valid Kotlin?
- What do `?.` and `?:` do?
- Why is `!!` considered risky?

## Additional resources
- [Control flow](https://kotlinlang.org/docs/control-flow.html)
- [Null safety](https://kotlinlang.org/docs/null-safety.html)

Previous: [Variables, types and functions](01-variables-types-functions.md) · Next: [Classes, data and sealed types](03-classes-data-sealed.md)
