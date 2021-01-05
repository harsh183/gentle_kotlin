---
layout: post
title: Classes and Objects
---

Classes are perhaps the most defining feature of Kotlin, allowing us to create custom data types with specific data and behaviour. This feature of languages is what sets up the category of programming languages called Object-Oriented Programming languages which include some of the most popular languages today like Java, Ruby, Python, C++, Swift, C#, Rust etc.

Quite simply, with classes you create a container where you can define specific variables that stores information and create specfic functions that can create custom behavior.

<!-- This is a heavy one, start with data container, then how to add functions, then what constructors are, then constructor short hand, dot notation, type inference-->

```kotlin
class Hero(val name: String, val type: String, var healthPoints: Int) {
    fun attacked(damage: Int) {
        println("Oh no! $name got attacked with $damage with $healthPoints hp left")
        healthPoints -= damage
    }

    fun healed(hp: Int) {
        println("Yay! $name got healed with $hp with $healthPoints hp now")
        healthPoints += hp
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

fun main(args: Array<String>) {
    val harsh = Hero("Harsh", "Mage", 100)
    val amirtha = Hero("Amirtha", "Warrior", 120)
    amirtha.attack(harsh)
    println()

    println("Ooops, let me heal you")
    amirtha.heal(harsh)

    println()
    println("You aren't a mage so it wasn't that useful")
    println("I'll do it myself")
    harsh.heal(harsh)
}
```

# See More

* [Classes - CS 199 IKP](https://kotlin.cs.illinois.edu/lessons/classes/)

* [Classes and Inheritance - Official Docs](https://kotlinlang.org/docs/reference/classes.html)

* [Inline classes](https://kotlinlang.org/docs/reference/inline-classes.html)

* [Objects in Kotlin - Baeldung](https://www.baeldung.com/kotlin-objects)

* [Kotlin Constructors - Baeldung](https://www.baeldung.com/kotlin-constructors)
