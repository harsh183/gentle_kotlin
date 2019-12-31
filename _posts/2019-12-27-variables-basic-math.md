---
layout:  post
title:  Variables, Values, and Basic Math
---

# Variables

A variable is a way to store data or information when we code; what we store can be of numerous types.  Let's look at the following example:

```kotlin
var a: Int = 1
var b = 6 
var c = 3.14
var d: Int
d = 9
```

In the first line, we made a variable (denoted as 'var') and stored the value 1 in it.  Its type is declared as an Int, or integer, meaning that it can be any positive or negative whole number, as well as 0.  So, variables have a type, a name, and (usually) a value.

In the second line, we initialized a variable 'b' with value 6; even though the type wasn't explicitly declared, the Kotlin compiler implicitly identifies 'b' as an Int.  It isn't required to declare the type of a variable.

'c' stores a double, a fractional number represented with decimal places.  While 6 was an Int, 3.14 and 6.0 are doubles since they require a decimal point.

Variable 'd' needs an explicit type since we didn't set its value when declaring it; we initialize it in the next line by giving it a value of 6.

# Values

Values are immutable variables, or variables that can't be changed over time.  While normal variables can be changed and reset, values are protected after being initialized and can't be reassigned.

A real-life example would be pi:  by definition pi is a constant, and we can use it for numerous calculations, such as the diameter of a circle.

```kotlin
val PI = 3.14
```

Using Kotlin vals is good coding practice and can lead to more readable code. 

<!--- might add more later -->

# Types of Variables and Values

The official Kotlin site has a great [description](https://kotlinlang.org/docs/reference/basic-types.html) of the different primitive types used in Kotlin.  The types most commonly used among coders are Ints, Doubles, and Booleans, and Strings.

```kotlin
val foo: Int = 100
val dummy: Double = 72.56
var isCorrect = true
var myName = "Bill Gates"
```

'foo' is an immutable Int set to the value of 100; Ints are typically used for storing whole numbers.

'dummy' is an immutable Double set to a mixed decimal value of 72.56; as you can infer, Doubles are typically used for fractional and decimal values.

'isCorrect' is a Boolean, a type that only has two possible values:  true or false.  Booleans come in handy more often than one might think; for example, say your program grades students' exams and you want to know whether a student's answer to a question was correct.  You might store the answer to that question in a Boolean!

Lastly, the variable 'myName' is a String.  A String in Kotlin is simply text; conventionally, we call a String literal a "string" of text surrounded in quotes.  So, 'myName' is a String that stores the String literal "Bill Gates." 

# Math Operators

Kotlin supports the standard set of arithmetic operators, such as addition, subtraction, multiplication, and division!  Here's some examples:

```kotlin
val foo1: Int = 7
val foo2: Int = 11
val pos: Int = foo1 + foo2
println(pos) // prints 18
val neg: Int = foo1 - foo2
println(neg) // prints -4
val rem: Int = 12 % 2
println(rem) // prints 0
val div: Int = 12 / 5
println(div) // prints 2
```

The '%' symbol on line 7 is called the modulus operator.  When given the statement a % b, the modulus operator returns the remainder of a divided by b.  Hence, the Kotlin val 'rem' stores 0 since the remainder from 12 / 2 is 0.

# Links

[Kotlin's Primitive Types](https://kotlinlang.org/docs/reference/basic-types.html)
