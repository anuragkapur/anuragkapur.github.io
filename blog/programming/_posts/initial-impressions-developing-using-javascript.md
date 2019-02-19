Trying out JavaScript development coming from Java/Scala development world!

* Can't use absolute paths in imports in React.js - which feels quite messy `(../../../someImport.js)`
* Tooling / IDE support - not as rich as that for other languages, such as JVM based languages (based on using Idea 
Webstorm IDE)
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
    Same with jest assertion methods, but this can be addressed using steps described here:
    https://intellij-support.jetbrains.com/hc/en-us/community/posts/115000357324-Get-rid-of-Unresolved-function-method-variable-warning-in-Jest-test-files
    ![](/assets/blog/programming/jest-expect-webstorm-settings.png)
*     
  
  