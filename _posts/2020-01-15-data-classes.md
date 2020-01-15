---
layout: post
title: Data classes
---

A new thing Kotlin introduces over many other languages like `Java` is the `data class`. All we do is add 'data' before the start of the class.

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
val hero2 = Hero("Amirtha", "Warrior", 100)
println(hero1 == hero2) // => false
val hero3 = Hero("Harsh", "Mage", 80)
println(hero1 == hero3) // => true

// Destructure it
val (name, type, hp) = hero2
println(name) // => Amirtha
```
