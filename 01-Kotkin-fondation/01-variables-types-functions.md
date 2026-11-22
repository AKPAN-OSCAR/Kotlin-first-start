# Variables, types and functions

## Introduction
Kotlin is the language of modern Android. Everything in Compose is a Kotlin function, so this lesson matters more than it looks.

## Learning outcomes
- Declare values with `val` and `var`.
- Use the basic types and string templates.
- Write functions with parameters, defaults and return values.

## Lesson

### val vs var
```kotlin
val name = "Ada"      // read-only: cannot be reassigned
var score = 0         // mutable: can change
score = 10
```
Prefer `val`. Use `var` only when the value must change. Kotlin infers the type, but you can write it: `val age: Int = 20`.

### Basic types
`Int`, `Long`, `Double`, `Boolean`, `Char`, `String`. There is no implicit conversion: `val d: Double = 5.toDouble()`.

### String templates
```kotlin
val user = "Ada"
println("Hello, $user! 2 + 2 = ${2 + 2}")
```

### Functions
```kotlin
fun add(a: Int, b: Int): Int {
    return a + b
}

fun square(x: Int) = x * x          // single-expression function

fun greet(name: String, greeting: String = "Hello") {
    println("$greeting, $name")
}

greet("Ada")                        // uses the default
greet(greeting = "Hi", name = "Ada") // named arguments
```
A function with no useful return value returns `Unit` (you can leave it out). Compose functions return `Unit` and describe UI.

### main
```kotlin
fun main() {
    println("Hello, Kotlin")
}
```
You can run this in the [Kotlin Playground](https://play.kotlinlang.org/) with no setup.

## Practice
Open `projects/kotlin-exercises/exercises/01_basics.kt`, fill in each `TODO`, and run it. Compare with the file in `solutions/` only after you've tried.

## Knowledge check
- When would you choose `var` over `val`?
- What does `fun square(x: Int) = x * x` return, and how does Kotlin know the type?
- What is a named argument and why is it useful?

## Additional resources
- [Kotlin docs: basic syntax](https://kotlinlang.org/docs/basic-syntax.html)
- [Kotlin Koans / Kotlin Playground](https://play.kotlinlang.org/)

Previous: [Set up](../00-start-here/02-set-up-environment.md) · Next: [Control flow and null safety](02-control-flow-null-safety.md)
