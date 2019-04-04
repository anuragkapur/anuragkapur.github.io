Trying out JavaScript development coming from Java/Scala development world!

* Can't use absolute paths in imports in React.js - which feels quite messy `(../../../someImport.js)`
* Tooling / IDE support - not as rich as that for other languages, such as JVM based languages (based on using Idea 
Webstorm IDE; Better support with VS Code, but still not as rich as a strongly typed language like Java)
    - Node.js, using Webstorm, method signature autocompletion doesn't seem to always work, example: no IDE hints to 
    generate method signature for the `use()` and `set()` methods in the snippet below. This means, you either need to
    remember the method signature (boo! too many to remember) or leave the IDE to refer to the documentation (boo! 
    again).
    ```javascript
    const express = require('express');
    const server = express();
    server.use(express.static('public'));
    server.set('view engine', 'hbs');
    ```
    - Same with jest assertion methods, but this can be addressed using steps described here:
    https://intellij-support.jetbrains.com/hc/en-us/community/posts/115000357324-Get-rid-of-Unresolved-function-method-variable-warning-in-Jest-test-files
    ![](/assets/blog/programming/jest-expect-webstorm-settings.png)
    - Even for simple methods like `this._id.toString()` IDE support to know what methods you have available is missing,
    which means you need to know the API instead of relying on the IDE for help!
* Node.js express app - unhandled exception/error can cause the app to crash and your service will become unavailable.
With java, requests are handled by a non-main thread and an unhandled error in such a thread doesn't cause the entire
process to crash   
```
(node:21217) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 1)
(node:21217) [DEP0018] DeprecationWarning: Unhandled promise rejections are deprecated. In the future, promise rejections that are not handled will terminate the Node.js process with a non-zero exit code.
``` 
* Cryptic warning and error messages - not easy to know which part of the code base these may be coming from. Examples:
    - Caused by `mongoose.connect('mongodb://127.0.0.1:27017/TodoApi', {useNewUrlParser: true, new: true});` but no easy
    way of knowing this, especially in a large code base that you may not be the author of
    ```
    the options [new] is not supported
    ```
    - 
    ```
    (node:21577) DeprecationWarning: collection.ensureIndex is deprecated. Use createIndexes instead.
    ```


  
  