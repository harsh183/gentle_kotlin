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
```

In the first line, we made a variable (denoted as 'var') and stored the value 1 in it.  Its type is declared as an Int, or integer, meaning that it can be any positive or negative whole number, as well as 0.  So, variables have a type, a name, and (usually) a value.

In the second line, we didn't specify the type as Int; it was implicitly identified as an Int since the value we stored in 'b' is 6, which fits the bill as an Int.

'c' stores a double, a number with two decimal places.  While 6 was an Int, 3.14 and 6.00 are doubles simply because they specify two places after the decimal.

The last variable, 'd', stores a string, which is quite literally text surrounded in quotes.  As you can see, variables can store many representations of data.  We can create a var named 'mean' that stores the mean of a data set we're using, or it can store the email addresses of people using an application. 

# Values

Values are essentially constants; they're variables that can't be modified or reset after being initialized (declared for the first time).

A real-life example would be pi:  its value will never change, and we can use it for numerous calculations, such as the diameter of a circle.

```kotlin
val PI = 3.14
```

# Math Operators
