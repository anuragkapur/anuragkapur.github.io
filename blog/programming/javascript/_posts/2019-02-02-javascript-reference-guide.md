---
layout: post
title:  "JavaScript Reference Guide"
date:   2019-10-16 00:00:00 +0000   
categories: programming javascript highlight
tags: programming
teaser: My JavaScript reference guide, created when taking courses, experimenting and coming across stuff during projects 
img-url: /assets/blog/programming/js.jpg
permalink: /blog/js-reference-guide
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Fundamentals](#fundamentals)
- [Callbacks, Higher Order Functions and Closures](#callbacks-higher-order-functions-and-closures)
- [Asynchronicity](#asynchronicity)
- [Classes and Prototypes (OOP)](#classes-and-prototypes-oop)
    - [Approach 1: Using a function](#approach-1-using-a-function)
    - [Approach 2: Using the prototype chain](#approach-2-using-the-prototype-chain)
    - [Approach 3: The `new` keyword](#approach-3-the-new-keyword)
    - [Approach 4: The `class` syntactic sugar](#approach-4-the-class-syntactic-sugar)
- [References](#references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Fundamentals
* What is functional programming?
  * FP is about verbs, while OOP is about nouns
  * Core tenant: pure functions don't have side effects which in turn makes the code easier to test
* Core JavaScript engine has 2 main parts
  * Execution context
  * Call stack
* An **execution context** is created to run the code of a function - has 2 parts:
  * Thread of execution
  * Memory 
* JS keeps track of what function is currently running, i.e. where's the thread of execution using a Call Stack
* JavaScript has a single thread of execution  
* Each function invocation gets its own new execution context
* Primitives are stored/passed by value and objects are stored/passed by reference
    ```javascript
    var person = {}; 
    person.name = "Mrs. White";
    var who = person.name;
    who; // "Mrs. White"
    person.name = "Mr. White";
    who; // Doesn't change; value remains "Mrs. White"
    ```  
* Arrays are just objects, with some special utility methods and the length property
    ```javascript
    var person = [];
    person.name = "Mrs. White";
    var who = person.name;
    who;
    typeof person === "array";  // false; instead, Array.isArray() can be used to find out if an object is an array
    typeof person === "object"; // true 
    person.push({age: 42});     // 0: {age: 42}, 1: {age: 54}, name: "Mrs. White"
    person.length;              // 1
    ```
* Using variables to access object properties - the thing after the dot notation is coerced into a string literal, while
one can use variables in the [] notation.
    ```javascript
    var person = [];
    var plea = "wouldShe";
    person.name = "Mrs. White";
    person[plea] = "I Would Never";
    person; // {name: "Mrs. White", wouldShe: "I Would Never"}
    ```
* ES6 destructuring
    ```javascript
    // variable declarations
    let [a, b] = [true, false];
    a; // true
    b; // false
    let {a, b} = {b: 0, a: 1};
    a; // 1
    b; // 0
    ```
* Variables declared with `let` have block scope while those with `var` have global scope
* `for..in` loop to iterate over keys of an object
    ```javascript
    var obj = {key1: 1, key2: 2};
    for (var key in obj) {
        console.log(obj[key]);
    }
    ```
* `for..of` loop to iterate over elements of array
    ```javascript
    let a = [1, 2, 3, 4, 5];
    for (let num of a) {
        console.log(num);
    }
    ```
* Objects can have function in addition to attributes
    ```javascript
    // ES5
    var obj1 = {
                name: "foo",
                age: 19,
                speak: function() {
                    console.log("ny name is ", this.name);
                }
            };
    
    // ES6
    var obj2 = {
                name: "foo",
                age: 19,
                speak() {
                    console.log("ny name is ", this.name);
                }
            }
    ```
* Functions are just objects under the hood
* Spread operator, aka rest parameter syntax - like varargs in java
    ```javascript
    var addAll = (...a) => {
        var sum = 0;
        for (var num of a) {
            sum = sum + num;
        }
    return sum;
    };
    
    addAll(1, 2, 3, 4, 5); // 15
    ```
* Block scope can be create with let
    ```javascript
    var fn = function () {
        var where = 'outer';
        {
            let where = 'inner';
        }
        console.log(where); // outer
        {
            var where = 'inner';
        }    
        console.log(where); // inner
    };
    
    fn();
    ```
* `var` hoisting: a variable can be declared after it has been used
     ```javascript
    console.log(x); // undefined
    x = 5;
    console.log(x); // 5
    var x = 6;
    console.log(x); // 6
    ```
* Variables and constants declared with `let` or `const` are not hoisted
* Currying is a transform of functions that translates a function from callable as f(a, b, c) into a callable as 
f(a)(b)(c)    
    ```javascript
    function curry(f) { // curry(f) does the currying transform
      return function(a) {
        return function(b) {
          return f(a, b);
        };
      };
    }
    
    // usage
    function sum(a, b) {
      return a + b;
    }
    
    let curriedSum = curry(sum);
    
    curriedSum(1)(2); // 3
    ```
* Example of using `reduce` [Run on JS Bin](https://jsbin.com/kolutan/edit?js,console)
<script src="https://gist.github.com/anuragkapur/4da97b7f87d6c25862412db8419d8916.js"></script>

# Callbacks, Higher Order Functions and Closures
* Function that takes in a function as an argument or returns a function is called a higher-order function
* Function that is passed as an argument is called a callback
* ES6 arrow functions don't have their own `this` binding like regular ES5 functions
    ```javascript
    const user = {
        name: 'Anurag',
        sayHi: () => {
            console.log(`ES6 :: Hi, I'm ${this.name}`);
        },
        sayHiAlt () {
            console.log(`ES5 :: Hi, I'm ${this.name}`);
        }    
     };
    
    user.sayHi(); // ES6 :: Hi, I'm
    user.sayHiAlt(); // ES5 :: Hi, I'm Anurag
    ```
* A **closure** is the combination of a function and the lexical environment (Persistent Lexical Scope Reference Data) 
within which that function was declared [Run on JS Bin](https://jsbin.com/lapuxoq/edit?js,console)
<script src="https://gist.github.com/anuragkapur/17426a23c922d66950c61001c52e811c.js"></script>
* [Additional examples of closures and higher order functions](http://csbin.io/closures)
* JS is a lexically (statically) scoped language
  * The word "lexical" refers to the fact that lexical scoping uses the location where a variable is declared within 
  the source code to determine where that variable is available
  * Nested functions have access to variables declared in their outer scope

# Asynchronicity
* Features like timer (setTimeout), HTML DOM (document), network requests (xhr / fetch), console are not core JS 
features, instead are provided by the web browser / engine that runs JS
  * Example: `setTimeout` is simply a facade function to call out functionality implemented by the runtime (say a web 
  browser)
* JS has a concurrency model based on an [event loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)
  * Facade functions (formally known as runtime APIs) call out to the functionality provided by the runtime
  * When the runtime has to pass a message back to JS execution context, it puts the message on a **callback queue**
  (aka the task queue)
    * Each message has an associated function which gets called in order to handle the message
  * The event loop continuously evaluates the state of the call stack and global execution context and if there is 
  nothing to process, picks a pending message (if any) from the callback queue and puts it on the call stack
  * Once the message from the runtime reaches the callback (via the callback queue) it is executed following standard
  JS execution rules
* [Asynchronicity examples](http://csbin.io/async)
* ES6 introduced promises as an alternative to callbacks
* **Promises** are two-pronged facade functions that both:
  * Initiate background work in the runtime (ex: web browser)
  * Return a placeholder object (promise) immediately in JavaScript
* Unlike promises, callbacks are limited in capability as they can only initiate the background but don't have a 
placeholder object that can be interrogated to know what's happening with the background task
* When a promise is fulfilled, the function passed to the promise object using the `then` method is pushed to the 
**microtask queue**
    ```javascript
    const futureData = fetch('http://something.com/somepath');
    futureData.then((data) => console.log(data));
    ```
* Event loop prioritises the microtask queue over the callback (or task) queue
    ```javascript
    function display(data) { console.log(data); }
    function printHello() { console.log("Hello"); }
    function blockFor300ms() { /* some computation, say an expensive for loop */ }
    
    setTimeout(printHello, 0);
    
    const futureData = fetch('https://twitter.com/anuragkapur/tweets/1');
    // let's assume the http request completes in less than 300ms, i.e. the promise if fulfilled in less than 300ms
    futureData.then(display);
    
    blockFor300ms();
    console.log("Me first!");
    
    /*
    Though the printHello function enters the callback queue before the display function enters the microtask queue, the 
    Event loop dequeues the display function and pushes it to the call stack before the printHello function  
    Console output:
    Me first!
    My tweet text
    Hello
    */
    ``` 

# Classes and Prototypes (OOP)
*  Objects    
    * Creating an empty object
    ```javascript
    const user1 = {};
    const user2 = Object.create(null);
    ```
* Object.create() method creates a new object, using an existing object as the prototype of the newly created object
    ```javascript
    const person = {
      isHuman: false,
      printIntroduction: function () {
        console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
      }
    };
    
    const me = Object.create(person);
    
    me.name = "Matthew"; // "name" is a property set on "me", but not on "person"
    me.isHuman = true; // inherited properties can be overwritten
    
    me.printIntroduction(); // "My name is Matthew. Am I human? true"
    ```  
* Properties and methods can be added to empty objects in the future
    ```javascript
    user1.name = "Foo";
    user1.score = 3;
    user1.increment = function () {
        user3.score ++;
    };
    ```
## Creating objects

### Approach 1: Using a function
*   ```javascript
    function userCreator(name, score) {
        const newUser = {};
        newUser.mame = name;
        newUser.score = score;
        newUser.increment = function () {
            newUser.score ++;
        };
        return newUser;
    }
    
    const user1 = userCreator("Foo", 3);
    const user2 = userCreator("Bar", 6);
    
    user1.increment(); // 4
    user2.increment(); // 7
    ```
* Problem: Each time we create a new user we allocate memory for all our data and functions. But functions are just
copies = memory wasted!
* Benefit: Simple and easy to reason about

### Approach 2: Using the prototype chain
* ```javascript
    function userCreator(name, score) {
        const newUser = Object.create(userFunctionStore);
        newUser.mame = name;
        newUser.score = score;
        newUser.increment = function () {
            newUser.score ++;
        };
        return newUser;
    }
    
    const userFunctionStore = {
        increment: function() {this.score++;},
        login: function() {console.log("Logged In");}
    };
    
    const user1 = userCreator("Foo", 3);
    const user2 = userCreator("Bar", 6);
    
    user1.increment(); // 4
    user2.increment(); // 7
    ```
* ![Prototype chain](/assets/blog/programming/js-prototype-chain.png)
* All objects have a `__proto__` property by default which defaults linking to a bug object - `Object.prototype`
* Benefit: function copies (`increment` and `login`) are not duplicated in memory
* Nested function (ES5 syntax and not the ES6 arrow function syntax) defined inside an object's method does not 
bind the `this` keyword to the object that the method binds to. However, nested ES6 functions, bind the `this` keyword 
to the **lexical scope** and thus behave differently, i.e. `this` keyword binds to the object defining the method 
containing the nested function. This is illustrated in the example below:
    ```javascript
    const user = {
        name: "Foo",
        score: 3,
        increment1: function() {
            function add1() {this.score++;}
    
            // `this` does not bind to the `user` object, instead binds to the global object which doesn't 
            // have property `score` defined on it
            add1();
            return this.score;
        },
        increment2: function() {
            function add1() {this.score++;}
            // calls add1 with this bound to the user object to have the desired effect of incrementing
            // score from 3 to 4
            add1.call(this); 
            return this.score;
        },
        increment3: function() {
            const add1 = () => {this.score++;};
            add1();
            return this.score;
        }  
    };
    
    console.log(user.increment1()); // 3
    console.log(user.increment1()); // 3
    console.log(user.increment1()); // 3
    console.log(user.increment2()); // 4
    console.log(user.increment2()); // 5
    console.log(user.increment2()); // 6
    console.log(user.increment3()); // 7
    console.log(user.increment3()); // 8
    console.log(user.increment3()); // 9
    ```
  * This is different to using arrow functions to define object methods - when arrow function is used to define object
  method, their `this` binds to the global scope and not the object. However, when arrow function is defined inside
  an object method (defined using the `function` keyword), the arrow function's `this` binds to the object and not
  global scope
  
### Approach 3: The `new` keyword
* When we call the function that returns an object with a `new` in front it automate 2 things:
  * Create a new object
  * Return the new object
*   ```javascript
    function userCreator(name, score) {
        this.name = name;
        this.score = score;
    }
    
    // arrow function won't do the job as its `this` will bind to the global context and not the object created by
    // userCreator
    userCreator.prototype.increment = function() {
        return ++this.score;    
    };
    
    const user1 = new userCreator("Foo", 5);
    console.log(user1.increment()); // 6
    ```   
* It's best practice to capitalise first letter of the function name that is meant to be used with the `new` keyword
  * If the function `userCreator` in example above is called without the new keyword it will end up adding properties
  `name` and `score` to the global scope instead of creating a new object with those properties and returning it

### Approach 4: The `class` syntactic sugar 
*   ```javascript
    class UserCreator {
        
        constructor(name, score) {
            this.name = name;
            this.score = score;
        }
        
        increment() { 
            return ++this.score;
        }
    
        login() {
            console.log("logged-in");
        }
    }
    
    const user1 = new UserCreator("Foo", 5);
    console.log(user1.increment()); // 6
    ```
* The `class` feature works exactly like approach 3, but its just cleaner as there is no need to separately define the
functions in the prototype property using `object.prototype`
* The above is strikingly similar to how classes (i.e. data + methods) work in other languages like Java
    
# References
* [JS: From Fundamentals to Functional JS - Day 1, by Bianca Gandolfo](https://slides.com/bgando/f2f-final-day-1#/)
* [JS: From Fundamentals to Functional JS - Day 2, by Bianca Gandolfo](https://slides.com/bgando/f2f-final-day-2#/)
* [JS: The Hard Parts, v2, by Will Sentance](https://frontendmasters.com/workshops/javascript-hard-parts-v2/)
