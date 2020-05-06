---
layout: post
title: "Launch, Join, And Hundreds of Thousands of Jobs"
category: Coroutines
---

In the previous post I mentioned that `coroutines` were like lightweight threads, but lets get an idea of how many different concurrent jobs can coroutines handle.

### `launch`

We start a `coroutine` with the `launch` lambda function.  Here's a simple example:

```
println("Start")

// Start a coroutine
GlobalScope.launch {
    delay(1000)
    val x = 2*6
    println(x)
}

Thread.sleep(2000) // wait for 2 seconds
println("Stop")
```

### `join`




<!-- show code example of launching lots of threads and failing, then launching lots of coroutines with ease, teach the launch and join instructions, and maybe a little intro to (but not detailed) on Atomic data types -->
