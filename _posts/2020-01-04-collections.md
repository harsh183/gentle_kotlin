---
layout: post
title: Collections
---

# What are Collections?

## Real-World Example

Say we're building an application that takes a picture of food and gives you recipes that use those ingredients.  While this sounds very complex, the first step would be to figure out how to store these food items in our program.  We can do so with something called collections.d

A collection is just a container that stores a number of objects.  These objects have to share the same type, so we can't have a collection of Ints, Doubles, and Booleans.  The objects stored in collections are called elements or items.  In our example, we can store a collection of food items represented with String literals!  How we use this collection depends on what type of collection we construct.  Kotlin provides different kinds of collections that are friendlier to use for different reasons; as such, depending on how you want to store and use objects, you might use a certain type of collection.  Let's delve into the different types.

## Types of Collections

### Mutable vs Immutable

Before we go into the different types, we need to talk about the difference between immutable collections and mutable collections.  We mentioned the concept of immutability when we introduced Kotlin values; in that context, we talked about how values are just variables that can't be changed over time.  The same applies with collections!  Once we construct a collection, meaning we add objects to it at the same time we declare it, we can't modify it anymore.  We call immutable collections as read-only collections, which just means that we can read through, or access, its items, without modifying the collection itself.

Mutable collections are just the opposite.  We can remove and add things anytime.  Both mutable and immutable collections are useful for different applications, and we'll give some examples we talk about the different types of collections.

### Lists

<!-- construct list -->

### Sets

<!-- might scrap since sets are more advanced -->

### Maps

<!-- explain key-val pairs, how they're different from lists -->

# How We Use Collections

