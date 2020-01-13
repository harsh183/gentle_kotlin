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
```

However, it's always good practice to write out argument and return types for lambdas so that your code is more readable!

### Why Lambas

Lambda functions are technically `anonymous functions` since they don't follow typical naming conventions.  They're really convenient because they allow you to write essential code logic without formally declaring them and adding unnecessary lines of code to your project.  They can act as sort of "throw-away functions," meaning that once you're outside of its scope, you never have to look back.

While the syntax is a bit different from typical first-order functions as you've seen up until now, a little bit of practice can lead to feeling more comfortable writing and using them.  They are especially handy in functional programming!

## Higher-Order Functions

### What are Higher-Order Functions?

### Syntax

### Why they're useful

## Links

[Kotlin Lambdas - GeeksForGeeks](https://www.geeksforgeeks.org/kotlin-lambdas-expressions-and-anonymous-functions/)
[Kotlin Higher-Order Functions - GeeksForGeeks](https://www.geeksforgeeks.org/kotlin-higher-order-functions/)
[Why Lambdas - StackOverflow](https://stackoverflow.com/questions/16501/what-is-a-lambda-function)
