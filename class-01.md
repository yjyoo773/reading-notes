# Intro to React and Components

## React
A type of JavaScript library for building user interface.  
Can compose complex UIs from constructing small pieces of codes called components.

### JSX
JSX is a syntax extension for JavaScript which is used for React.
A simple example using JSX is  
  `let element = <h1>Hello World</h1>`
#### Features
- Can embed expressions
- Can be used as expressions
- Can contain children
- Prevents injection attacks
- Represents objects

### Rendering Elements in React
Elements: smallest building block of React apps

React elements are plain objects that are cheap to create. -> does not take up much data

#### Rendering an Element into DOM
In order to render elements into the DOM the HTML file should have a `<div id ="root"></div>`.  
This is the root DOM node where everything inside is managed by React DOM.  
  
Applications built with React tend to have one root node. However, when intergrating React into  
an existing application, there may exist several root nodes.
```JavaScript
const element = <h1> Hello, world </h1>
ReactDOM.render(element,document.getElementById('root'));
```

#### Updating Rendered Elements
React elements are immutable ==> cannot change attributes/children  
So in order update the UI, a new element must be created and passed to `ReactDOM.render()`
  
Example)
```JavaScript
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}
setInterval(tick, 1000);
```
(source: https://reactjs.org/docs/rendering-elements.html)
From the code above, `ReactDOM.render()` is called every second by the `setInterval()` callback.  
  
React only updates necessary parts from what is changed from the previous ReactDOM.  
By doing this, React scopes at how the UI looks at any given moment than how it changes or how the  
previous/next event affects the present. By doing so eliminates the possibilities of bugs.  

### Components and Props
Components: allows the UI to split into independent reusable pieces in React -> Similar to functions

#### Function and Class Components
In React's point of view using JavaScript function and ES6 class is the same.  
```JavaScript
function Welcome(x){
  return <h1>Welcome, {x.name} </h1>
  }

class Welcim extends React.Components{
  render(){
    return <h1>Welcome, {this.x.name} </h1>;
  }
}
```
The two above are equivalent.

#### Rendering Components
Just as React elements represent DOM tags, it can represent components created by users.  
Using the `Welcome` function,
```JavaScript
const element = <Welcome name="Tom"/>;
```
#### Composing Components
Components can refer to other components in their output. Similar to using a function within a function.  
Typically, React apps have a single `App` component at the very top running the application using a  
collection of components.  
#### Extracting Components
Sometimes a single component can get too long and complicated. In those cases it can be helpful to extract  
the component into smaller pieces. This is especially helpful if the broken down components are reusable in  
other places.
#### Note on Props
All React components must act like pure functions with respect to its props. Meaning, the component should never  
modify its own props.  
Example)
```JavaScript
function sum(a, b) {
  return a + b;
}
function withdraw(account, amount) {
  account.total -= amount;
}
```
(source: https://reactjs.org/docs/components-and-props.html)  
The `sum` function is considered pure because the returned value does not affect the input. On the other hand,  
`withdraw` function changes the `account.total` hence is an impure function.
