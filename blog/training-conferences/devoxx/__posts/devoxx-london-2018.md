# Parallel and Asynchronous Programming with Streams and Completable Future

by Venkat Subramaniam

## Parallel vs Asynchronous
* party example where we need pizza and drinks, get pizza and drinks in parallel, order and wait

## Parallel Streams
* "Lambdas are the drug, streams is the addiction"
* Martin Fowler: Collection pipeline pattern
* Stream is an internal iterator - iterator on auto-pilot
* Imperative style has accidental complexity
* Functional style has less complexity and easier to parallelise
* Imperative style the structure of sequential code is very different from the structure of concurrent code
* Using stream the structure of sequential code is identical to the structure of cocurrent code
    - enhances readability, debugability, testability
* Mutability and parallel don't go together
* ![java-streams-paralle-sequential](/assets/blog/training/devoxxuk2018/devoxx - 2.png) 
- last one (the one before the terminal operation) wins
* <insert pic> - paralleStream uses Common FJP
* Some methods are inherently ordered
* Some methods are unordered but may have an ordered counterpart
```java
forEach(System.out::println);
forEachOrdered(System.out::println); // doesn't guarantee ordering unless the stream does. Ex: List vs Set
```
* filter and map can run in parallel
* reduce - (aka foldLeft) - runs as expected in parallel iff initial value = identity value, if not you may not get
expected result
    - <insert pic>
    - monoid ??
* How many threads
    - How many threads can I create? // bad question
    - How many thread should I create? // good question
    - Computation intensive vs IO intensive
    - Computation intensive: threads <= # of cores
    - IO intensive: threads may be greater than cores... how may, don't know yet
    ```
    #T = # of cores / (1 - blocking factor), where 0 <= blocking factor < 1
    ```

## Streams | Reactive streams
* sequential vs parallel | synchronous vs asynchronous
* entire pipeline is sequential or parallel | Depends 
* no segments | subscribeOn - no segments; observerOn - segments

## CompletableFutures
* Non-blocking
* Stream | CompletableFuture
<insert pic>
* Callbacks
    - lacks consistency: first param data or error? no consistency
    - hard to compose: callback chain or callback hell
    - hard to deal with errors
* Exception handling and functional programming are mutually exclusive
* JavaScript world moved to promises
    - may resolve, reject or be pending
    - have two channels: data channel and error channel
    - errors are first class citizens
    - failure/error is like data
* CompletableFuture is Java is Promises in JavaScript
    - have stages
    - evert stage takes a CF and returns a CF
* <insert pic>
* `future.get()` is a bad idea as it is a blocking call
* Futures use the main thread when running something on a separate thread isn't necessary/valuable
* Methods
    - thenAccept()
    - thenRun() // used to celebrate success of the accept op
* You can recover from an exception path and move back to the data path
```
---f---f---f           f---f---f 
            \         /
             f---f---f
```

## References
* http://agiledeveloper.com/downloads.html
    
# Reactive Spring Deep Dive
    
by Mark Heckler
    
* Non-blocking and event driven 
* Scales with a small number of threads
* Key interfaces
    - Publisher<T>
    - Subscriber<T>
    - Subscription
    - Processor<T,R>
* Debugging with async reactive code is non trivial
    - `Hooks.onOperatorDebug()`
    - use `checkpoint()`
    - to get full stacktrace: `checkpoint(description: "checkpoint A", forceStackTrace: true)`
    
## References    
* https://projectreactor.io/
* http://start.spring.io/
* https://github.com/mkheck/reactive-spring-deepdiveite

# Exploring the Real Power of Streams

by Venkat Subramaniam

* Postpone evaluation
* Applicative order vs Normal order
    - most mainstream systems use applicative order
    - applicative order: evaluation when applied or invoked
    - normal order: execution is deferred
* Haskell is lazy, i.e. uses normal order or uses lazy evaluation
* Scala can do lazy evaluation when the `lazy` keyword is used
```scala
lazy val x = compute(2)
```
* How do we do lazy evaluation in Java?
    - Lambdas are a level of indirection
    - <insert pic>
    - Lombok also provides a `@Lazy` annotation
* <insert pic>
* Lambdas are stateless; closures carry __immutable__ state
<insert pic>
* Lazy evaluation at display
<insert pic>

# Kotlin for Java Programmers

by Venkat Subramaniam

* Running Kotlin
    - compile and run
        * java -jar
        * kotlinc && kotlin
    - use REPL
    - run as script
* Niceties
    - Semicolon optional
    - Useful warnings
    - `val` and `var`, like in Scala
    - String tempaltes
    ```kotlin
    val name = "Sam"
    println("Hello $name")
    printlno("Hello ${name.length}")
    ```
    - Expressions over statements
    - Default method args
* Pattern matching
<insert pic>
