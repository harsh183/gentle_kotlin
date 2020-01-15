---
layout: post
title: Classes and Objects
---

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


