---
layout: post
title: Conditional Statements - if and when
---

<img src="/assets/img/conditional_statements.png" width="500">

So far the programs we have written all turn out pretty much the same. So no matter what the input we got the same output. 

## If

```kotlin
val score = 94.03
var grade = ""
if (score > 90) {
    grade = "A"
} else if (score > 80) {
    grade = "B"
} else {
    grade = "C"
}
println(grade) // => A
```

Or the shorthand that fits on a line for just assignment.

```kotlin
// or shorthand for just assignment
val score = 78.46
val quickGrade = if (score > 90) "A" else if (score > 80) "B" else "C"
println(quickGrade)
```

Note as a block `else` is optional but when it's being used as an expression (ex. the `quickGrade` assignment above) then `else` has to be there.

## Collections and Ranges

With collections we can use `in` to check if something exists and `!in` to see if it does not. In the case of maps by default it checks the keys and if you want to check with values use `in mapName.values`

```kotlin
val jvmLanguages = listOf("Java", "Kotlin", "Scala", "Clojure")
if ("Ruby" in jvmLanguages) {
    println("Ruby is a JVM language")
}
val favLang = mapOf("Harsh" to "Ruby", "Varshini" to "Kotlin", "Vinayak" to "JavaScript")
if ("Astha" !in favLang) {
    println("Astha has not decided what her favorite language is.")
}
if ("Java" !in favLang.values) {
    println("No one likes Java :(")
}
```

We can do the same thing with ranges as well.

```kotlin
val myAge = 20
if (myAge !in 13..19) {
    println("I am no longer a teenager")
}
```

## When  

We use `when` for dealing with more than 2 branches. This has some very powerful syntax that improves from C-like languages with the `switch case` syntax.

```kotlin
val age: Int = 19 

val undergradAges = arrayOf(18, 19, 20, 21, 22, 23, 24)
when (age) {
    1 -> print("home")
    2 -> print("day care")
    3, 4, 5 -> print("pre-school")
    in 6..17 -> print("school") // ranges
    in undergradAges -> print("undergrad") // collections
    else -> print("Invalid age")
}
```
 
It works with single values, several values collected, ranges and collections as well as many more complex matchers. 

## See More

* [Conditionals - CS199 IKP](https://kotlin.cs.illinois.edu/lessons/conditionals/)

* [Control Flow: if, when, for, while - Official docs](https://kotlinlang.org/docs/reference/control-flow.html)

* [Guide to the “when{}” Block in Kotlin - Baeldung](https://www.baeldung.com/kotlin-when)

* [If-Else Expression in Kotlin - Baeldung](https://www.baeldung.com/kotlin/if-else-expression)