---
layout: post
title:  "Java Concurrency - Reference Guide"
date:   2020-08-18 00:00:00 +0000
lastUpdatedDate: 2020-08-18 00:00:00 +0000
categories: programming highlight
tags: programming
teaser: Java Concurrency - Reference Guide
permalink: /blog/java-concurrency-reference-guide
img-url: /assets/blog/programming/java-concurrency/Java-Concurrency.gif
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Information and Guidelines](#information-and-guidelines)
- [Running and Scheduling Tasks](#running-and-scheduling-tasks)
- [Thread-Safe Data Structures](#thread-safe-data-structures)
- [Locks](#locks)
- [Thread-Local](#thread-local)
- [References](#references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Information and Guidelines
* Multiple threads run concurrently, by using separate processors or different time slices on the same processor 
* Prefer using parallel algorithms and threadsafe data structures over programming with locks
* Visibility: if multiple threads update the same variable, their updates may not be visible across other threads by
default; synchronisation (or volatile declaration) may be necessary   
  * Value of a final variable is visible after initialisation
  * Initial value of static variable is available after static initialisation
  * Changes to volatile variables are visible
  * Changes that happen before releasing a lock are visible to anyone acquiring the same lock
![visibility-locks](/assets/blog/programming/java-concurrency/visibility-locks.png)  
(Ref: Java Concurrency in Practice, Brain Goetz)
* Race conditions: can occur whenever state shared across threads is mutated
* Strategies for safe concurrency
  * Confinement
  * Immutability
  * Locking / synchronisation (however, Locking is error-prone, and it can be expensive since it reduces opportunities
  for concurrent execution)
* For `parallelStream` to work well, 
  * The stream operations should not block (because it uses ForkJoinPool.commonPool by default and you don't want to
  exhaust this common pool)
  * The data should be in memory
  * There needs to be enough data; There is a substantial overhead for parallel streams that is only repaid for large data sets

# Running and Scheduling Tasks
* Tasks can be defined either using the `Runnable` or `Callable` interface
* Best to use `ExecutorService` to handle creation and scheduling of threads
* `Executors.newCachedThreadPool()` is optimised for use-cases with many tasks that are short-lived or spend most of 
their time waiting; there is no bound on the umber of concurrent threads
* A fixed size thread pool created using `Executors.newFixedThreadPool(nthreads)` is best suited for computationally 
intensive tasks so-as-to not exceed number of available processors (`Runtime.getRuntime().availableProcessors()`) or to
limit the resource consumption of a service
* Running tasks defined using `Runnable` and scheduled using an `ExecutorService`

```java
Runnable hellos = () -> {
    for (int i = 0; i < 1000; i++) {
        System.out.println("Hello " + i);
    }
};

Runnable goodbyes = () -> {
    for (int i = 0; i < 1000; i++) {
        System.out.println("Goodbye " + i);
    }
};

ExecutorService executor = Executors.newCachedThreadPool();
executor.execute(hellos);
executor.execute(goodbyes);
```
* Running tasks defined using `Callable` and obtaining result wrapped in a `Future`

```java
Callable<Integer> callable1 = () -> {
    int a;
    // ... some processing
    return a;
};

Callable<Integer> callable2 = () -> {
    int a;
    // ... some processing
    return a;
};

ExecutorService executor = Executors.newCachedThreadPool();
Future<Integer> result1 = executor.submit(callable1);
Future<Integer> result2 = executor.submit(callable2);

// blocking calls
result1.get()
result2.get()

// Alternatively, a list of callables can be submitted to an executor
List<Callable<Integer>> callables = List.of(callable1, callable2);
List<Future<Integer>> results = executor.invokeAll(callables); // blocking call, waits for *all* callables to complete before returning
```  
* Running a task asynchronously and obtaining a `CompletableFuture`

```java
// Using a Supplier that returns a result
Supplier<Integer> supplier = () -> {
    int a;            
    // ... some processing
    return sum;
};

ExecutorService executorService = Executors.newFixedThreadPool(2);
CompletableFuture<Integer> result = CompletableFuture.supplyAsync(supplier, executorService);

// Alternatively, if no executorService is supplied, ForkJoinPool.commonPool() is used
CompletableFuture<Integer> result = CompletableFuture.supplyAsync(supplier);

// Using a Runnable that returns void
CompletableFuture.runAsync(() -> {
    // do something
});
```
* `Callable<T>` vs `Supplier<T>`
  * A callable can throw a checked exception, while supplier can't
  * `CompletableFuture.supplyAsync` takes a `Supplier` as an argument
  * `ExecutorService.submit` takes a `Callable` as an argument
* Composing CompletableFutures

```java
    public static CompletableFuture<String> readPage(URI url) {
        // do something with the url...
    }

    public static CompletableFuture<URI> getURLInput(String prompt) {
        // do something with the prompt...
    }

    public static void main(String[] args) {
        getURLInput("example")
            .thenCompose(uri -> readPage(uri))
            .thenAccept(System.out::println);
    }
```
* Actions on CompletableFutures (Ref: Core Java SE 9 for the Impatient)    
![Completable Future Actions](/assets/blog/programming/java-concurrency/completable-future-actions.png)

# Thread-Safe Data Structures
* ConcurrentHashMap

```java
// Increment if present else initialise

// Not thread-safe
ConcurrentHashMap<String, Long> map = new ConcurrentHashMap<>();
Long oldValue = map.get("foo");
Long newValue = oldValue == null ? 1 : oldValue + 1;
map.put("foo", newValue);

// thread-safe
map.compute("foo", (k, v) -> v == null ? 1 : v+1);
System.out.println(map.values().toString()); // prints [1]

// thread same
map = new ConcurrentHashMap<>();
map.merge("foo", 1L, (oldVal, newVal) -> oldVal + newVal);
System.out.println(map.values().toString()); // prints [1]
map.merge("foo", 1L, (oldVal, newVal) -> oldVal + newVal);
System.out.println(map.values().toString()); // prints [2]
```
* BlockingQueue
* CopyOnWriteArrayList
* CopyOnWriteArraySet

# Locks
* Explicit locks

```java
Lock countLock = new ReentrantLock(); // Shared among multiple threads
int count; // Shared among multiple threads
//...
countLock.lock();
try {
    count++; // Critical section
} finally {
    countLock.unlock(); // Make sure the lock is unlocked
}
```
* Intrinsic locks: use the `synchronized` keyword

```java
public class Counter {
    private int value;
    public synchronized int increment() {
        value++;
        return value; 
    }
}
```

# Thread-Local
* Define a thread-local with initial value

```java
ThreadLocal<T> myThreadLocal = ThreadLocal.withInitial(Supplier<T>);
```
# References
1. Core Java SE 9 for the Impatient, Cay S. Hortsmann, Chpater 10 - Concurrent Programming
2. Java Concurrency in Practice, Brain Goetz

