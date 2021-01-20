---
layout: post
title: Classes and Objects
---

Classes are perhaps the most defining feature of Kotlin, allowing us to create custom data types with specific data and behaviour. This feature of languages is what sets up the category of programming languages called Object-Oriented Programming languages which include some of the most popular languages today like Java, Ruby, Python, C++, Swift, C#, Rust etc.

Quite simply, with classes you create a container where you can define specific variables that stores information and create specfic functions that can create custom behavior.

## Data Container 

The first thing we can understand about classes as a grouping of data under a common name. 

In this case we have made an RPG like class called `Hero` which has three properties 

1. `name` of the Hero which is a `String` since players can use any number of characters to define their name
2. `type` of the Hero that is game specific roles that could have different custom behaviour like `Mage` or `Warrior`
3. `healthPoints` of the Hero which is an `Int` which represents how alive the character is and having it go too low can end the game.

In each case you have to consider how to use classes based on your specific code design and what can be composed of what. There are often many different ways to do it so don't worry if you see lots of the same approaches to different problems.

## Basic class syntax

So all we're doing is creating a more complex data type out of existing data types we know. For this we use the `class` keyword and curly `{}` brackets all the variables it holds. Here I give some default values for each of the three variables.

```kotlin
class Hero {
    var name: String = "Harsh"
    var type: String = "Mage"
    var healthPoints: Int = 120
}
```

Here I setup the `Hero` class with the three variables and sample values. Now when I want to use this new data type in my code is declare it like any other variable. Every time you make a variable that is of a particular type, we call it an `object` of that class. Below is an object of the type `Hero` that we refer to as `harsh` in the code.

```kotlin
val harsh: Hero = Hero()

// Getting
println(harsh.type)
// => Mage
println(harsh.healthPoints)
// => 120

// Setting
harsh.healthPoints = 70
println(harsh.healthPoints)
// => 70
```

Using `variable_name.property` can let me access the inner variables that make up the class. You can print it, use it in some computation and use the `=` as if you'd change any other variable.

### Constructor

Let's make another object and then set the fields we want.

```kotlin
val varshini = Hero()
varshini.type = "Warrior" 
varshini.name = "Varshini"
```

Now you start to see how this can quickly get annoying. Every time you make a new `object` you have to setup each field with `.variableName =`. For large classes this can take a lot of space and this adds clutter. This also results in making everything `var` that we want custom but it will be better if we can set some properties to be assignable once.

For this we can use constructors. Constructors are like special functions that are run when an object is first created. All you have to do is add a list of parameters in `()` round brackets and then use it to set up your variables. Make sure they're called something different than the variables in your class. Thanks to constructors we were able to make `name` and `type` into `val` which we were not able to do earlier.

```kotlin
class Hero(setName: String, setType: String) {
    val name: String = setName
    val type = setType
    var healthPoints = 120
}
```

And declaring a new object becomes nicer too

```kotlin
val varshini = Hero("Varshini", "Warrior")
``` 

Creating an object with name `"Varshini"`, type `"Warrior"` and healthpoints `120` a default value.

### Constructor short hand

Even that sytnax can get quite repetitive. That's why kotlin has made a simple shorthand for the most common case with constructors. If you add `var` or `val` before the variables it'll create the same constructor for you automatically. Using `=` we can set default values as well which is most common reason we often have many constructors too.

```kotlin
class Hero(val name: String, val type: String, var healthPoints: Int = 120) 
```

And the earlier declaration code works unchanged. 
```kotlin
val varshini = Hero("Varshini", "Warrior")
``` 

## Adding functions

Inside the class body `{}` you can add functions that are only avaible to objects that belong to the class. This is how we create specialized behavior for classes. Functions inside a class can access that object's variables just by mentioning it by name.

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
}
```

As you can see above that the syntax for functions is the same but we can access properties of the object as well. To use these functions we use the same `.` dot notation like `object.functionName(...)`

```kotlin
val varshini = Hero("Varshini", "Warrior")
varshini.attacked(50) // Oh no
// => Oh no! Varshini got attacked with 50 with 70 hp left
varshini.healed(70)   // yay
// => Yay! Varshini got healed with 70 with 140 hp now
```

### Calling functions on other objects

Our functions can also work on other objects of the same kind. This is useful because we want objects to interact with each other. Here we can set up functions that take `Hero` objects and call actions on them.

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

Look at the two new functions, `attack` and `heal`, they both act differently based on the `type` of the `Hero` and use the `.` dot notation to call things from other classes.

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

which outputs

```
Varshini attacks Harsh
Oh no! Harsh got attacked with 50 with 50 hp left

Ooops, let me heal you
Varshini casts heal on Harsh
Yay! Harsh got healed with 10 with 60 hp now

You aren't a mage so it wasn't that useful
I'll do it myself
Harsh casts heal on Harsh
Yay! Harsh got healed with 40 with 100 hp now
```

# See More

* [Classes - CS 199 IKP](https://kotlin.cs.illinois.edu/lessons/classes/)

* [Classes and Inheritance - Official Docs](https://kotlinlang.org/docs/reference/classes.html)

* [Inline classes](https://kotlinlang.org/docs/reference/inline-classes.html)

* [Objects in Kotlin - Baeldung](https://www.baeldung.com/kotlin-objects)

* [Kotlin Constructors - Baeldung](https://www.baeldung.com/kotlin-constructors)
