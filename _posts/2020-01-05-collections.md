---
layout: post
title: Collections
---

# What are Collections?

## Real-World Example

Say we're building an application that takes a picture of food and gives you recipes that use those ingredients.  While this sounds very complex, the first step would be to figure out how to store these food items in our program.  We can do so with something called collections.

A collection is just a container that stores a number of objects.  These objects have to share the same type, so we can't have a collection of Ints, Doubles, and Booleans.  The objects stored in collections are called elements or items.  In our example, we can store a collection of food items represented with String literals! 

How we use this collection depends on what type of collection we construct.  Kotlin provides different kinds of collections that are friendlier to use for different reasons; as such, depending on how you want to store and use objects, you might use a certain type of collection.  Let's delve into the different types.

## Types of Collections

### Mutable vs Immutable

Before we go into the different types, we need to talk about the difference between immutable collections and mutable collections.  We mentioned the concept of immutability when we introduced Kotlin values; in that context, we talked about how values are just variables that can't be changed over time.  The same applies with collections!  Once we construct a collection, meaning we add objects to it at the same time we declare it, we can't modify it anymore.  We call immutable collections as read-only collections, which just means that we can read through, or access, its items, without modifying the collection itself.

Mutable collections are just the opposite.  We can remove and add things anytime.  Both mutable and immutable collections are useful for different applications, and we'll give some examples we talk about the different types of collections.

### Lists

Lists are a type of collection that stores items in a specified order and uses indexing to access those items.  In Kotlin, indexing starts at 0, i.e. the first element in a list is at the 0th index, the second element in a list is at the 1st index, and so on.

Here's an example of an immutable list:

#### Mutable and Immutable Lists

```kotlin
val immutableList = listOf(2, 4, 6, 8, 10)
println(immutableList[0]) // prints 2
immutableList[0] = 12 // compile error!
```

Since we used the keyword 'val,' this list is immutable.  Remember, vals are immutable variables; as such, we can't delete or add anything to the list.  We also can't modify any of the list's elements, which is why the third line will not compile.

 Here's an example of a mutable list:

```kotlin
var mutableList = listOf(2, 4, 6, 8, 10)
mutableList[0] = 0 // now the list is 0, 4, 6, 8, 10
mutableList.removeAt(0) // now the list is 4, 6, 8, 10
```

#### Add and Remove

From the examples above, you can see that lists have built-in add and remove functions!  `removeAt` takes only one argument:  the index of the element to be removed.  In line 3 of the immutable example, we remove at the 0th index, or the 1st element in the list.  The `add` function takes an element and adds that element to the end of the list by default.  Here's an example:

```kotlin
var mutableList = listOf(2, 4, 6, 8, 10)
mutableList.add(12)
println(mutableList) // prints [2, 4, 6, 8, 10, 12]
```

To see more documentation on lists in Kotlin, check out [the official Kotlin site](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/index.html).  It goes more in detail with the add and remove functions, as well as similar built-in functions that come in handy with lists. 

### Sets



### Maps

A map is a collection of keys that point to values, stored as key-value entries.  A key can be of any type, as can a value.  For example, let's say we're storing companies in our program and need a way to easily look up their annual revenues; we can create a map that stores Strings as keys that point to Int values.  Each key is the name of the company and points to an Int that represents that company's value.  With this set up, all it takes is the company's name and the computer will automatically return to us the revenue we're looking for!

```kotlin
var studentGrades = mapOf("Alice" to 96.7, "Greg" to 90.1, "Jessica" to 89.7)
studentGrades.put("Max", 94.3)
studentGrades["Alice"] = 97.0
```

`Map<K,V>` has a built-in `put` function that allows us to add key-value pairs to mutable maps.  It takes a key and a value, in that order.  If a map is mutable, we can also modify a key's value by using the `[]` operator.

While lists allow us to keep track of objects by numerical indexing, maps give us a more convenient way to model real-life data into our Kotlin programs.
<!-- explain key-val pairs, how they're different from lists -->

# How We Use Collections

## Lists



## Maps

# Links

[Kotlin collections](https://www.geeksforgeeks.org/kotlin-collections/)
