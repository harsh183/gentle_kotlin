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
var d = "hey there"
var e: Int
e = 9
```

In the first line, we made a variable (denoted as 'var') and stored the value 1 in it.  Its type is declared as an Int, or integer, meaning that it can be any positive or negative whole number, as well as 0.  So, variables have a type, a name, and (usually) a value.

In the second line, we initialized a variable 'b' with value 6; even though the type wasn't explicitly declared, the Kotlin compiler implicitly identifies 'b' as an Int.  It isn't required to declare the type of a variable.

'c' stores a double, a fractional number represented with decimal places.  While 6 was an Int, 3.14 and 6.0 are doubles since they require a decimal point.

Variable, 'd', stores a string, which is quite literally text surrounded in quotes.  As you can see, variables can store many representations of data.  We can create a var named 'mean' that stores the mean of a data set we're using, or it can store the email addresses of people using an application. 

Variable 'e' needs a type since we didn't set its value when declaring it; we initialize it in the next line by giving it a value of 6.

# Values

Values are immutable variables, or variables that can't be changed over time.  While normal variables can be changed and reset, values are protected after being initialized and can't be reassigned.

A real-life example would be pi:  by definition pi is a constant, and we can use it for numerous calculations, such as the diameter of a circle.

```kotlin
val PI = 3.14
```

Using Kotlin vals is good coding practice and can lead to more readable code. 

<!--- might add more later -->

# Types of Variables and Values

The official Kotlin site has a great [description](https://kotlinlang.org/docs/reference/basic-types.html) of the different primitive types used in Kotlin.  The types most commonly used among coders are Ints, Doubles, and Booleans.

# Math Operators


