    ---
layout: post
title:  "Spring boot class hotswap in IntelliJ"
date:   2018-06-3 19:15:00 +0000   
categories: programming
teaser: Enabling hot swap of classes in a spring boot application with IntelliJ Idea IDE
---  

Spring boot dev tools enable hot swapping and fast application restarts when a class file in the classpath changes. This
speeds up development by reducing the time spent in a change, re-build and manually restarting the container.

This is done by adding the following dependency to a gradle project:
```groovy
dependencies {
	compile("org.springframework.boot:spring-boot-devtools")
}
```

However, there is a minor catch! The devtools only swing into action when a file in the classpath is changed. This does
not happen by default in IntelliJ when you make a change to a java class file and save it. To make it happen, either:

1. Build project (Cmd + F9) which recompiles files and updates the classpath folder, thereby triggering the devtools
to do a fast app restart
or
2. Make the following change to the IDE registry (Cmd + Shift + A) entry for the follwing attribute to true
```
compiler.automake.allow.when.app.running
```

I personally prefer option 1 as I have control over when I want the fast restart to happen. It however comes with a few
extra keystrokes to also to a build (Cmd + F9) after a save action. I just find this a matter of getting used to and 
prefer the extra controlled and not having restarts happening all over the place.
