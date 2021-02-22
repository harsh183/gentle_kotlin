---
layout: post
title: "Web Services with Kotlin using Ktor (Installation)"
category: Ktor
---

JetBrains provides users with an option to install ktor using their [IntelliJ Idea Plugin](https://ktor.io/docs/intellij-idea.html#using-the-plugin). However, if you don't use IntelliJ Idea IDE or you would simply like to install it by yourself using Gradle, then this guide can be useful to you!

## Installation using Gradle from Scratch

To setup ktor using Gradle, first ensure that you have Gradle installed on your machine. Then, make a new directory for your project and run the `gradle init` command inside it. After this, you will be prompted to enter the project options. For this, you should select `Application` for project type, `Kotlin` for implementation language, and `Kotlin` again for script DSL. If you are prompted to split the application into multiple sub-projects, then feel free to choose whichever option you prefer. For the purpose of this guide, I opted to go with the 'no' option. The project and package name can be set as desired (or left as default). Once the `gradle init` command has finished running with all the provided options, you can use the `gradle run` to run the generated 'Hello, World' program. The source code for this project can be found under `/app/src/main/kotlin/<project-name>/` and you can edit this as desired to test things out.

Next, ktor will need to be installed in the generated gradle kotlin project. For this, you will first need to visit the [Official Ktor Website](https://ktor.io/) and navigate to the [gradle section on the docs](https://ktor.io/docs/gradle.html#initial) in order to obtain the latest version number of ktor that you wish to install. Then, you will need to add the following lines under `dependencies` in the `app/build.gradle.kts` file of your project:

```kotlin
implementation("io.ktor:ktor-server-core:<ktor-version-goes-here>")
implementation("io.ktor:ktor-server-netty:<ktor-version-goes-here>")
```

Note: **Please ensure that you add the desired ktor version in the lines given above.** To use the latest version, simply refer to the docs as mentioned above. The final `build.gradle.kts` file should look something like this (likely with different versions and mainClass name under application):

```kotlin
plugins {
    id("org.jetbrains.kotlin.jvm") version "1.3.72"
    application
}

repositories {
    jcenter()
}

dependencies {
    implementation(platform("org.jetbrains.kotlin:kotlin-bom"))
    implementation("org.jetbrains.kotlin:kotlin-stdlib-jdk8")
    implementation("com.google.guava:guava:29.0-jre")
    implementation("io.ktor:ktor-server-core:1.5.0")
    implementation("io.ktor:ktor-server-netty:1.5.0")
    testImplementation("org.jetbrains.kotlin:kotlin-test")
    testImplementation("org.jetbrains.kotlin:kotlin-test-junit")
}

application {
    mainClass.set("gradle.test.AppKt")
}
```

Now, when you run `gradle run`, gradle should automatically resolve all the dependencies. If you're using IntelliJ Idea IDE to work with this project, then you may have to reload the IDE or click on the option that lets you reload and index changes made by `gradle run` into IntelliJ.

To verify that everything is working as intended, you can add the following code to the `App.kt` file in your project (be sure to change the package name as neccessary!) and use the command `gradle run` to start the web server. If everything went smoothly, then visiting the URL `http://localhost:8080` should show you a web page with the text `Hello, World!`.

```kotlin
package KtorTestProject // This package name should be different for you

import io.ktor.application.*
import io.ktor.response.*
import io.ktor.routing.*
import io.ktor.server.netty.Netty
import io.ktor.server.engine.embeddedServer

fun main(args: Array<String>) {
    embeddedServer(Netty, 8080) {
        routing {
            get("/") {
                call.respondText("Hello, World!")
            }
        }
    }.start(wait = true)
}
```

You can find the code generated and shown in this guide over at [this repository](https://github.com/p-vinayak/gentlekotlin-ktor-starter).

## Installation using Gradle from Ktor Starter (Recommended)

If you don't want to setup everything from scratch using Gradle as shown in the section above, then you can use [Ktor's Project Generator](https://start.ktor.io/) that comes with everything that you would need to get started on a ktor project. The project generator even lets you select from many of the useful dependencies that you may want on your project (such as JSON serialization, CORS, and Session support).

To get started with the project generator, visit [Ktor's Project Generator](https://start.ktor.io/) and choose `Gradle project` and check the `with Wrapper option`. Then, choose the `Netty` server engine and latest ktor version available to you. The remaining text fields can be filled out as desired but for this guide I filled out `com.gentlekotlin.helloworldktor` for group and `hello-world-ktor` for project name. For the scope of this guide, we will not reuiqre any additional dependencies so you can leave all of the server-side and client-side features unchecked.

Lastly, simply click on `Build` and you should have a zipped version of your starter project ready to go. Now, simply unzip the project files, open the extracted directory, and use the `gradle run` command. This should resolve all dependencies for you and start the ktor server on `http://0.0.0.0:8080/` for you. However, when you visit this, don't be surprised if get a `Page not found` error. To fix this, we will need to define what our application actually does. Head on over to the `src/Application.kt` file of your project and the following lines of code to your `Application.module` function:

```kotlin
    routing {
        get("/") {
            call.respondText("Hello, World!")
        }
    }
```

Make sure to add any imports that are needed. Your final `Application.kt` file should look something like this (apart from the package name):

```kotlin
package com.gentlekotlin.helloworldktor // This package name should be different for you!

import io.ktor.application.*
import io.ktor.response.*
import io.ktor.routing.*

fun main(args: Array<String>): Unit = io.ktor.server.netty.EngineMain.main(args)

@Suppress("unused") // Referenced in application.conf
@kotlin.jvm.JvmOverloads
fun Application.module(testing: Boolean = false) {
    routing {
        get("/") {
            call.respondText("Hello, World!")
        }
    }
}
```

Now, when you restart your application and visit the same `http://0.0.0.0:8080` url, you should see a text saying "Hello, World!" You can find the code generated and shown in this guide over at [this repository](https://github.com/p-vinayak/gentlekotlin-ktor-starter).
