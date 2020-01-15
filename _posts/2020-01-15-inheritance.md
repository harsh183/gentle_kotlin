---
layout: post
title: Inheritance
---

After a while you start to notice how a lot of classes start having really similar boilerplate and standard code. What Inheritance does is it lets us extend classes from a Base and then add on only the stuff we need. That way we can put the common stuff in the base class itself. 

Consider making a simple setup for a teacher and their group of a students. 

```kotlin
data class Student(val name: String,
                   var age: Int,
                   var mathScore: Double,
                   var scienceScore: Double) {
    fun reportCard() {
        println("Name: $name")
        println("Age: $age")
        println("Math score: $mathScore")
        println("Science score: $scienceScore")
    }
}

data class Teacher(val name: String,
                   var age: Int,
                   var students: Collection<Student>) {
    fun details() {
        println("Name: $name")
        println("Age: $age")
        println("Number of students: ${students.size}")
    }
}
```

## Identify common data

`name`, `age`

## Indentify common functionality 

`data` does a lot of it for us also the first two lines of both prints can be made common

## Syntax

## Better code

<!-- TODO: Showing more abstract function calling and such -->
