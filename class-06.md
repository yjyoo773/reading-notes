# NODE.js

## `Node.js` is
- a JavaScript runtime built on Chrome's V8 JavaScript engine.
- an event-based, non-blocking, asynchronous I/O runtime that uses Google's V8 JavaScript engine and libuv library
==> A program we can use to execute JavaScript.

## Why Node?
- Node has excellent support for ES6 and beyond => able to use most modern syntax.
- No compatibility issues with different browsers.
- Lets run JavaScript on the server.

## `npm`
`npm` is a Node package manager. In order to install a package globally on the system add a `-g`.  
`npm install -g jshint`  

### Installing a Package Locally
By adding `--save`  after the desired package, it becomes saved as a project dependency.  
`npm install lodash --save`  

### `package.json`
A file where you store a list of packages you have used in order to use your application. By doing so, 
when other developers clone your project the packages needed will be installed accordingly.

### Node.js Execution Model
**Traditional server**
1. Spawn a thread to handle request
2. With other languages (PHP,Ruby) I/O operations block execution of your code
3. Operation complete
4. Code runs
==> server has to wait ofr database lookup to complete before next process

**Node.js**
1. New request comes in
2. Blocking I/O operation occurs
3. Register a callback before continuing  to process next event
4. When I/O operation finishes, server executes callback and continue original request.
==> Capable of handling a large number of simultaneous connections.

### Apps suit for Node.js
- Great for applications needing real-time interaction and collaborations. --> chatting, *CodeShare*
- Good fit for building APIs when handling numerous request that are I/O driven

## Pair Programming
- Driver: programmer typing --> handle mechanics of coding, text editting, switching files, version control
- Navigator: design big picture --> algorithm to code, scan typos and bugs, no code writing.

## Benefits of Pair Programming
Improves listening, spekaing, reading, writing
1. Greater Efficiency
2. Engaged Collaboration
3. Learning from peers
4. Social Skills
5. Job Interview Readiness
6. Work Environment Readiness
