---
layout:  post
title:  Hello World
---

Let's start with a fun and popular introductory programming example:  printing Hello world! to the console.  To do so in Kotlin, we use the `println()` function.  It takes any text in quotes and prints it to the console. 

```kotlin
println("Hello world!")
```

We need to write this programming statement inside of a main function:

```kotlin
fun main() {
	println("Hello world!")
}
```

The main function is an entry point for every program; it takes any code that you've written as a set of instructions and executes it line by line. In this case, we told the main function to print out "Hello world!" on the first line and then it exited the program.

Add that bit of code in an empty .kt file, then compile and run!  You should see 'Hello world!' displayed on the console. If you're doing it on an online playground just type this and run. 

Pretty much all your code will always go inside the `main()` setup and will often not be mentioned but it is always required. Later as you learn more syntax you can explore splitting code between other functions and classes.

## See more

* [The History of 'Hello World](https://blog.hackerrank.com/the-history-of-hello-world/)
