---
layout: post
title: "Console input output"
---

The fundamental difference between all the machines that came before computers
is because of interactivity. Basically every single computer program you will
ever deal with is some format of `input`-`process`-`output`.

Here I will show you the most simple ways of dealing with input and output with just the console, but the general principles you can apply with pretty much any  other formats (websites, apps, bots etc.)

## Printing

Remeber how we started with saying hello to the world in our first program. 
Likewise, we can use `println()` to show `String`s on the console screen.

`println()` is a short way of saying print whatever inside the brackets on a line.

```kotlin
fun main() {
    println("Hello Kotlin")
}
```

Likewise, we have another function called `print()` which does the same thing but
it does not go to a new line. This is also useful in many cases like when dealing
with users entering information etc. 

Try writing out this example below to get an idea of the difference between both. 
```kotlin
fun main() {
    println("Line 1")
    print("Line 2")
    print(" - Still on Line 2")
    println(" - Still on Line 2 but the next one is on Line 3")
    print("Line 3 now")
}
```

### Newlines and other special characters

The difference between both are quite simple `println()` just adds one more piece of information called a special character called the new line character `\n`. 

Special characters are invisible characters that convey special information like 'go to the next line', 'indent with a tab', 'play a bell sound' and you will encounter more as you go along. 

Let's test out our newline `\n` in action. 

```kotlin
fun main() {
    println("Line 1")
    print("Line 2 and see how it ends here despite being print \n")
    print("Let's skip three lines \n\n\n and now lets skip another \n")
}
```    


### Printing variables

Okay that's great, but what if we want to greet a particular person and have it change dynamically based on what their name is set as. 

```kotlin
fun main() {
    val name: String = "Harsh Deep"
    println("Hello $name, nice to meet you!")
}
```

All we have to do put `$` before the variable name inside the print statement and it works 
like how we did `$name` above. 

This works just as well with all sorts of different data types. 

```kotlin
fun main() {
    val city: String = "Bangalore"
    val birthYear: Int = 2000 
    val age: Double = 19.25
    print("I see you come from $city,")
    println("and since you are born in $birthYear your age is $age")
}
```

## Input

Note: If you are following this on an online IDE, the Kotlin Playground does not support proper user input but this section works on [JDoodle](https://www.jdoodle.com/compile-kotlin-online/)

This is when we start getting in true interactivity. Let's have a user enter their name and then we greet them with it.

### With Strings

```kotlin
fun main() {
    println("What is your name?")
    val name: String = readLine()!!
    println("Hello $name")
}
```

`readLine()` is like the opposite of `println()` where it takes an entire line of user input from them. So it reads everything in that line after the user hits enter. Try running this program a few times with different values so you get an idea of how it changes with different names you enter. 

Another interesting thing we see here is the double exclaimation mark `!!`. It looks like Kotlin is screaming at you quite loudly in fact. And rightly so, `!!` indicates that this function might be empty and that can cause an error and so we have the program stop and display the error to us then. 

More technically, many programming languages have a concept called `null`, which is how computers say 'nothing'. Our program here can't really work if someone's name turns out to be empty so this makes sure that does not happoen.

In later posts, I'll show better and safer ways of dealing with `null` which Kotlin is quite well known for avoiding many of the common pitfalls with dealing with null. <!-- Should we link the million dollar mistake -->  

### With non strings

At the end of the day, anything a user enters on the console is a `String`, so if we want users to enter in numbers like `Int` or `Float` what we do is that we first use `readLine()!!` to collect the `String` and then use converter methods to make it into the number types that we like.

It's quite often that you get strings from various types of inputs so knowing this basic conversions can get you quite far. 

They're fairly easy to remember `toInt()` to convert something to an `Int` and `toDouble()` to convert something to a `Double`

```kotlin
fun main() {
   val whole: String = "42"
   val decimal: String = "4.2"

   val wholeInt: Int = whole.toInt()
   val wholeDouble: Double = whole.toDouble()

   println("$whole as Int is $wholeInt and as Double is $wholeDouble")
   
   val decimalDouble: Double = decimalNumber.toDouble()

   println("$decimal as Int is $decimalInt and as Double is $decimalDouble")
}
```

We can't use `toInt()` for `decimal` because it will lose out on that data during conversion and give us an error. 

Now if we combine this with the `readLine()!!` from earlier, this can be a really effective one liner to enter in `Int` and `Double`.

```kotlin
fun main() {
    println("Welcome to made up example tax calulator")
    println("Enter your salary rounded to the nearest number")
    val salary: Int = readLine()!!.toInt()

    println("Enter the tax rate from 0.0 to 1.0")
    val taxRate: Double = readLine()!!.toDouble()

    val tax: Double = salary * taxRate
    println("Your taxes this year are $tax")
} 
```

Oh if only taxes were this simple. 




