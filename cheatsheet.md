---
layout: page
title: Cheetsheet/Reference
sidebar_link: true
---

What's important is not having each and every bit of syntax memorized, so feel free to use this a lot, print it out, bookmark it etc. It's also a good idea to inspire from this and/or make your own as a reference.

## Hello World

```kotlin
fun main() {
    println("Hello, World!") 
}
```

The most basic program. Every program starts executing from `main()`.

## Variables 
```
var <name_of_variable>: <Type> = <value>
```

```kotlin
var x: Int = 25
var displayNext: String = "Hello World"
var isSorted: Boolean = false;
var temperature = 24.32 // If you don't mention one it guesses
```

These are when you want to store data that you will expect changes more than *once*. Most if the time this does not happen so we use  *values*

## Values

```
val <name_of_variable>: <Type> = <value>
```

```kotlin
val name: String = "Harsh Deep"
val PI: Double = 3.14 // constants are conventionally upper case
val radius: Int = 10
val area = PI * radius // the guesses are fairly smart
```

When you want to store something that will not change more than once. If it does use `var`.

## Types

There are many different built in types for Data in Kotlin. The most important ones are 

* `Int` - whole numbers `0`, `324123`, `42`, `-43`, `4234234`

* `Double` - numbers with decimal/fractional parts allowed `0`, `42.125`, `-4236.3`, `-0.11233332`

* `String` - any type of text - "Random text", "Insurance rates go up 8%", "42.0", "25"

* `Boolean` - can be either `true` or `false`. Useful in control flow like `if`, `when`, `for`, `while` etc.

### Converting

Generally it's `to<Type>()` like `toInt()`, `toDouble()`, `toInt()`

```kotlin
val x: Int = "42".toInt()
var y: Double = "21.5".toDouble()
val z: String = 32.toString()
```

## Basic math

Most standard operations work with numeric types like `Int` and `Double`

```kotlin
val x: Int = 10
val y: Int = 3

val added = x + y                   // => 13
val subtracted = x - y              // => 7
val multiplied = x * y              // => 30

val integer_divided = x / y         // => 3
val normal_divided = x.toDouble()/y // => 3.3333333333333335
val remainder = x % y               // => 1
```

Note that if we want normal division over integer division we have to convert one of them to a `Double` or some decimal type.

## Printing - console output

```kotlin
println("This prints out a whole line and to the next")
print("This only prints what's inside")

val name: String = "Harsh"
val age: Int = 19
val eyePower: Double = 0.103

// To print variables
println("$name is $age years old with power $eyePower")
```

Basically use `print()` to display, `println()` to print with a new line and `$<variable name>` inside to print out values

## Console input

```kotlin
val name: String = readLine()!!
val age: Int = readLine()!!.toInt()
val eyePower: Double = readLine()!!.toDouble()

// If you know what you are doing
val simple = readLine()
```

`readLine()!!` gives us a line of input as a `String`, the `!!` is to handle the case of `null` input.

## If

```
if (<boolean condition>) {
    <code for when things are true>
} else { // optional 
    <code for when things are false>
}
```

```kotlin
val tax: Int = 0
val income = 1000

if (income > 500) {
    tax = income * 0.1
    println("10% tax")
} else {
    println("No tax")
}

// or shorthand for just assignment only
val quickTax = if (income > 500) income * 0.1 else 0
```

Note as a block `else` is optional but when it's being used as an expression (ex. the `quickTax` assignment above) then `else` has to be there.

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

It works with single values, several values collected, ranges and collections as well as many more complex matchers. 

## While

## For 

## Functions 

## Inline functions

## Lambdas

## Classes and Objects

## Data Classes

## Inheritance

## Generics

## Null safety

## Basic testing

## Coroutines
