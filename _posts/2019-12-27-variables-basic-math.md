---
layout:  post
title:  Variables, Values, and Basic Math
---

# Introduction to Variables

A variable is a way to store data or information in our code, and what we store can be of numerous types.  Let's look at a simple example:

```kotlin
var firstExample: Int = 1
```

In the first line, we made a variable (denoted as 'var'), gave it the name 'firstExample', and stored the value 1.  Its type is also declared as an Int, short for integer.  So variables have a type, a name, and (usually) a value.  Let's delve into some basic primitive types in Kotlin.

## Types of Variables

The official Kotlin site has a great [description](https://kotlinlang.org/docs/reference/basic-types.html) of all the primitive types used in Kotlin; the ones most commonly used are Ints, Doubles, and Booleans, and Strings.

```kotlin
var foo: Int = 100
var basicInt = 6
var dummy: Double = 72.56
var isCorrect: Boolean = true
var myName: String = "Bill Gates"
```

'foo' is an Int set to the value of 100; Ints are typically used for storing whole numbers.  While 'basicInt' doesn't have an explicit type, the Kotlin compiler knows that it is of type Int since we assigned an integer value to it.  Even though types aren't required, it's good practice to always list a type when declaring a variable, as it leads to more readable code.

'dummy' is a Double set to a mixed decimal value of 72.56; as you can infer, Doubles are typically used for fractional and decimal values.

'isCorrect' is a Boolean, a type that only has two possible values:  true or false.  Booleans come in handy more often than one might think; for example, say you built a program that grades students' exams and you want to know whether a student's answer to a question was correct.  You might store this property in a series of Boolean variables for every question, with `true` being that the student answered correctly, and `false` being that they didn't.

Lastly, the variable 'myName' is a String.  A String in Kotlin is simply text; conventionally, we call a String literal a "string" of text surrounded in quotes.  So, 'myName' is a String that stores the String literal "Bill Gates."

### When Types are Required

```kotlin
var thirdExample: Int
thirdExample = 9
```

If we don't store a value in a variable when declaring it, the compiler forces us to list an explicit type.  For the variable 'thirdExample', we initialize its value in the next line by giving it a value of 9.

## Variable Naming

### Why it's Important

```kotlin
var x: Double = 1.10
var y: Double = 50.00
var z: Double = x * y
```

As you will learn throughout your coding experiences, the names given to variables are often neglected.  If you're reading through someone's code and every variable is named with letters from the alphabet, imagine how difficult it would it be to explain every line of their code.  In this example, what do vars x, y, and z represent?  You can make some inferences if you're given more context and the application of these lines of code, but it's much easier to have your code look like this:

```kotlin
var salesTax: Double = 1.10
var retailPrice: Double = 50.00
var totalDue: Double = salesTax * retailPrice
```

Now the person reading this code can say that the program could have been written for a sales clerk who wants to calculate the paid amount due for every customer.  While this example may be simple, having to decipher, say, 700-1000 lines of code, throughout which all of the variables were named 1, 2, 3, etc. would be outrageously frustrating!

### namingConventions

There are two main rules to variable naming:  1) Variables are named after what they do, and 2) naming follows the camel case rule.

With the "camel case" standard, the first word in the variable name is lower case, while the first letter of every word following is capitalized.  In the example above, we had a variable that stored the sales tax multiplier, so we called the variable salesTax (there are numerous possibilities for the name, but it's up to the programmer and her/his style choice).  Make sure to keep the camel case standard throughout your programs; remember, you want your code to be as clean and consistent as possible!

If you want more details on the camel case rules, check out [Geeks for Geeks](https://www.geeksforgeeks.org/java-naming-conventions/).  There is a lot of information in that particular article that may not be relevant for you yet, but it delves into some good examples with variable naming.

# Values

Values are immutable variables, or variables that can't be changed over time.  While normal variables can be changed and reset, values can't be reassigned after initialization.

A real-life example would be pi:  by definition, pi is a constant, and we can use it for numerous calculations, such as the diameter of a circle.

```kotlin
val pi = 3.14
```

Using Kotlin vals is good coding practice and can lead to more readable code.  We can use immutable variables for values that we know won't change throughout the lifetime of a program.  As such, this optimizes the computer since it doesn't have to account for reassignments.

We want our code to make sense to us, too; while declaring PI as a Kotlin variable is acceptable, it is more appropriate to store it in a val so that it functions solely as a constant.  We can also test our own code with a lot more accuracy since Kotlin vals ensure less of a gray area within in our own program.

<!--- might add more later -->

# Math Operators

Kotlin supports the standard set of arithmetic operators, such as addition, subtraction, multiplication, and division for any of its **numeric** types (such as Ints, Doubles, Floats, etc.):

```kotlin
1: val foo1: Int = 7
2: val foo2: Int = 11
3: val positiveNum: Int = foo1 + foo2
4: println(positiveNum) // prints 18
5: val negativeNum: Int = foo1 - foo2
6: println(negativeNum) // prints -4
7: val product = 2 * 4
8: println(product) // prints 8
9: val remainder: Int = 12 % 2
10: println(remainder) // prints 0
11: val quotient: Int = 12 / 5
12: println(quotient) // prints 2
```

While most of the operators should be familiar to you, the one on line 9 may not! The '%' symbol is called the modulus operator.  The statement a % b returns the remainder of a divided by b.  Hence, the val we declared called 'remainder' stores 0 since the remainder of 12 / 2 is 0.

# Links

[Kotlin's Primitive Types](https://kotlinlang.org/docs/reference/basic-types.html)

[Java's Naming Conventions](https://www.geeksforgeeks.org/java-naming-conventions/)
