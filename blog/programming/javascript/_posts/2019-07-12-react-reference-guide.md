---
layout: post
title:  "React.js Reference Guide"
date:   2019-07-12 00:00:00 +0000   
categories: programming javascript reactjs
tags: programming
teaser: My React.js reference guide, created when taking courses, experimenting and coming across stuff during projects 
img-url: /assets/blog/programming/react.png
permalink: /blog/reactjs-reference-guide
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Fundamentals](#fundamentals)
- [Hooks](#hooks)
- [References](#references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->
# Fundamentals
* React is simply a JS library
* Hello, world react app, using pure react, i.e. just some JS on a page; Run on [JS Bin](https://jsbin.com/meqaroc/edit?html,output)
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Adopt Me</title>
    </head>
    
    <body>
      <div id="root">not rendered</div>
      <script src="https://unpkg.com/react@16.8.4/umd/react.development.js"></script>
      <script src="https://unpkg.com/react-dom@16.8.4/umd/react-dom.development.js"></script>
      <script>
        ReactDOM.render(React.createElement("h1", {}, "Hello, world!"), document.getElementById("root"));
      </script>
    </body>
    
    </html>
    ```
* **Props** are variable that a parent passes to its children
    ```javascript
    const Pet = props => {
      return React.createElement("div", {}, [
        React.createElement("h1", {}, props.name),
        React.createElement("h2", {}, props.animal),
        React.createElement("h2", {}, props.breed)
      ]);
    };
    
    const App = () => {
      return React.createElement("div", {}, [
        React.createElement(Pet, {
              name: "Pepper",
              animal: "Bird",
              breed: "Cockatiel"
            }),
        React.createElement(Pet, {
          name: "Luna",
          animal: "Dog",
          breed: "Havanese"
        })
      ]);
    }
    ```  
* Components are of two types
  * Class components
  * Function components
* **Function component**
  * Must return markup
  * Must be pure, i.e. have not side effects
  * Example of function component, [Run on JS Bin](https://jsbin.com/jeziteb/edit?html,js,output)
    ```javascript
    const App = (props) => {
        return React.createElement("h1", {}, props.message);
    };
    
    ReactDOM.render(React.createElement(App, {message: "Hello, world!"}), document.getElementById("root"));
    ```
  * `React.createElement` creates one instance of a component
  * In the example above, `App` is a _class_ of components and `React.createElement` creates an instance of the class
  passed to it as argument
* **Class component**
  * Extends `React.Component`
  * Have a render method that returns a react element
  * Example of a class component, [Run on JS Bin](https://jsbin.com/nolujap/edit?js,output)
  * Provide state and lifecycle methods for the component
  * State is private to the component
  * A component may choose to pass its state down as props to its child components
    ```html
    <h1>It is {this.state.foo}.</h1>
    ```
* All react component must act like pure functions with respect to their props
* Instead of pulling react library and other future dependencies from unpkg.com / similar CDN, it is better to download
it locally using npm and then package into the app bundle
    ```shell script
    npm install react react-dom
    ```
* Packer can bundle all dependencies from import statements in the src files
* JSX (JavaScript XML) is a syntax extension to JS
  * It is not HTML
  * Produces React elements
  * React doesn't require JSX, but makes writing UI code inside JS easier to read/write
  * `React.createElement("h1", { id: "main-title" }, "Hello, world!");` is equivalent to `<h1 id="main-title">Hello, world!</h1>`
  * JS expressions can be used within `{}` inside JSX code    
    ```
    <h1>{props.name}</h1>
    ```
* Handling HTML `form` elements
  * Whenever a DOM events happens, React thinks something may have changed and runs a re-render, overwriting any changes
  to a input text field initiated by a user. Ref: [Run on JS Bin](https://jsbin.com/suxoxo/edit?html,js,output)
    ```
    const SearchParams = () => {
      const location = "Seattle, WA";
      return (
        <div className="search-params">
          <form>
            <label htmlFor="location">
              Location
              <input id="location" value={location} placeholder="Location" />
            </label>
            <button>Submit</button>
          </form>
        </div>
      );
    };
    ```
  * These elements need to be handled using [Controlled Components](https://reactjs.org/docs/forms.html#controlled-components) 
  to allow a JS function to handle form submission and read the value of form elements beings submitted
    * Event handler methods in a controlled component need to be explicitly bound to the object's `this` because in JS,
    class methods are not bound by default as illustrates in 
    [MDN reference doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)
  * Alternatives to controlled components: [uncontrolled component](https://reactjs.org/docs/uncontrolled-components.html)
  where the form data is handled by the DOM instead of in the react state object
* [Strict Mode](https://reactjs.org/docs/strict-mode.html) can be enabled to highlight potential issues in a react app
* [Reach Router](https://reach.tech/router) is a new router from the creators of React Router  

# Hooks
* Introduced in React 16.8
* Allow using / "hooking into" state and component lifecycle without writing classes, i.e. from function components
* Do not put hooks inside if statement or loops because hooks rely on strict ordering of declaration  
* `useState` hook: for handling form elements, i.e state
    ```
    import React, { useState } from "react";
    
    const ExampleComponent = () => {
    const [location, setLocation] = useState("Seattle, WA");
      
    return(
      <input
          id="location"
          value={location}
          placeholder="Location"
          onChange={e => setLocation(e.target.value)}
      />
    )};
    ```
* `useEffect` hook: for hooking into component lifecycle methods that perform side effects
    ```
    const [count, setCount] = useState(0);
    
    // Similar to componentDidMount and componentDidUpdate:
    useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
    });
    ```

# References
* [https://reactjs.org/docs](https://reactjs.org/docs)
* [https://frontendmasters.com/courses/complete-react-v5/](https://frontendmasters.com/courses/complete-react-v5/)
  * [https://btholt.github.io/complete-intro-to-react-v5/](https://btholt.github.io/complete-intro-to-react-v5/)  