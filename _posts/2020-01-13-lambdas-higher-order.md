---
layout: post
title: Lambdas and Higher Order Functions 
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
  val andOperator: (Boolean, Boolean) -> Boolean = { a, b -> a && b }
  val first = true
  val second = false
  println(andOperator(first, second)) // prints false
}
```

So lambda functions typically have this format:  `val lambda_name: (Arg Types) -> Return Type = { Args -> code_body }`.

We don't always need to list out types.  The Kotlin compiler assumes types when it's not given any explicit ones, so we can omit them if they're not necessary.

```kotlin
fun main() {
  val basicSum = { a: Int, b: Int -> a + b }
  println(basicSum(6, 9)) // prints 15
} 
```

However, it's always good practice to write out argument and return types for lambdas so that your code is more readable!

#### The `it` keyword

In Kotlin, we can use `it` as the implicit name of a single parameter in a lambda function.  Let's think about the notion in this way:  if we pass something to a function, what do we want the function to do with `it`?  The `it` keyword also allows us to omit the `->` operator, but this is all better explained with an example:

```kotlin
fun main() {
  val v1: (Int) -> Boolean = { x -> x > 0 }
  val v2: (Int) -> Boolean  = { it > 0 }
  println(v1(5)) // prints true
  println(v2(5)) // prints true
}
```

As you can see, we didn't explicitly state how many arguments are passed into the lambda `v2`; instead, using `it` allows the Kotlin compiler to assume that only one argument is passed into the function.

### Why Lambas

Lambdas are really convenient because they allow you to write essential code logic without formally declaring them and adding unnecessary lines of code to your project.  They can act as sort of "throw-away functions," meaning that once you're outside of its scope, you never have to look back.

While the syntax is a bit different from typical first-class functions as you've seen up until now, a little bit of practice can lead to feeling more comfortable writing and using them.  They are especially handy in functional programming!

## Higher-Order Functions

### What are Higher-Order Functions?

A higher-order function is one that can take a function as an argument and/or return a function.  We can pass in and/or return lambdas, as well as other Kotlin `first-class` functions by explicitly stating the type.  Let's look at an example.

### Built-In Functions

Kotlin provides some really useful higher-order functions, like `map` and `filter`.  These functions allow us to evaluate collections in one single line of code without writing an entire `foreach` loop!

#### `filter`

```kotlin
fun main() {
  var numList = listOf(1, 2, 3, 4, 5)
  println(numList.filter { it > 3 } ) // prints [4, 5]
```

The `filter` function returns every value in the list that satisfies the boolean condition passed in.  In this case, `filter` only considers values greater than 3, so it returns a list containing 4 and 5.  `filter` is really useful because it allows us to access every element in a list without any modification, and does so in one line of code.

#### `map`

```kotlin
fun main() {
  var numList = listOf(1, 2, 3, 4, 5)
  println(numList.map { it * 3 } ) // prints [3, 6, 9, 12, 15]
```

`map` returns a list of the output values from the original list based on the code body passed into the lambda.  In our case, we multiplied every value in the list by 3 and built a new list from these new values.  `map`, like filter, is really useful in that it doesn't modify the original list and does what a for loop would do in one line of code.

#### `fold`

```kotlin
fun main() {
  val numList = listOf(1, 2, 3, 4, 5)
  println(numList.fold(10) { max, item -> if (item > max) item else max }) // prints 10
}
```

The syntax for `fold` requires a bit more explanation.  It takes a single argument, and in this situation, we use it as a default value.  Typically, `fold` is used as an accumulator; for example, we can take fold, iterate it through a list, and have it accumulate every value into a sum.  In this bit of code, however, we store a current maximum value in it as we iterate through the list.  `fold` compares 10 to the current max in the list and stores whichever value is bigger at every comparison.  Since 10 beats every element in our list, it will return 10 as the default value.  If we want to find the maximum value without using a default, we can call `reduce`.

```kotlin
fun main() {
  val numList = listOf(1, 2, 3, 4, 5)
  println(numList.reduce() { max, item -> if (item > max) item else max }) // prints 10
}
```

### Writing Our Own Functions

```kotlin
var lambdaFunc: () -> Unit = { println("Hello Kotlin") }
fun highOrdFunc( lambda: () -> Unit ) {
  lambda()
}

fun main() {
  highOrdFunc(lambdaFunc)
} 
```
Let's review this code.  The first line defines a lambda function, which we call in the `main` method.  The second function we declared is a higher-order function, and we know this not just because of the obvious naming, but we can see that the function takes in a lambda.  Remember, first-order functions take in only variables.

In the higher-order function we run the lambda.  Then, in the `main` method, we call `highOrdFunc`, which calls `lambdaFunc`, which prints out "Hello Kotlin!" to the console.

### Why Higher-Order Functions

Higher-order functions are most popular with functional programming.  They allow for cleaner, crisper code and provide a succint way to utilize functions and work with really big data structures!  With these functions we can abstract our logic even further to be more widely applicable; this is especially important for building large models and structures with code. 

## Links

[Kotlin Lambdas - GeeksForGeeks](https://www.geeksforgeeks.org/kotlin-lambdas-expressions-and-anonymous-functions/)

[Kotlin Higher-Order Functions - GeeksForGeeks](https://www.geeksforgeeks.org/kotlin-higher-order-functions/)

[Why Lambdas - StackOverflow](https://stackoverflow.com/questions/16501/what-is-a-lambda-function)
