---
layout: post
title: Inheritance
---

After a while you start to notice how a lot of classes start having really similar boilerplate and standard code. What Inheritance does is it lets us extend classes from a Base and then add on only the stuff we need. That way we can put the common stuff in the base class itself. 

Consider making a simple setup for a teacher and their group of a students. 

```kotlin
class Student(val name: String,
              var age: Int,
              var mathScore: Double,
              var scienceScore: Double) {
    fun display() {
        println("Name: $name")
        println("Age: $age")
        println("Math score: $mathScore")
        println("Science score: $scienceScore")
    }
}

class Teacher(val name: String,
              var age: Int,
              var students: Collection<Student>) {
    fun display() {
        println("Name: $name")
        println("Age: $age")
        println("Number of students: ${students.size}")
    }
}

fun main() {
    val me = Student("Harsh", 20, 98.5, 95.3)
    me.display()
    val geoff = Teacher("Geoffery Challen", 4000, listOf(me)) 
    geoff.display()
}
```

If we look above both classes have a lot of common data and functionality. One very important principle of programming is DRY (Don't Repeat Yourself) so we can use `inheritance`. How it works is creating a base class that other classes can use as a starting point for adding more data and functionality. This leads to nicer design, fewer bugs and shorter programs when used well. 

## Identify common data and functionality

`name`, `age` are common for both classes so we can extract that. 

In terms of functionality the first two lines of `dispay()` are the same so we can extract that as well.

## New Base Class

```kotlin
open class Person(val name: String,
                  var age: Int,) {
    open fun display() {
        println("Name: $name")
        println("Age: $age")
    }
}
```

By default, Kotlin classes are set up that no classes can be derived from it so we have to add the `open` keyword. Adding `open` in front of the class makes it clear that the class can have other classes inherit from it. Making our `open class Person` sets up the base class we're going to have as a starting point for `Student` and `Teacher`.

Adding `open` before a function lets derived classes create a new function with the same name. Otherwise you will have to create new functions in your derived classes. Our `open fun display()` will be overriden by both `Student` and `Teacher` since they do display slightly differently.

## Derived Classes

```kotlin
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

To indicate a class is derived we have to indicate in the class header itself and if there is a constructor we have to pass the right variables along as well. This is what `: Person(name, age)` does in our example by indicating that these class derives from `Person` and `(name, age)` are passed to the base class constructor.

`override` indicates that we are overriding a function from the base class and using `super.functionName()` lets us call the existing display function from the base class. In general the `super` keyword lets us access things specific to the base class that isn't always there in derived classes.

## Output

If you did everything right, the output and behavior of the program should be the same.

```kotlin
fun main() {
    val me = Student("Harsh", 20, 98.5, 95.3)
    me.display()
    val geoff = Teacher("Geoffery Challen", 4000, listOf(me)) 
    geoff.display()
}
```

which gives

```
Name: Harsh
Age: 20
Math Score: 98.5
Science Score: 95.3
Name: Geoffery Challen
Age: 4000
Number of students: 1
```

## See More

* [Classes and Inheritance - Official Docs](https://kotlinlang.org/docs/reference/classes.html)

* [Kotlin Delegation Pattern - Baeldung](https://www.baeldung.com/kotlin-delegation-pattern) - An interesting alternative to look into

* [Kotlin Sealed Classes - Baeldung](https://www.baeldung.com/kotlin-sealed-classes) - When you want to restrict inheritance to only a few subtypes
