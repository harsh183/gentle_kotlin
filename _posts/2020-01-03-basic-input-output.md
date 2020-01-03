---
layout: post
title: "Basic input output"
---

The fundamental difference between all the machines that came before computers
is because of interactivity. Basically every single computer program you will
ever deal with is some format of `input`-`process`-`output`.

Here I will show you the most simple ways of dealing with input and output with
just the console, but the general principles you can apply with pretty much any 
other formats (websites, apps, bots etc.)

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

```
fun main() {
    println("What is your name?")
    val name = readLine()
    println("Hello $name")
}
```
`readLine()` is like the opposite of `println()` where it takes an entire line of user input from them. So it reads everything in that line after the user hits enter. Try running this program a few times with different values so you get an idea of how it changes with different names you enter. 

```kotlin
fun main() {
    println("What is your first name?")
    val firstName: String? = readLine()
    
    println("What is your last name?")
    val lastName: String = readLine()!!

    println("Welcome, $firstName $lastName!")
}
`
More confusing is the `?` and `!!`, both the lines for getting the first name and last name are pretty much identical other than that. If you try writing the

