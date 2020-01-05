---
layout: post
title:  "TypeScript Reference Guide"
date:   2019-05-27 00:00:00 +0000   
categories: programming javascript highlight
tags: programming
teaser: My TypeScript reference guide, created when taking courses, experimenting and coming across stuff during projects 
img-url: /assets/blog/programming/ts.png
permalink: /blog/ts-reference-guide
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Fundamentals](#fundamentals)
  - [Basic Types](#basic-types)
  - [Function Basics](#function-basics)
  - [Interfaces and Type Aliases](#interfaces-and-type-aliases)
  - [Classes](#classes)
- [Generics](#generics)
- [Type Guards](#type-guards)
- [Advanced Types](#advanced-types)
- [References](#references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Fundamentals
* Typescript is a types, syntactic superset of JavaScript, developed by Microsoft
* Compiles to JavaScript and doesn't have its own runtime, i.e. can be thought of as a static type analysis tool
* TypeScript uses a **structurally typed** system (focused on the _shape_ that values have) as opposed to languages 
like Java and C++ that use a **nominally typed** system (focused on the _name_ that values have)
    ```typescript
    class Foo { method(input: string) { /* ... */ } }
    class Bar { method(input: string) { /* ... */ } }
    
    let foo: Foo = new Bar(); // 🚨 Error in a nominally typed language, but OK in a structurally typed language
    ```
  * References:
    * [https://flow.org/en/docs/lang/nominal-structural/](https://flow.org/en/docs/lang/nominal-structural/)
    * [https://www.typescriptlang.org/docs/handbook/type-compatibility.html](https://www.typescriptlang.org/docs/handbook/type-compatibility.html)  
* To show inferred type in WebStorm: `Command + hover on variable`
* Compile typescript code
    ```
    # Compiles to ES3 target, i.e. JS that is compatible with IE6
    tsc src/index.ts
  
    # Compiles to ES6 (ES2015)
    tsc src/index.ts --target ES2015
  
    # Compules to ES2015 and uses commonjs (used by node) modules
    tsc src/index.ts --target ES2015 --module commonjs
    ```
  * Ref: [TS Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)  
* Conventional way to set compiler flags is to use a file called [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)
  * Example
    ```json
    {
    "compilerOptions": {
      "module": "commonjs",
      "target": "es2017",
      "outDir": "lib",
      "declaration": true,
      "sourceMap": true
    },
    "include": ["src"]
    }
    ```
* Utility for testing types: [https://github.com/Microsoft/dtslint](https://github.com/Microsoft/dtslint)
    
## Basic Types 
* Variables with type `any`
    ```typescript
    let z; // Variable 'z' implicitly has an 'any' type, but a better type may be inferred from usage.
    z = 41;
    z = "abc";
    
    // we could improve this situation by providing a type annotation when we declare our variable
    let zz: number;
    zz = 41;
    zz = "abc"; // 🚨 ERROR Type 'abc' is not assignable to type 'number'.
    ```
* Array type
    ```typescript
    let aa: number[] = [];
    aa.push(33);
    aa.push("abc"); // 🚨 ERROR: Argument of type '"abc"' is not assignable to parameter of type 'number'.
    
    // The following means bb is an array of `never` and hence no elements of any type can be pushed to the array
    let bb = [];
    bb.push(44); // 🚨 ERROR: Argument of type '33' is not assignable to parameter of type 'never'.
    ```
* Tuple (array of fixed length) type
    ```typescript
    let cc: [number, string, string, number] = [
      123,
      "Fake Street",
      "Nowhere, USA",
      10110
    ];
    
    // we don't get any type safety when using push with a tuple and hence the below should be avoided with a tuple
    // in this example, the push method accepts element whose type matches `string | number`
    cc.push(1, 2, 3, 4);
    ```  
* Tuple values should always have a type annotation so that the type system doesn't consider the variable as a regular
array
    ```typescript
    const xx = [32, 31]; // type: number[];
    const yy: [number, number] = [32, 31]; // type: [number, number]
    ```  
* Object types
    ```typescript
    let cc: { houseNumber: number; streetName: string };
    cc = {
      streetName: "Fake Street",
      houseNumber: 123
    };
    
    cc = {
      houseNumber: 33
    };
    /**
     * 🚨 Property 'streetName'
     * 🚨   is missing in type   '{ houseNumber: number; }'
     * 🚨   but required in type '{ houseNumber: number; streetName: string; }'.
     */
    ```
* Object types with optional params
    ```typescript
    let dd: { houseNumber: number; streetName?: string };
    dd = {
      houseNumber: 33
    };
    ```
* Interface types    
    ```typescript
    interface Address {
          houseNumber: number;
          streetName?: string;
    }
    let ee: Address = { houseNumber: 33 };
    ```                   

## Function Basics
* Params and return values can have type annotations
    ```typescript
    interface HasPhoneNumber {
      name: string;
      phone: number;
    }
    
    interface HasEmail {
      name: string;
      email: string;
    }
    
    function sendEmail(to: HasEmail): { recipient: string; body: string } {
      return {
        recipient: `${to.name} <${to.email}>`,
        body: "Hello, world!"
      };
    }
    ```
* Overloaded function signatures
    ```typescript
    interface HasPhoneNumber {
      name: string;
      phone: number;
    }
    
    interface HasEmail {
      name: string;
      email: string;
    }
    
    function contactPeople(method: "email", ...people: HasEmail[]): void;
    function contactPeople(method: "phone", ...people: HasPhoneNumber[]): void;
    
    // "function implementation"
    function contactPeople(
      method: "email" | "phone",
      ...people: (HasEmail | HasPhoneNumber)[]
    ): void {
      if (method === "email") {
        (people as HasEmail[]).forEach(sendEmail);
      } else {
        (people as HasPhoneNumber[]).forEach(sendTextMessage);
      }
    }
    
    // ✅ email works
    contactPeople("email", { name: "foo", email: "" });
    
    // ✅ phone works
    contactPeople("phone", { name: "foo", phone: 12345678 });
    
    // 🚨 mixing does not work
    contactPeople("email", { name: "foo", phone: 12345678 });
    ```      
* To prevent confusion over what `this` might be bound to, it is best to always explicitly specify the type of `this`
argument the function expects
* Additionally, the `--noImplicitThis` warns if the type of `this` is `any`. Example:
    ```typescript
    // With the `--noImplicitThis` compiler flag set
    function sendMessage(
      preferredMethod: "phone" | "email"
    ) {
      if (preferredMethod === "email") {
        console.log("sendEmail");
        sendEmail(this); // 🚨 'this' implicitly has type 'any' because it does not have a type annotation.
      } else {
        console.log("sendTextMessage");
        sendTextMessage(this); // 🚨 'this' implicitly has type 'any' because it does not have a type annotation.
      }
    }
    ```
* Explicitly specifying the type of `this`
    ```typescript
    function sendMessage(
      this: HasEmail & HasPhoneNumber,
      preferredMethod: "phone" | "email"
    ) {
      if (preferredMethod === "email") {
        console.log("sendEmail");
        sendEmail(this);
      } else {
        console.log("sendTextMessage");
        sendTextMessage(this);
      }
    }
    ```
* With the type of `this` explicitly specified, the compiler points out any scope binding issues
    ```typescript
    // ...sendMessage as defined in the previous snippet
    
    // 🚨 The 'this' context of type 'void' is not assignable to method's 'this' of type 'HasEmail & HasPhoneNumber'.
    sendMessage("email");
    
    // ✅ creating a bound function is one solution
    sendMessage.bind(c, "email");
    
    // ✅ call/apply works as well
    sendMessage.apply(c, ["phone"]);
    ```

## Interfaces and Type Aliases
* Type aliases allow us to give a type a name
    ```typescript
    type StringOrNumber = string | number;
    type HasName = {name: string};
    ```
* Types don't allow self references as the TS compiler evaluates types, inline/eagerly as it parses through the code line by 
line as opposed to interfaces which are evaluated lazily
    ```typescript
    // 🚨 self-referencing types don't work!
    type NumVal = 1 | 2 | 3 | NumArr;
    // type NumArr = Numval[]; // Cannot find name 'Numval'.
  
    // ✅ this can be made to work by using an interface
    interface NumArr extends Array<NumVal> {}
    const x: NumVal = [1, 2, 3, 1, 1, [3, 1, 1, 2]];
    
    // 🚨 Initializer type 4 is not assignable to variable type NumVal 
    const y: NumVal = 4;
    ```  
* Interfaces can extend from other interfaces
    ```typescript
    interface HasPhoneNumber {
      name: string;
      phone: number;
    }
  
    interface HasInternationalPhoneNumber extends HasPhoneNumber {
      countryCode: string;
    }
    ```
* Readonly properties
    ```typescript
    interface Point {
        readonly x: number;
        readonly y: number;
    }
    
    let p1: Point = { x: 10, y: 20 };
    p1.x = 5; // 🚨 Attempt to assign to const or readonly variable 
    ```  
* Readonly arrays
    ```typescript
    let a: number[] = [1, 2, 3, 4];
    let ro: ReadonlyArray<number> = a;
    ro[0] = 12; // error!
    ro.push(5); // error!
    ro.length = 100; // error!
    a = ro; // error!
    ```
* Readonly is like const, but for object properties
* Interfaces can describe objects, functions, arrays, i.e. everything that is an object (functions and arrays are 
objects in JS), but not primitives
* Type aliases are flexible and can handle everything interfaces handle plus primitives
* Typing function signatures
    ```typescript
    // using an interface
    interface ContactMessenger1 {
      (contact: HasEmail | HasPhoneNumber, message: string): void;
    }
    
    // equivalent signature type using a type alias
    type ContactMessenger2 = (
      contact: HasEmail | HasPhoneNumber,
      message: string
    ) => void;
  
    // using a function signature
    const emailer: ContactMessenger1 = (_contact, _message) => {
      /** ... */
    };
    ```
* Typing constructor signatures
    ```typescript
    interface ContactConstructor {
      new (...args: any[]): HasEmail | HasPhoneNumber;
    }
    ```
* Excess property checks: if an object literal has any properties that the “target type” doesn’t have, you’ll get an 
error, but this doesn't apply to object variables
    ```typescript
    interface SquareConfig {
        color?: string;
        width?: number;
    }
    
    function createSquare(config: SquareConfig): { color: string; area: number } {
        // ...
        return {color: "bla", area: 100}; 
    }
    // 🚨Argument type {colour: string, width: number} is not assignable to parameter type SquareConfig
    let mySquare = createSquare({ colour: "red", width: 100 }); 
    
    // ✅ Excess property checks only apply to object literals and not object variables
    let mySquareConfig = { colour: "red", width: 100 };
    mySquare = createSquare(mySquareConfig);
    ```
* Index types
    ```typescript
    interface StringArray {
        [index: number]: string;
    }
    
    let myArray: StringArray;
    myArray = ["Bob", "Fred"];
    
    let myStr: string = myArray[0];
    
    interface NumberOrStringDictionary {
        [index: string]: number | string;
        length: number;    // ok, length is a number
        name: string;      // ok, name is a string
    }
    
    let myDict : NumberOrStringDictionary = {length: 1, name: "abc"};
    myDict = {length: 1}; // 🚨Assigned expression type {length: number} is not assignable to type NumberOrStringDictionary 
    ```
* Declaration merging - interfaces are "open", meaning any declarations of the same name are merged
    ```typescript
    interface PhoneNumberDict {  
        [thisCanBeAnythingItsIgnoredOnlyTypeIsImportant: string]:
            | undefined
            | {
            areaCode: number;
            num: number;
        };
    }
    
    interface PhoneNumberDict {
        home: {
            areaCode: number;
            num: number;
        };
        office: {
            areaCode: number;
            num: number;
        };
    }
    
    const phoneDict: PhoneNumberDict = {
      
        // office and home are mandatory because of the 2nd interface declaration
        office: { areaCode: 321, num: 5551212 },
        home: { areaCode: 321, num: 5550010 },
        
        // this is allowed due to the first interface declaration
        iphone: { areaCode: 321, num: 5550010 }
    };
    
    phoneDict.home; // definitely present
    phoneDict.office; // definitely present
    phoneDict.mobile; // MAYBE present
    ```

## Classes
* Classes implement interfaces and can use parameter properties shorthand
    ```typescript
    interface HasEmail {
      name: string;
      email: string;
    }
    
    class Contact implements HasEmail {
      email: string;
      name: string;
      constructor(name: string, email: string) {
        this.email = email;
        this.name = name;
      }
    }
    
    // This is a short-hand using `parameter properties` that is exactly same as the previous more verbose definition
    class ParamPropContact implements HasEmail {
      constructor(public name: string, public email: string) {
        // nothing needed
      }
    }
    ```

# Generics
* Parameterize types
    ```typescript
    interface WrappedValue<X> {
      value: X;
    }
    
    let val: WrappedValue<string> = { value: "" };
    ```
* You don't have to use exactly your type parameter as an arg, instead things that are based on your type parameter are
fine too
    ```typescript
    function resolveOrTimeout<T>(promise: Promise<T>, timeout: number): Promise<T> {
      return new Promise<T>((resolve, reject) => {
        // start the timeout, reject when it triggers
        const task = setTimeout(() => reject("time up!"), timeout);
    
        promise.then(val => {
          // cancel the timeout
          clearTimeout(task);
    
          // resolve with the value
          resolve(val);
        });
      });
    }
    
    // Resolves T as Response, based on argument `fetch` which returns a Promise<Response>
    resolveOrTimeout(fetch(""), 3000);
    ```
* Type params can use inheritance constructs
    ```typescript
    function foo<T extends { id: string }>(param1: T): T {
        //...
        return param1;
    }
    ```
* Type params are associated with scopes, just like function arguments
    ```typescript
    function startTuple<T>(a: T) {
      return function finishTuple<U>(b: U) {
        return [a, b] as [T, U];
      };
    }

    // type of `myTuple` is `[string[], number]`            
    const myTuple = startTuple(["first"])(42);
    ```  
* Its best to use generics when we want to describe a relationship between two or more types, example, a function 
argument and return type
  * Its an overkill to use Generics in the following scenario
    ```typescript
    type Shape = {
      draw();
    };
    interface Circle extends Shape {
      radius: number;
    }
    
    function drawShapes1<S extends Shape>(shapes: S[]) {
      return shapes.map(s => {
        s.draw();
      });
    }
    
    // Its simpler and equivalent to just use the following
    function drawShapes2(shapes: Shape[]) {
      shapes.forEach(s => s.draw());
    }
    ```
  * Its useful to use Generics in the following scenario, to link the type of function arg and its return type
    ```typescript
    type Shape = {
      draw();
      isDrawn: boolean;
    };
    interface Circle extends Shape {
      radius: number;
    }
    
    function drawShapes1<S extends Shape>(shapes: S[]): S[] {
      return shapes.map(s => {
        s.draw();
        s.isDrawn = true;
        return s;
      });
    }
    
    const cir: Circle = { draw() {}, radius: 4, isDrawn: false };
    drawShapes1([cir]).map(c => c.isDrawn);
    ```        

# Type Guards
* Typescript has two top types - `any` and `unknown`
* `unknown`s need to be narrowed using a type guard before they can be used
    ```typescript
    let myUnknown: unknown = "hello, unknown";
    
    if (typeof myUnknown === "string") {
      // in here, myUnknown is of type string
      myUnknown.split(", "); // ✅ OK
    }
    if (myUnknown instanceof Promise) {
      // in here, myUnknown is of type Promise<any>
      myUnknown.then(x => console.log(x));
    }
    ```
* User defined type guards
    ```typescript
    function isHasEmail(x: any): x is HasEmail {
      return typeof x.name === "string" && typeof x.email === "string";
    }
    
    if (isHasEmail(myUnknown)) {
      // In here, myUnknown is of type HasEmail
      console.log(myUnknown.name, myUnknown.email);
    }
    
    function isDefined<T>(arg: T | undefined): arg is T {
      return typeof arg !== "undefined";
    }
    const list = ['a', 'b', undefined, 'c'];
    const filtered = list.filter(isDefined);
    ```
  
# Advanced Types
* **Mapped Types** allow the use of an interface to transform keys into values
    ```typescript
    interface CommunicationMethods {
      email: HasEmail;
      phone: HasPhoneNumber;
      fax: { fax: number };
    }
    
    function contact<K extends keyof CommunicationMethods>(
      method: K,
      contact: CommunicationMethods[K] // 💡turning key into value -- a *mapped type*
    ) {
      //...
    }
    contact("email", { name: "foo", email: "mike@example.com" });
    contact("phone", { name: "foo", phone: 3213332222 });
    contact("fax", { fax: 1231 });
    
    // we can get all values by mapping through all keys
    type AllCommKeys = keyof CommunicationMethods;
    type AllCommValues = CommunicationMethods[keyof CommunicationMethods];
    ```   
* Partial allows us to make all properties on on object optional
    ```typescript
    type MayHaveEmail = Partial<HasEmail>;
    const me: MayHaveEmail = {}; // everything is optional
    ```
* `Extract` and `Exclude` allows us to obtain a subset of types from given types
    ```typescript
    type OnlyStrings = Extract<"a" | "b" | 1 | 2, number>; // type OnlyStrings = "a" | "b"
    type NotStrings = Exclude<"a" | "b" | 1 | 2, string>; // type NotStrings = 1 | 2
    ```
 
# References
* [TypeScript Fundamentals, Mike North](https://drive.google.com/file/d/170oHzpLNeprUa-TMmOAnSU4caEFDSb3e/view)
  * [https://github.com/mike-works/typescript-fundamentals/tree/v2-fem](https://github.com/mike-works/typescript-fundamentals/tree/v2-fem)