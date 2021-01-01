---
layout: post
title: "Web Services with Kotlin using Ktor (Installation with Gradle)"
category: Ktor
---

## Installation using Gradle

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

To verify that everything is working as intended, you can add the following code to the `App.kt` file in your project and use the command `gradle run` to start the web server. If everything went smoothly, then visiting the URL `http://localhost:8080` should show you a web page with the text `Hello, World!`.

```kotlin
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

You can find the code generated and shown in this guide over at [this](https://github.com/p-vinayak/gentlekotlin-ktor-hello-world) repository.
