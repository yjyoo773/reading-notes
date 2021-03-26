# Memory Storage

## JavaScript Call Stack

####Call Stack
used for function invocation(call) done synchronous. Or one at a time top to bottom.  
data stucture *last in first out*
```JavaScript
function firstFunction(){
  throw new Error('Stack Trace Error');
}
function secondFunction(){
  firstFunction();
}
function thirdFunction(){
  secondFunction();
}
thirdFunction();
```

![image](https://user-images.githubusercontent.com/60489495/112593758-3314b180-8dc5-11eb-8e0e-a5970afb2f5e.png) 
==> the `firstFunction()` is called last but returns the first.  

in Asynchronous JavaScript we have
- callback function: acted upon by the call stack during execution after the call back function has been pushed to the stack by the event loop
- event loop
- task queue

#### Temporarily Store
When a functions is called, the function and its parameters, and variables are pushed into the call stack to form a stack frame(memory location)
=> memory is cleared when function returns

#### Manage Function Invocation
Call stack maintains a record of the position of each stack frame; knowing the next function to be executed (and removced from stack) ==> makes JS synchronous

```JavaScript
function firstFunction(){
  console.log("Hello from firstFunction");
}

function secondFunction(){
  firstFunction();
  console.log("The end from secondFunction");
}

secondFunction();
// Hello from firstFunction
// The end from secondFunction
```
1. `secondFunction()` get executed and an empty stack frame is created => main entry point 
2. `secondFunction()` calls `firstFunction()` being pushed into stack on top of `secondFunction()`
3. `firstFunction()` is returned and prints
4. `firstFunction()` is popped out of stack
5. `secondFunction()` is executed and prints
6. `secondFunction()` pops out of stack

### Stack Overflow
When a recursive function has no exit point.
```JavaScript
function callMyself(){
  callMyself();
}
callMyself();
```

## JavaScript Error Messages and Debugging

### Types of Errors
#### Reference Error
Calling a variable that has not been declared.
```JavaScript
let a = 1
console.log(b) // Uncaught ReferenceError: b is not defined
```
Also not declaring variable type such as `let`, `const`, and `var` can also cause this error.

#### Syntax Errors
Occurs when you have something that cannot be parsed in terms of syntax.   
e.g parse an invalid object using JSON.parse
```JavaScript
JSON.parse( {'foo': 'bar'} ) // Uncaught SyntaxError: Unexpected token o in JSON at position 1
```
Solution:
```JavaScript
JSON.parse('{"foo":"bar"}')
```
#### Range Errors
Occurs when manipulating an object with a length of sort and give invalid length
```JavaScript
var foo= []
foo.length = foo.length -1 // Uncaught RangeError: Invalid array length
```
#### Type Errors
When the datatype trying to access is incompatible

### Debugging
- Set a breakpoint to check if code is working up to certain line.
- Add conditional breakpoints

### Handling Errors
Using a **try** to **catch** allows us to fallback to a default state of error in case of an error.

### Tools to Avoid Runtime Errors
Since JavaScript is not compiled language, the errors will happne at runtime meaning can only find errors after 
code is run.  
There are tools that help avoid
- quokka
- eslint
- TypeScript

source:
https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4/
https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c
