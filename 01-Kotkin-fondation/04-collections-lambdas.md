# Collections and lambdas

## Introduction
Lists drive screens, and lambdas are how you handle clicks and pass behaviour around. Compose callbacks like `onClick = { ... }` are lambdas.

## Learning outcomes
- Create and transform `List`, `Set` and `Map`.
- Use `map`, `filter`, `sortedBy`, `groupBy`.
- Write lambdas and higher-order functions.
- Use scope functions (`let`, `apply`).

## Lesson

### Collections
```kotlin
val names = listOf("Ada", "Bola", "Chidi")          // read-only
val mutable = mutableListOf("Ada")
mutable.add("Bola")

val ages = mapOf("Ada" to 20, "Bola" to 22)
println(ages["Ada"])                                 // 20 (Int?)
val unique = setOf(1, 2, 2, 3)                       // [1, 2, 3]
```

### Transforming
```kotlin
val scores = listOf(45, 60, 82, 91)
scores.filter { it >= 60 }              // [60, 82, 91]
scores.map { it + 5 }                   // [50, 65, 87, 96]
scores.sortedByDescending { it }        // [91, 82, 60, 45]
scores.sum(); scores.average(); scores.maxOrNull()

data class Student(val name: String, val level: Int)
val students = listOf(Student("Ada", 1), Student("Bola", 2), Student("Chidi", 1))
students.groupBy { it.level }           // Map<Int, List<Student>>
students.firstOrNull { it.name == "Bola" }
```

### Lambdas
```kotlin
val double: (Int) -> Int = { x -> x * 2 }
val shout: (String) -> String = { it.uppercase() }   // `it` is the single parameter
println(double(4))
```

### Higher-order functions
```kotlin
fun repeatAction(times: Int, action: (Int) -> Unit) {
    for (i in 1..times) action(i)
}
repeatAction(3) { println("Round $it") }   // trailing lambda syntax
```
Trailing lambda syntax is exactly how you'll write `Button(onClick = { }) { Text("Hi") }` in Compose.

### Scope functions
```kotlin
val text = StringBuilder().apply { append("Hello"); append(" World") }.toString()
user?.let { println(it.name) }
```

## Practice
`projects/kotlin-exercises/exercises/04_collections_lambdas.kt`: process a list of students with `filter`, `map` and `groupBy`.

## Knowledge check
- What's the difference between `listOf` and `mutableListOf`?
- What does `it` refer to in a lambda?
- Why is `Button(onClick = { }) { ... }` valid syntax?

## Additional resources
- [Collections overview](https://kotlinlang.org/docs/collections-overview.html)
- [Lambdas and higher-order functions](https://kotlinlang.org/docs/lambdas.html)

Previous: [Classes, data and sealed types](03-classes-data-sealed.md) · Next: [Project structure and Gradle](../02-android-foundations/01-project-structure-gradle.md)
