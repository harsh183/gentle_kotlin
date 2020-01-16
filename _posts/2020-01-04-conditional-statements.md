---
layout: post
title: Conditional Statements - if and when
---

So far the programs we have written all turn out pretty much the same. So no matter what the input we got the same output. 

## If

```kotlin
val tax: Int = 0
val income = 1000

if (income > 500) {
    tax = income * 0.1
    println("10% tax")
} else { // optional
    println("No tax")
}

// or shorthand for just assignment only
val quickTax = if (income > 500) income * 0.1 else 0
```

Note as a block `else` is optional but when it's being used as an expression (ex. the `quickTax` assignment above) then `else` has to be there.

<!-- TODO: Ranges, Boolean Expression --> 

## When  

For when there are more than two branches possible. This has some very powerful syntax better than C-like languages like `switch`

```kotlin
val age: Int = 19 

val undergradAges: Array<Int> = arrayOf(18, 19, 20, 21, 22)
when (age) {
    1 -> print("home")
    2 -> print("day care")
    3, 4, 5 -> print("pre-school")
    in 6..17 -> print("school") // ranges
    in undergradAges -> print("undergrad") // collections
    else -> print("Invalid age")
}
```
<!-- TODO: Collections -->
 
It works with single values, several values collected, ranges and collections as well as many more complex matchers. 

