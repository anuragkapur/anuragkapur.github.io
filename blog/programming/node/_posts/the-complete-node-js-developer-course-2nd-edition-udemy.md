# Node.js Fundamentals

* Requiring your own files
```javascript
// uses relative paths
const notes = require('./notes.js'); 
```

* Module
  - available to all files
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
```
node --inspect-brk <filename>
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
  
# Testing Node Applications

http://mochajs.org/    
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
