---
layout: post
title:  "Dropwizard runnable jar with Gradle"
date:   2017-06-21 10:50:00 +0000   
categories: programming
tags: programming
teaser: Unlike Maven Shade plugin, building a runnable Dropwizard application jar with Gradle isn't as straightforward as I initially thought
img-url: /assets/blog/engineering/gradle-dropwizard-uber-jar/dropwizard.png
---  

## Requirement
Build a runnable jar for a Dropwizard project from test<sup>*</sup> sources
using Gradle.

* Unlike most scenarios, where the Dropwizard application code sits in the main
sources directory, I had a scenario where the application lived in the test
sources (example: /src/test/java)

## Implementation

### Approach 1 - did not work
Wanted to avoid using 3rd party plugins so built an uber jar as follows
```
task packageTests(type: Jar) {
    manifest {
        attributes 'Main-Class': 'example.MyDropwizardAppMain'
    }
    from {
        sourceSets.test.output
    }
    from {
        configurations.testCompile.collect {
            it.isDirectory() ? it : zipTree(it)
        }
    }
    from {
        configurations.testRuntime.collect {
            it.isDirectory() ? it : zipTree(it)
        }
    }
    exclude("META-INF/*.SF")
    zip64=true
    archiveName "${baseName}-tests.jar"
}
```

#### Notes
* The attribute `zip64` whose value defaults to false was required to be set to
true as the resulting uber jar was larger (or contained more than the allowed
number of files) than what is allowed by default
* The exclude attribute excluding files with `.SF` extension in the META-INF
folder was required to prevent any signing issues in the resulting uber jar.
Without this, errors like the following are likely
```
Exception in thread "main" java.lang.SecurityException: Invalid signature file digest for Manifest main attributes
```

While this approach is known to have worked in most scenarios, it didn't work
for my Dropwizard application as running the uber jar gave the following error
```
Could not resolve type id 'http' into a subtype of [simple type, class io.dropwizard.jetty.ConnectorFactory]
```
A little reading on the web suggested this is due to the invalid merging of
files in the `META-INF/services` folder across all jar dependencies that get
packaged into the uber jar.

### Approach 2 - using the ShadowJar plugin

Using the [Shadow Jar](http://imperceptiblethoughts.com/shadow/) Gradle plugin
that has an option to `mergeServiceFiles()` appropriately (didn't really care
about understanding how 'appropriately' is precisely defined in this context)
worked and I was able to run my Dropwizard application using the resulting uber
Jar.

Gradle build script snippets below

```
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.github.jengelman.gradle.plugins:shadow:2.0.0'
    }
}

apply plugin: 'com.github.johnrengelman.shadow'

shadowJar {
    classifier = 'tests'
    from sourceSets.test.output
    configurations = [project.configurations.testRuntime]
    mergeServiceFiles()
    manifest {
        attributes 'Main-Class': 'example.MyDropwizardAppMain'
    }
}
```

## References
* http://imperceptiblethoughts.com/shadow/
* https://gist.github.com/yunspace/170efc94faa7fe974207
