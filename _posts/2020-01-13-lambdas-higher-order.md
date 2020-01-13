---
layout: post
title: Lambdas and Inline Functions
---

## Lambda Functions

### What are Lambda Functions?

Lambdas are an interesting way to write and declare functions; we've seen them written formally up to this point, involving the `fun` keyword and explicit types.  Lambda functions are functions that aren't declared but passed immediately as an expression.

### Syntax

```kotlin
fun main() {
  val firstLambda = { println("This is a lambda expression!") }
  firstLambda() // prints out "This is a lambda expression!")
}
```

Let's look at `firstLambda`:  it doesn't take any arguments or return anything, so it's equivalent to a void function.  What happens when we want to write something that takes arguments or returns them?  Here's how:

```kotlin
fun main() {
  val andOperator: (Boolean, Boolean) -> Boolean = { a: Boolean, b: Boolean -> a && b }
  val first = true
  val second = false
  println(andOperator(first, second)) // prints false
}
```

So lambda functions typically have this format:  `val lambda_name: (Arg Types) -> Return Type = { Args -> code_body }`.

We don't always need to list out types.  The Kotlin compiler assumes types when it's not given types, so we can omit them if they're not necessary.

```kotlin
fun main() {
  val basicSum = { a: Int, b: Int -> a + b }
  println(basicSum(6, 9)) // prints 15
} 

However, it's always good practice to write out types for readability!

### Why Lambas



## Higher-Order Functions

### What are Higher-Order Functions?

### Syntax

### Why they're useful

## Links
