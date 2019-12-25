---
layout: post
title:  "JavaScript Reference Guide"
date:   2019-02-2 00:00:00 +0000   
categories: programming javascript highlight
tags: programming
teaser: My JavaScript reference guide, created when taking courses, experimenting and coming across stuff during projects 
img-url: /assets/blog/programming/js.jpg
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Fundamentals](#fundamentals)
- [References](#references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Fundamentals
* What is functional programming?
  * FP is about verbs, while OOP is about nouns
  * Core tenant: pure functions don't have side effects which in turn makes the code easier to test
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
* for..in loop to iterate over keys of an object
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
    var obj = {
                name: "foo",
                age: 19,
                speak: function() {
                    console.log("ny name is ", this.name);
                }
            }
    
    // ES6
    var obj = {
                name: "foo",
                age: 19,
                speak() {
                    console.log("ny name is ", this.name);
                }
            }
    ```
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
* Spread operator - like varargs in java
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
* A **closure** is the combination of a function and the lexical environment within which that function was declared [Run on JS Bin](https://jsbin.com/lapuxoq/edit?js,console)
<script src="https://gist.github.com/anuragkapur/17426a23c922d66950c61001c52e811c.js"></script>
  
# References
* [JS: From Fundamentals to Functional JS - Day 1](https://slides.com/bgando/f2f-final-day-1#/)
* [JS: From Fundamentals to Functional JS - Day 2](https://slides.com/bgando/f2f-final-day-2#/)
