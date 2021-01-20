---
layout: page
title: Cheatsheet
sidebar_link: true
---

<img src="/assets/img/cheatsheet.png" width="500">

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
var temperature = 24.32 // If you don't mention a type Kotlin can infer it
```

These are when you want to store data that you will expect changes more than *once*. 

Type inference is fairly smart so almost all the time you can not mention the type and it will figure it out so put it in place where it matters. 

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

Generally you'd want to use `val` as much as possible over `var`.

## Types

There are many different built in types for Data in Kotlin. The most important ones are 

* `Int` - whole numbers `0`, `324123`, `42`, `-43`, `4234234`

* `Double` - numbers with decimal/fractional parts allowed `0`, `42.125`, `-4236.3`, `-0.11233332`

* `String` - any type of text - "Random text", "Insurance rates go up 8%", "42.0", "25"

* `Boolean` - can be either `true` or `false`. Useful in control flow like `if`, `when`, `for`, `while` etc.

### Converting

Generally it's `to<Type>()` like `toInt()`, `toDouble()`, `toString()`

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

// String interpolation
println("$name is ${age} years old with power $eyePower")
```

Basically use `print()` to display, `println()` to print with a new line and string interpolation like`${<variable name>}` inside to print out values.

Most of the time if it's just a single variable name the `{}` are not requried and it's just `$<variable name>`

## If

```kotlin
val score = 94.03
var grade = ""
if (score > 90) {
    grade = "A"
} else if (score > 80) {
    grade = "B"
} else {
    grade = "C"
}

// or shorthand for just assignment only
val quickGrade = if (score > 90) "A" else if (score > 80) "B" else "C"
```

Note as a block `else` is optional but when it's being used as an expression (ex. the `quickGrade` assignment above) then `else` has to be there.

If can be also used well with collections

```kotlin
val jvmLanguages = listOf("Java", "Kotlin", "Scala", "Clojure")
if ("Ruby" in jvmLanguages) {
    println("Ruby is a JVM language")
}
val favLang = mapOf("Harsh" to "Ruby", "Varshini" to "Kotlin", "Vinayak" to "JavaScript")
if ("Astha" !in favLang) {
    println("Astha has not decided what her favorite language is.")
}
if ("Java" !in favLang.values) {
    println("No one likes Java :(")
}
```

as well as ranges

```kotlin
val myAge = 20
if (myAge !in 13..19) {
    println("I am no longer a teenager")
}
```

## When  

For when there are more than two branches possible. This has some very powerful syntax better than C-like languages like `switch`

```kotlin
val age: Int = 19 

val undergradAges: Array<Int> = arrayOf(18, 19, 20, 21, 22, 23, 24)
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

## Repeat

```kotlin
repeat(3) { print("Loop $it") }
// => Loop 0 Loop 1 Loop 2
```

## While

```kotlin
var x = 0
while(x < 5) {
    print("$x ")
    x++
}
// => 0 1 2 3 4 
```

## For 

For looping over anything that is `Iterable` like ranges, collections etc. 
```kotlin
for (<variable name> in <iterable thing>) {
    // body will run for each with <variable name> changing each time
}
```

### Ranges

```kotlin
for (i in 0..5) print("$i ")
// => 0 1 2 3 4 5
for (i in 10 downto 1 step 2) print("$i ")
// => 10 8 6 4 2 
```

### Arrays

```kotlin
val undergrad: Array<Int> = arrayOf(18, 19, 20, 21, 22)
for (age in undergradAges) {
    print("$age ")
}
// => 18 19 20 21 22
```

### Lists

```kotlin
val cities = listOf("Bangalore", "London", "Champaign", "Urbana")
for (city in cities) {
    println("$city ")
}
=> Bangalore London Champaign Urbana
```

### Maps

Here it's slightly different because we can assign two variables, one for the key and the other for the value. Note the bracket around the variable part since we have more than one. 

```kotlin
val studentGrades = mapOf("Alice" to 96.7, 
                          "Greg" to 90.1, 
                          "Jessica" to 89.7)
for ( (name, score) in studentGrades) {
    println("$name got $score")
} 
```

```
Alice got 96.7
Greg got 90.1
Jessica got 89.7
```

## Functions 

A simple function with no parameters and no return

```kotlin
fun sayHello(): Unit {
    println("Hello!")
}
```

`Unit` indicated that there is no return, since it's optional we usually write it like
```kotlin
fun sayHello() {
    println("Hello")
}
```

### Parameters/Arguments

Seperated by commas like `functionName(name1: Type1, name2: Type2)`

```kotlin
fun sayHello(from: String, to: String) {
    println("$from says Hello to $to")
}
```

For variable number of arguments (Varargs) we use the `vararg` keyword 

```kotlin
fun printNumbers(vararg numbers: Int) {
    for (number in numbers) {
        print("$number ")
    }
    println()
}  

fun main() {
    printNumbers(1, 3, 5, 7, 9) // => 1 3 5 7 9
    printNumbers()              // => 
    printNumbers(2)             // => 2
}
```

### Return 

`return` brings the control back to the function that called it.

If you add a type then it gives back that value, like an output.

```kotlin
fun average(numbers: List<Double>): Double {
    var sum: Double = 0.0
    for (num in numbers) {
        sum += num
    }
    var average = sum / numbers.size

    return average
}
```

### Parameterized arguments and return

Also called `Generics` and `Parametric polymorphism`

For parameterized types we want to write general functions over writing the same one again and again. Also called parametric polymorphism. We use `<T>` that denotes any generic type.

```kotlin
fun <T> getFirst(list: List<T>): T {
    return list[0]
}

...
getFirst(listOf(1, 2, 3)) => 1
getFirst(listOf("Kotlin", "Java", "Scala") => Kotlin
```

## Lambdas

```kotlin
val function_name : Type = { arguments -> code body }
```

Lambdas are like functions which can be assigned to variables, passed around functions and returned. It basically has a type `(<list of types>) -><return type>`

```kotlin
val sum: (Int, Int) -> Int = { x: Int, y: Int -> x + y }
```

Kotlin is quite smart with type inference so this can also be
```kotlin
val sum = {x, y -> x + y}
```

### Higher order functions

Lambdas can be used in higher order functions (functions that take in other functions as input)

```kotlin
val luckyNumbers = listOf(1, 2, 5, 25, 42)
luckyNumbers.map {it * it } // it is there if there is only one param
=> [1, 4, 25, 625, 1764]
luckyNumbers.filter {it % 2 == 0}
=> [2, 42]
luckyNumbers.fold(0) {acc, item -> acc + item} 
=> 75
```

Making one ourselves
```kotlin
fun nestedApply(input: Int, n: Int, fn: (Int) -> Int): Int {
    var result: Int = input
    for (i in 1..n) {
        result = fn(result)
    }
    return result
}
...
nestedApply(10, 2) {it * it} // f(f(x)) where f(x) = x*x
// => 10000
nestedApply(10, 5) {it + 1} // f(f(f(f(f(x))))) where f(x) = x + 1
// => 15
```

## Classes and Objects

Classes wrap `properties` and `behaviour`. We use the `class` keyword

```kotlin
class Hero(val name: String, val type: String, var healthPoints: Int = 120) {
    fun attacked(damage: Int) {
        healthPoints -= damage
        println("Oh no! $name got attacked with $damage with $healthPoints hp left")
    }

    fun healed(hp: Int) {
        healthPoints += hp
        println("Yay! $name got healed with $hp with $healthPoints hp now")
    }
    
    fun attack(anotherPlayer: Hero) {
        println("$name attacks ${anotherPlayer.name}")
        val damage = if (type == "Warrior") 50 else 30
        anotherPlayer.attacked(damage)
    }

    fun heal(anotherPlayer: Hero) {
        println("$name casts heal on ${anotherPlayer.name}")
        val hp = if (type == "Mage") 40 else 10
        anotherPlayer.healed(hp)
    }
}
```

`val` makes it read only, `var` means it will change. The variables can be accessed within the functions as is and other objects or outside the class you need the `.` dot notation. You also need the `.` notation to call functions outside the class.

To use objects of the class:

```kotlin
fun main() {
    val harsh: Hero = Hero("Harsh", "Mage", 100)
    val varshini = Hero("Varshini", "Warrior")
    varshini.attack(harsh)
    println()

    println("Ooops, let me heal you")
    varshini.heal(harsh)
    println()
    
    println("You aren't a mage so it wasn't that useful")
    println("I'll do it myself")
    harsh.heal(harsh)
}
```

### Data Classes

The `data` keyword before the class name sets up the standard utility functions (Plain Old Java Object) with ain class. 

```kotlin
data class Hero(val name: String, val type: String, var healthPoints: Int) {
    [...]
}
```

Lets us do: 

```kotlin
val hero1 = Hero("Harsh", "Mage", 100)
println(hero1) // get a nice print
// => Hero(name=Harsh, type=Mage, healthPoints=100)
println(hero1.healthPoints) // get values
// => 100
hero1.healthPoints = 80 // set values (var only)
println(hero1) 
// => Hero(name=Harsh, type=Mage, healthPoints=80)

// Check equality 
val hero2 = Hero("Varshini", "Warrior", 100)
println(hero1 == hero2) // => false
val hero3 = Hero("Harsh", "Mage", 80)
println(hero1 == hero3) // => true

// Destructure it
val (name, type, hp) = hero2
println(name) // => Varshini

// Copy
val mageVarshini = hero2.copy(type = "Mage")
println(mageVarshini)
```

## Inheritance

```kotlin
open class Person(val name: String,
                  var age: Int,) {
    open fun display() {
        println("Name: $name")
        println("Age: $age")
    }
}

class Student(name: String,
              age: Int,
              val mathScore: Double,
              val scienceScore: Double): Person(name, age) {
    override fun display() {
        super.display()
        println("Math Score: $mathScore")
        println("Science Score: $scienceScore")
    }
}

class Teacher(name: String,
              age: Int,
              var students: Collection<Student>): Person(name, age) {
    override fun display() {
        super.display()
        println("Number of students: ${students.size}")
    }
}
```

## Null types

One of the neatest things about Kotlin comes from it's `null` safe programming idioms. Unless you specifically allow Kotlin to, you will never encounter a `NullPointerException` as null checking becomes the compiler's job.

```kotlin
val name: String = null // this can't happen
var age = 19 // Inferred Int
age = null // this can't happen
```

For this we add `?` at the end of the variable type to say, this can be of the type or `null`. This applies to function parameters, variable names, returns, class instance variables.

```kotlin
val name: String? = null
var age: Int? = 19
age = null
```

Or here is an example with functions

```kotlin
fun getNameIfAgeLegal(name: String, age: Int): String? {
  if (age >= 18) {
    return name
  } else {
    return null
  }
}
val filteredName = getNameIfAgeLegal("Varshini", 20) // infer String?
println(filteredName) // => Varshini
```

## Null safe calling

Kotlin also provides idiomatic ways to deal with functions that may return `null`. You'll often see this kind of code when interfacing with Java or Android libraries especially.

To call a method on something that results in a nullable type (ending with `?`) instead of a normal method call `.` we use `?.` which acts normally when the data is not null and when the data is `null` it just returns `null` instead of trying to call a function on `null` and creating a null pointer exception. The Kotlin compiler will make sure things propogate through the chain.

```kotlin
data class Person(var name: String, var leftEye: Eye?, var rightEye: Eye?)
data class Eye(var power: Double)

val me = Person("Harsh", Eye(0.1), Eye(-0.1))
println(me.leftEye?.power)   // => 0.1
val her = Person("Varshini", Eye(-5.0), null) // arr
println(her.rightEye?.power) // => null
```

The Elvis operator `?:` can be used at the end of null chain calls when you want a default value in case you ended up with `null`.

```kotlin
val combinedPower = (her.leftEye?.power ?: 0.0) + (her.rightEye?.power ?: 0.0)
println(combinedPower) // => -5.0
```

## Console input

```kotlin
val name: String? = readLine()?.toString()
val age: Int? = readLine()?.toInt()
val eyePower: Double? = readLine()?.toDouble()

// Infers String?
val simple = readLine()
```

`readLine()` gives us a line of input as a `String`, the `?.` null safe calling takes care of input issues 

## Coroutines

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
  val deferredFirst =  async { getUser(1) }
  val deferredSecond = async { getUser(2) }
  println("Hello ${deferredFirst.await()}")   // Hello Amirtha
  println("Hello ${deferredSecond.await()}")  // Hello Astha
}

suspend fun getUser(id: Int): String? {
  val users = listOf("Harsh", "Amirtha", "Astha")
  delay(200) // simulated load time
  return users.elementAtOrNull(id);
}
```
