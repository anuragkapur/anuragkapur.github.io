---
layout: post
title:  "The Complete Node.js Developer Course"
date:   2019-04-28 14:00:00 +0000   
categories: programming javascript
tags: programming
teaser: Notes from the Node.js developer course offered by Andrew Mead on Udemy. 
img-url: /assets/blog/programming/node/UC-4QNQ9KI2.jpg
---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Introduction](#introduction)
- [Node.js Fundamentals](#nodejs-fundamentals)
- [Asynchronous Programming](#asynchronous-programming)
- [Web Server and Application Deployment](#web-server-and-application-deployment)
- [Testing Node Applications](#testing-node-applications)
- [MongoDB, Mongoose and Rest API](#mongodb-mongoose-and-rest-api)
- [Handling File Uploads](#handling-file-uploads)
- [Realtime Applications](#realtime-applications)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Introduction
Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O
model that makes it lightweight and efficient.

[Official Course PDF Guide](/assets/blog/programming/node/PDF-Guide-Node-Andrew-Mead-v3.pdf)    
[Official Documentation](https://nodejs.org/en/docs/)

JavaScript is a single threaded programming language. However, node.js uses other threads using C++ behind the scenes to
provide non-blocking capabilities such as handling callbacks and promises.

# Node.js Fundamentals

* Requiring your own files
```javascript
// uses relative paths
const notes = require('./notes.js'); 
```

* Module
  - available to all files
  - node uses CommonJS modules
```
$ node
> module
Module {
  id: '<repl>',
  exports: {},
  parent: undefined,
  filename: null,
  loaded: false,
  children: [],
  paths:
   [ '/Users/anuragkapur/tech-stuff/workspace/ak/anuragkapur.github.io/repl/node_modules',
     '/Users/anuragkapur/tech-stuff/workspace/ak/anuragkapur.github.io/node_modules',
     '/Users/anuragkapur/tech-stuff/workspace/ak/node_modules',
     '/Users/anuragkapur/tech-stuff/workspace/node_modules',
     '/Users/anuragkapur/tech-stuff/node_modules',
     '/Users/anuragkapur/node_modules',
     '/Users/node_modules',
     '/node_modules',
     '/Users/anuragkapur/.node_modules',
     '/Users/anuragkapur/.node_libraries',
     '/usr/local/lib/node' ] }
```  

* Exporting to module
```javascript
module.exports.age = 25;
```

```javascript
module.exports.addNote = () => {
    console.log('addNote');
}
```

```javascript
add = (a, b) => a + b;

square = x => x * x;

module.exports = {
  add,
  square
};
```

* String formatting with variables (ES6)
```javascript
console.log(`Sum of numbers = ${result}`);
```

* Initialise npm module
```
$ npm init
```

* Install npm module
```
npm install <package-name>

// save in package.json - done by default in npm version >= 5.0
npm install <package-name> --save

// install as a global utility - doesn't add to the project specific package.json
npm install <package-name> --global 

// install as a dev dependency only
npm install <package-name> --save-dev
```

* node_modules directory shouldn't be committed to git

* nodemon - dev utility to automatically restart app when there are code changes        
https://www.npmjs.com/package/nodemon 
  -  nodemon - doesn't watch template (hbs) files by default, include them using
  ```
  nodemon server.js -e js, hbs
  ```

* Accessing command line args
```javascript
process.argv 
```

* `==` vs `===`
`===` does not do type conversion before doing the comparison    
```
> if (2 == '2') console.log('equal'); else console.log('not');
equal
undefined
> if (2 === '2') console.log('equal'); else console.log('not');
not
```

* yargs - utility module to handle command line arg parsing
https://www.npmjs.com/package/yargs

* ES6 JSON variables can skip value if it is same as key
```json
{
  title: title,
  body: body
}
```
is same as 
```json
{
  title,
  body
}
```

* Debugging via command line
```
node inspect <filename>
```
  - `n` for next
  - `c` for continue
  - `repl` enter into repl at the current debug state
  - `debugger;` add this to application code to add a break point

* Debugging via chrome dev tools
Add `debugger` statement to relevant line of code to act as a break point,    
```
node inspect <filename>
```
Next, go to chrome://inspect

* ES6 arrow functions don't bind to the `this` keyword
```javascript
const user = {
    name: 'Anurag', 
    sayHi: () => {
        console.log(`Hi, I'm ${this.name}`);
    }
 }

user.sayHi();
```

Prints:    
Hi, I'm undefined    

Alternate to the above:
```javascript
const user = {
    name: 'Anurag',
    sayHi: () => {
        console.log(`Hi, I'm ${this.name}`);
    },
    sayHiAlt () {
        console.log(`Hi, I'm ${this.name}`);
    }
    
 }

user.sayHiAlt();
```

* Object Destructuring
```javascript
var user = {name: 'Anurag Kapur', location: 'London'};
var {name, location} = user;
```

* Working with time
https://momentjs.com/ 

# Asynchronous Programming

* All functions get added to call stack before execution
* Event loop pushes items from the Callback queue to the call stack, only when the call stack is empty 
* Promises provide clearer semantics and code readability compared to callbacks
```javascript
// typical callback usage
doWorkCallback((error, result) => {
   if (error) {
       return console.log(error);
   } 
   
   console.log(result);
});

// typical promise usage
doWOrkPromise.then((result) => {
   console.log(result); 
}).catch((error) => {
    console.log(error);
});
```
* Promise chaining instead of nesting
```javascript
add(1, 2).then((sum) => { 
    console.log(sum);  // Will print 3 return add(sum, 4)
    return add(sum, 4);
}).then((sum2) => {
    console.log(sum2); // Will print 7
}).catch((e) => {
    console.log(e);
});
```
* Async-Await - syntactic sugar over promises
```javascript
const doWork = async () => {
const sum = await add(1, 99) const sum2 = await add(sum, 50) const sum3 = await add(sum2, 3) return sum3
}
doWork().then((result) => {
    console.log('result', result)
}).catch((e) => {
    console.log('e', e)
})
```

# Web Server and Application Deployment

https://github.com/anuragkapur/udemy-node-web-server contains example code using the following:

* [Express](https://www.npmjs.com/package/express)
  - Middleware is called in order of declaration in the code
    - The files under `/public` are still rendered in the following code, even though we have setup the middleware
    to render a maintenance page in the code sample below:
    ```javascript
    const server = express();
   
    hbs.registerPartials(__dirname + '/views/partials');
    server.use(express.static('public'));
    server.set('view engine', 'hbs');
    // maintenance middleware
    server.use((req, res, next) => {
      res.render('maintenance.hbs', {
        pageTitle: 'Maintenance Page'
      });
    });
    ```
    To remedy this, simply move the call to `server.use(express.static('public'))` to after the maintenance middleware
    declaration.
* [Handlebars](https://www.npmjs.com/package/hbs)
  - Partials for sharing code across html templates, example for header/footer code
  - Helper functions   
* Express Middleware    
  - Like servlet filters in java
  ```javascript
  app.use((req, res, next) => {
    // do something useful with the req and/or res
    next();
  });
  ```
  
# Testing Node Applications

http://mochajs.org/    
https://jestjs.io/      
https://www.npmjs.com/package/supertest     
https://github.com/anuragkapur/udemy-node-tests

* Using `nodemon` to run tests automatically when a file changes
    ```
    nodemon --exec 'npm test'
    ```
    Or, add the following script to the `package.json` file
    ```json
    "test-watch": "nodemon --exec \"npm test\""
    ```
    and then in the bash shell,
    ```
    $ npm run test-watch
    ```

* Assertion library - [Expect](https://github.com/mjackson/expect)

* Testing async methods - using `done()`
```javascript
it('should square the number asynchronously', (done) => {
  utils.asyncSquare(3, (result) => {
    expect(result).toBe(9).toBeA('number');
    done();
  })
});
```

* [Supertest](https://github.com/visionmedia/supertest) - Express app testing library
```javascript
it('should get users and the response should contain expected user in users array', (done) => {
  request(app)
    .get('/users')
    .expect(200)
    .expect((response) => {
      expect(response.body).toInclude({
        name: 'Anurag Kapur',
        location: 'London'
      })
    })
    .end(done);
});
```

* Mocking node modules using jest - https://jestjs.io/docs/en/manual-mocks

* Spies for unit testing
    - [Rewire](https://www.npmjs.com/package/rewire)  
    ```javascript
    const rewire = require('rewire');
    const expect = require('expect');
    
    const app = rewire('./app');
    
    describe('App', () => {
    
      const db = {
        saveUser: expect.createSpy()
      };
      app.__set__('db', db);
    
      it('should call saveUser with user object', () => {
        const email = 'anurag@example.com';
        const password = 'password';
        app.handleSignup(email, password);
        expect(db.saveUser).toHaveBeenCalledWith({email, password});
      });
    });
    ```
    
# MongoDB, Mongoose and Rest API

* [MongoDB Node.js driver](https://mongodb.github.io/node-mongodb-native/)
* Object/Document relationships
```javascript
const Todo = mongoose.model('Todo', {
    description: {
        type: String,
        trim: true,
        required: true
    },
    owner: {
        type: mongoose.Schema.Types.ObjectId,
        required: true,
        ref: 'User'
    }
});

userSchema.virtual('todos', {
    ref: 'Todo',
    localField: '_id',
    foreignField: 'owner'
});

user.populate('todos').execPopulate();
```
* Add automatic timestamps to docs
```javascript
const todoSchema = new Schema(
    {
        description: {
            type: String,
            trim: true,
            required: true
        }
    }, {
        timestamps: true
    }
);

const Todo = mongoose.model('Todo', todoSchema);
```

# Handling File Uploads

* Express ecosystem library - [Multer](https://github.com/expressjs/multer)
* Sample code implemented - https://github.com/anuragkapur/udemy-node-todo-api/blob/106eec6ef6898a442ab4b85905b9e9fe9ea0183c/src/router/users.js#L81 

# Realtime Applications

https://github.com/anuragkapur/udemy-node-chat-app    

* On the client, `socket.emit` emits an event to the server. On the server, both `socket.emit` and `io.emit` can be 
used. `socket.emit` sends an event to that specific client, while `io.emit` sends an event to all connected clients.

* Events can be broadcasted from the server using `socket.broadcast.emit`. This event will get sent to all sockets 
except the one that broadcasted the event.
```javascript
io.on('connection', (socket) => {
    socket.broadcast.emit('message', 'A new user has joined!')
})
```

* Socket.io rooms
https://socket.io/docs/rooms-and-namespaces/#Rooms   
