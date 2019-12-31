---
layout:  post
title:  Variables, Values, and Basic Math
---

# Variables

A variable is a way to store data or information in our code; what we store can be of numerous types.  Let's look at the following example:

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

Values are immutable variables, or variables that can't be changed over time.  While normal variables can be changed and reset, values can't be reassigned after initialization.

A real-life example would be pi:  by definition pi is a constant, and we can use it for numerous calculations, such as the diameter of a circle.

```kotlin
val PI = 3.14
```

Using Kotlin vals is good coding practice and can lead to more readable code.  We can use immutable variables for values that we know won't change throughout the lifetime of a program.  As such, this optimizes the computer since it doesn't have to account for reassignments.  We want our code to make sense to us, too; while declaring PI as a Kotlin variable is acceptable, it is more appropriate to store it in a val so that it functions solely as a constant.  We can also test our own code with a lot more accuracy since Kotlin vals ensure less of a gray area with what happens in our own program.

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

## Variable Naming

### Why it's Important

The variables from the examples throughout this post are named fairly poorly; as you will learn throughout your coding experiences, the names given to variables are often neglected.  If you're reading someone's Kotlin project and every variable is just the next letter in the alphabet, how easy would it be to explain every line of their code?  Here's an example:

```kotlin
var x: Double = 1.10
var y: Double = 50.00
var z: Double = x * y
```

What do vars x, y, and z represent?  You can make some inferences if you're given more context and the application of these lines of code, but it's much easier to have your code look like this:

```kotlin
var salesTax: Double = 1.10
var retailPrice: Double = 50.00
var totalDue: Double = x * y
```

Now the person reading this code can say that the program was written for a sales clerk who wants to calculate the final price after sales tax.  While this example may be simple, imagine having to decipher 700-1000 lines of code, for which all of the variables were named 1, 2, 3, etc. Yeah.

## Naming Conventions

Java programmers use what is known as the "camel case" standard:  the first word in the variable name is lower case, while the first letter of every word following is capitalized.  In the example above, we had a variable that stored the sales tax multiplier, so we called the variable salesTax (we also could have named the variable salesTaxMultiplier, but it's a little long).  Try to keep the camel case standard throughout your programs; remember, you want your code to be as clean and consistent as possible!

# Math Operators

Kotlin supports the standard set of arithmetic operators, such as addition, subtraction, multiplication, and division!  Here's some examples:

```kotlin
val foo1: Int = 7
val foo2: Int = 11
val pos: Int = foo1 + foo2
println(pos) // prints 18
val neg: Int = foo1 - foo2
println(neg) // prints -4
val mult = 2 * 4
println(val) // prints 8
val rem: Int = 12 % 2
println(rem) // prints 0
val div: Int = 12 / 5
println(div) // prints 2
```

The '%' symbol on line 7 is called the modulus operator.  When given the statement a % b, the modulus operator returns the remainder of a divided by b.  Hence, the Kotlin val 'rem' stores 0 since the remainder from 12 / 2 is 0.

# Links

[Kotlin's Primitive Types](https://kotlinlang.org/docs/reference/basic-types.html)
