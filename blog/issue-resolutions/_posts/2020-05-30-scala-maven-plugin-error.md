---
layout: post
title:  "Scala Maven Plugin - scala.runtime in compiler mirror not found"
date:   2020-05-30 01:27:00 +0100   
categories: issue-resolution
tags: issue-resolutions
teaser: Scala maven plugin error when using latest versions of plugins, jdk 11 and scala 2.13.2
---  

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Issue](#issue)
  - [Project Info](#project-info)
  - [Error Stacktrace](#error-stacktrace)
- [Resolution](#resolution)
  - [Observation](#observation)
  - [Fix](#fix)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Issue

### Project Info
* Java 11
```
❯ java -version
openjdk version "11.0.2" 2019-01-15
OpenJDK Runtime Environment 18.9 (build 11.0.2+9)
OpenJDK 64-Bit Server VM 18.9 (build 11.0.2+9, mixed mode)
```
* Maven 3.6.3
```
❯ mvn -version
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
```
* Maven compiler plugin 3.8.1
```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.8.1</version>
    <executions>
        <execution>
            <phase>compile</phase>
            <goals>
                <goal>compile</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <release>11</release>
    </configuration>
</plugin>
```
* Scala maven plugin
```xml
<plugin>
    <groupId>net.alchim31.maven</groupId>
    <artifactId>scala-maven-plugin</artifactId>
    <version>4.4.0</version>
    <executions>
        <execution>
            <id>scala-compile-first</id>
            <phase>process-resources</phase>
            <goals>
                <goal>add-source</goal>
                <goal>compile</goal>
            </goals>
        </execution>
        <execution>
            <id>scala-test-compile</id>
            <phase>process-test-resources</phase>
            <goals>
                <goal>testCompile</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <scalaVersion>2.13.2</scalaVersion>
    </configuration>
</plugin>
```

### Error Stacktrace
```
[ERROR] : error while loading Object, Missing dependency 'class scala.native in compiler mirror', required by /modules/java.base/java/lang/Object.class
[ERROR] ## Exception when compiling 155 sources to /Users/anuragkapur/tech-stuff/workspace/ak/algorithmic-programming/target/classes
scala.reflect.internal.MissingRequirementError: object scala.runtime in compiler mirror not found.

[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  5.178 s
[INFO] Finished at: 2020-05-30T01:26:10+01:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal net.alchim31.maven:scala-maven-plugin:4.4.0:compile (scala-compile-first) on project algorithmic-programming: wrap: scala.reflect.internal.MissingRequirementError: object scala.runtime in compiler mirror not found. -> [Help 1]
```

## Resolution

### Observation
Rolling back to Java 8 and scala-maven-plugin version `3.4.2` instead of `4.4.0` doesn't have the same issue and the project compiles 
successfully. But this is not a solution as I want this to work with Java 11!

### Fix
Add scala-library as a dependency, as specified in the [documentation of scala-maven-plugin v4.4.0](https://davidb.github.io/scala-maven-plugin/example_java.html)  
```xml
<dependency>
    <groupId>org.scala-lang</groupId>
    <artifactId>scala-library</artifactId>
    <version>2.13.2</version>
</dependency>
```

