---
layout: post
title: Intro to Coroutines
category: Coroutines
---

One of Kotlin's biggest strengths is a very easy and neat way to write programs that can make use of concurrency using `coroutines`. This allows for a way of running different pieces of code at once and avoid wasting time waiting during programs. 

If you've heard of threads before coroutines are a much more lightweight version of that where hundreds of thousands of coroutines can run for each thread. Similar to the what is used by the programming language Go, this is based off the `CSP` model.

<!-- ## Concurrency vs Parallelism. Important distinction -->

This is often quite intimidating, and other programming languages often have very weird and complex syntax to perform this kind of programming. Lots of it feels quite out of reach for beginners. Luckily for us Kotlin actually makes things quite nice for us and this is one of the strongest strengths of the language.

Let's take a normal looking program and see how to quickly convert to an asynchronous coroutine based program. Load two users and print out their details.

```kotlin
fun main() {
  val first =  getUser(1)
  val second = getUser(2)
  println("Hello $first")   // Hello Amirtha
  println("Hello $second")  // Hello Astha
}

fun getUser(id: Int): String? {
  val users = listOf("Harsh", "Amirtha", "Astha")
  Thread.sleep(200) // simulated load time
  return users.elementAtOrNull(id);
}
```

The issue here is that while loading and showing both the users are independent, we have to wait one after another to finish. But the time awaiting is just waiting for the response while the system sits idle. And this problem gets worse if it's not just two tasks like this, but hundreds or thousands.

The idea is that we can make use of this idle time using suspendable functions. The idea is that functions can be suspended and then resumed, so while it's waiting another function can take over and do it's thing. Then we just have to indicate by when we really need the result. Here is a coroutine version of the same.

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

### Import kotlin coroutines

Much like using the `math` package, we have to import `coroutines` since they aren't always used by most common programs. All we have to add to the top of the script

```kotlin
import kotlinx.coroutines.*
```

which imports everything coroutine related. In practice you may want to be more precise with imports but for learning coroutines it's good enough.

### The suspend keyboard

To make a function work with coroutines all we need to do is add the `suspend` keyword right in front of it. So `suspend` before `getUser()` now made it a suspendable function.

## Sleep vs delay 

`Thread.sleep()` is blocking, that means it doesn't allow anything else to happen while running, this is not what we want and we won't be able to make use of the suspending function logic. Instead we replace it with `delay()` which is non blocking so suspendable functions can take advantage of this and do tasks concurrently.

## Async and await

`async` basically lets us say, hey start this code given as a coroutine and keep track of the value it will be eventaully return. And when we use `await()` we can get that value when we need it.

If you try checking out what you get from the result of async itself you get `DeferredCoroutine` which is basically a represenation of the differed result of the coroutine. 

## runBlocking

Functions that use suspendable functions must also be suspendable, but this poses a problem where we have to make every single function of our program suspendable and in most cases that's simply not feasible. 

What `runBlocking` allows us to do is run coroutines in 'normal' blocking contexts. So like in a main function or anywhere in the code. This way we can program just as normal and then use coroutine based code where we need it. Of course, the more and more coroutine based code we write can give us performance but sometimes it does add complexity. 

## See also

* [Your first Coroutine with Kotlin](https://kotlinlang.org/docs/tutorials/coroutines/coroutines-basic-jvm.html)
* [Composing suspendable functions](https://kotlinlang.org/docs/reference/coroutines/composing-suspending-functions.html)
* A gentle introduction to Kotlin Coroutines [video](https://www.youtube.com/watch?v=q6ohvAw7bKM) and [slides](https://speakerdeck.com/amejia481/a-gentle-introduction-to-kotlin-coroutines)
