# Functional Programming
A programming paradigm - a style of building the structure and elements of computer programs - that treats
computation as the evaluation of mathematical functions and avoids changing-state and mutable data

## Pure Functions
- returns the same result if given the same arguments aka deterministic
- does not cause observable side effects  
* Reading Files is not pure because the file's content can change

### How to make a function pure
return the value 
```JavaScript
let counter = 1
const increaseCounter = (value) => value + 1;
increaseCounter(counter); // 2
console.log(counter); // 1
```
### Benefits of Pure Functions
code becomes easier to test

## Immutability
Immutable data: its state cannot change after being created. => must create new object with new value
```JavaScript
let list = [1, 2, 3, 4, 5];
let accumulator = 0;

function sum(list, accumulator) {
  if (list.length == 0) {
    return accumulator;
  }

  return sum(list.slice(1), accumulator + list[0]);
}

sum(list, accumulator); // 15
list; // [1, 2, 3, 4, 5]
accumulator; // 0
```
Using recursion which is calling the function itself as `sum` above is doing, the variables can be immutable.

### Referential Transparency
**pure functions + immutable data = referential transparency**

### Functions as First-Class Entities
=> functions are also treated as values and used as data
- refer functiuons from constants and variables
- pass functions as parameters to other functions
- return functionas as results from other functions

### Higher-Order Functions
- takes one or more functions as arguments
- returns a function as its result

==> `map`,`filter`,`reduce`  


## Refactoring JavaScript for Performance and Readability
Improving performance for functions: using a *hash function*  
*hash function: map a given key to a location in the hash table*
```JavaScript
// Unrefactored code

const URLstore = [];

function makeShort(URL) {
  const rndName = Math.random().toString(36).substring(2);
  URLstore.push({[rndName]: URL});
  return rndName;
}

function getLong(shortURL) {
  for (let i = 0; i < URLstore.length; i++) {
    if (URLstore[i].hasOwnProperty(shortURL) !== false) {
      return URLstore[i][shortURL];
    }
  }
}
```
```JavaScript
const URLstore = new Map(); // Change this to a Map

function makeShort(URL) {
  const rndName = Math.random().toString(36).substring(2);
  // Place the short URL into the Map as the key with the long URL as the value
  URLstore.set(rndName, URL);
  return rndName;
}

function getLong(shortURL) {
  // Leave the function early to avoid an unnecessary else statement
  if (URLstore.has(shortURL) === false) {
    throw 'Not in URLstore!';
  }
  return URLstore.get(shortURL); // Get the long URL out of the Map
}
```
### Strategies for Readability
#### Return early from functions
```JavaScript
function showProfile(user) {
  if (user.authenticated === true) {
    // ..
  }
}

// Refactor into ->

function showProfile(user) {
  // People often inline such checks
  if (user.authenticated === false) { return; }
  // Stay at the function indentation level, plus less brackets
}
```
#### Cache variables so functions can be easily read
``` JavaScript
function showProfile(user) {
  if (user.authenticated === true) {
    // ..
  }
}

// Refactor into ->

function showProfile(user) {
  // People often inline such checks
  if (user.authenticated === false) { return; }
  // Stay at the function indentation level, plus less brackets
}
Cache variables so functions can be read like sentences:
function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    for (let j = 0; j < continents[i].length; j++) {
      for (let k = 0; k < continents[i][j].tags.length; k++) {
        if (continents[i][j].tags[k] === name) {
          return continents[i][j].id;
        }
      }
    }
  }
}

// Refactor into ->

function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    const group = continents[i]; // This code becomes self-documenting
    for (let j = 0; j < group.length; j++) {
      const tags = group[j].tags;
      for (let k = 0; k < tags.length; k++) {
        if (tags[k] === name) {
          return group[j].id; // The core of this nasty loop is clearer to read
        }
      }
    }
  }
}
```
#### Check fro Web APIs before implementing own functionality
```JavaScript
function cacheBust(url) {
  return url.includes('?') === true ?
    `${url}&time=${Date.now()}` :
    `${url}?time=${Date.now()}`
}

// Refactor into ->

function cacheBust(url) {
  // This throws an error on invalid URL which stops undefined behaviour
  const urlObj = new URL(url);
  urlObj.searchParams.append('time', Date.now); // Easier to skim read
  return url.toString();
}
```
source:
- https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa
- https://dev.to/healeycodes/refactoring-javascript-for-performance-and-readability-with-examples-1hec
