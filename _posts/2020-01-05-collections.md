---
layout: post
title: Collections and Arrays
---

<img src="/assets/img/collections_and_arrays.png" width="300">

## Arrays

An array is a container that stores multiple items of the same type; for this reason, Kotlin has primitive type arrays such as IntArray, BooleanArray, etc.  Here's an example of an IntArray:

```kotlin
var array: IntArray = intArrayOf(1, 2, 3, 4, 5)
println(array[3]) // prints 4
array[0] = array[1] + array[2]
println(array[0]) // prints 5
println(array.size) // prints 5
```

We access the items in an array with indexing, a sort of numbering system.  In real life, we use 1-based indexing, meaning that the first item is at index 1.  In programming, however, we use 0-based indexing, so the first element is actually at index 0; similarly, the last element is at index `array.size - 1`.  To access an item in the array, we use the `[]` operator, which takes an Int as the index we want to look at.  In line 2, we printed out the value in the array at index 3, which is actually the 4th value listed in the array in 1-based indexing.

Since this array is a `var`, we can also modify the items at any index, as we did in line 3!  We took the sum of values at array[1] and array[2], which is 5, and passed it into array[0].  So, before that line, we had 1 at the 0th index of the array, but now we've replaced 1 with 5.  The array actually now reads as `[5, 2, 3, 4, 5]`.

We can also initialize an array by giving it a size without assigning values; when we do so, the Kotlin compiler will create an array of the size you gave and fill every spot in that array with the default value of the array's type.  This is better explained with an example:

```kotlin
val array = IntArray(5)
// this is an array with values: [0, 0, 0, 0, 0]
```

Creating a String array is a bit different; even though we use Strings like they're a primitive type, Strings are, in fact, NOT a primitive type.  In the above example we used the `intArrayOf` function to initialize an array of Ints; with Strings, we can use the `arrayOf<String>` function:

```kotlin
var stringArray = arrayOf<String>("hello", "world", "Kotlin")
println(stringArray[2]) // prints "Kotlin"

var emptyStrArr = arrayOf<String>(3)
// array of empty Strings: ["", "", ""]
``` 

One key thing to note about arrays is that their size is fixed at initialization; we can modify the items and access them at any given valid index (0 to `size - 1`), but we can't change the size itself, i.e. add or remove items.  With collections, if we've specified that we can modify them, we can add and remove elements as we please.

## A Real-World Example of Collections

Say we're building an application that takes a picture of food and gives you recipes that use those ingredients.  While this sounds very complex, the first step would be to figure out how to store these food items in our program.  We can do so with something called collections.

A collection is just a container that stores a number of objects.  Collections are similar to arrays, in that the objects they store have to share the same type, so we can't have a collection of Ints, Doubles, and Booleans.  With collections, however, we can change the size of the collection to store more objects (conventionally called elements or items)..

How we use this collection depends on what type of collection we construct.  Kotlin provides different kinds of collections that are friendlier to use for different reasons; as such, depending on how you want to store and use objects, you might use a certain type of collection.

## Mutable and Immutable Collections

### Immutable

Before we go into the different types, we need to talk about the difference between immutable and mutable collections.  We mentioned the concept of immutability when we introduced Kotlin values; in that context, we talked about how values are just variables that can't be changed over time.  The same applies with collections!  Once we construct a collection, meaning we add objects to it at the same time we declare it, we can't modify it anymore.  We call immutable collections as read-only collections, which just means that we can read through, or access, its items, without modifying the collection itself.

### Mutable

Mutable collections are just the opposite.  We can remove and add things anytime.  Both mutable and immutable collections are useful for different applications, and we'll give some examples we talk about the different types of collections.

## Types of Collections

### Lists

Lists are a type of collection that stores items in a specified order and uses indexing to access those item. Remember, indexing is just a way to access an element in a container using numbering; we use 0-based indexing, which means that the 1st element is in the 0th index, the 2nd element is in the 1st index, etc.  At first glance, they might seem really similar to arrays; they use similar operators to access and modify within it, but lists and arrays start to differ when we make a list mutable.

Here's an example of an immutable list:

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

#### Adding and Removing Elements

From the examples above, you can see that lists have built-in add and remove functions!  `removeAt` takes only one argument:  the index of the element to be removed.  In line 3 of the immutable example, we remove at the 0th index, or the 1st element in the list.  The `add` function takes an element and adds that element to the end of the list by default.  Here's an example:

```kotlin
var mutableList = listOf(2, 4, 6, 8, 10)
mutableList.add(12)
println(mutableList) // prints [2, 4, 6, 8, 10, 12]
```

To see more documentation on lists in Kotlin, check out [the official Kotlin site](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/index.html).  It goes more in detail with the add and remove functions, as well as similar built-in functions that come in handy with lists. 

#### Iterating through the Elments

Lists are really useful for storing objects and accessing them through something known as a `foreach` loop.  It's called a loop because the code block we write for it repeats itself for EVERY item in the list.  Let's start with a basic example:

```kotlin
var numbers = listOf(1, 2, 3, 4, 5)
for (item in numbers) {
  print("$item ")
}
```
The console prints out the following:

```
1 2 3 4 5 
```

Since our for loop only has line of code run for each item in the list, we can actually write the for loop as a single line of code, as opposed to a curly bracket-enclosed block:

```kotlin
for (item in numbers) print("$item ")
```

We can't modify the items in a `foreach` loop, we can access them and read their attributes.  In this case, we access every item and just print them, but we can make `foreach` loops to do a variety of things with just a bit of conditional logic.  We can also access the index of every element by looping through the indices.  The syntax looks like the following:

```kotlin
var chars = listOf('a', 'b', 'c', 'd')
for (i in chars.indices) {
  print(chars[i] + " ")
}
```

When run, the code above prints out the following on the console:

```
0 1 2 3 
```

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

Unlike maps, lists can contain duplicate entries.  A list functions like a list; we can read from top to bottom using numerical indexing, and add and remove things.  The order doesn't matter unless the list is sorted, so finding a value without knowing its index can mean looking through the entire list.

## Maps

Maps can't have duplicate keys, which makes values less complicated to find.  With a list, we have to start from either the top or the bottom from the list and work our way through the entire list to find our value.  With maps, if we know the key, we can find the value in one line of code!

# See More

* [Kotlin collections - Geeks for geeks](https://www.geeksforgeeks.org/kotlin-collections/)

* [Collections overview - Kotlin official docs](https://kotlinlang.org/docs/reference/collections-overview.html)

* [Collections - CS 199 IKP](https://kotlin.cs.illinois.edu/lessons/collections/)

* [Collections overview - Baeldung](https://www.baeldung.com/kotlin-collections-api)

* [Immutable Collections - Baeldung](https://www.baeldungtest.com/kotlin-immutable-collections)
