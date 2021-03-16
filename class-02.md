# State and Props

## State and Lifecycle
### State
An instance of React Component Class and can be defined as
an object of a set of **observable** properties that control the behaviour of the component

### State vs Props
- Props are immutable i.e. once set the props cannot be changed, while State is an observable
object that is to be used to hold data that may change over time and to control the behavior after each change.
- States can only be used in Class Components while Props don’t have this limitation.
- While Props are set by the parent component, State is generally updated by event handlers.

### Convert Function to Class
1. Create ES6 with same name from function + `extends React.Component`
2. Add a single empty method called `render()`
3. Move the body of the function into `render()`
4. Replace `props` with `this.props` in `render()`
5. Delete remaining empty function declaration

```JavaScript
function Clock(props){
  return (
    <div>
      <h1>Hello World</h1>
      <h2>It is {props.date.toLocaleTimeString()}.</h2>
    </div>
  );
}
```
Converting the above becomes
```JavaScript
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

### Add Local State to Class
1. Change the `this.props.date` into `this.state.date`
2. Add a class contstructor assigning the initial `this.state`
    *note `prop` is passed in the base constructor*
3. Remove `date` prop from the `<Clock />` element.
``` JavaScript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```
### Adding Lifecycle Methods to Class
#### Mounting
Setting up a timer with `setInterval` when class is rendered to the DOM for the first time.
```JavaScript
componentDidMount(){
  this.timerID = setInterval(
  () => this.tick(),
  1000
  );
 }
 ```
#### Unmounting
Clearing the set up timer with `clearInterval` whenever the DOM produced by class is removed.
```JavaScript
  componentWillUnmount() {
    clearInterval(this.timerID);
  }
```
We can use `this.setState()` to update the component local state such as
```JavaScript
tick(){
  this.setState({date: new Date()});
}
```
### Using State Correctly
- **Do Not Modify State Directly**
  use `this.setState() to modify state
- **State updates are asynchronous**
  do not rely using `this.props` and `this.state` values when calculating.  
  ==> If needed accept a function rather than an object
- **State updates are merged**
  If state contatins several independent variables, can update them independentyl with seperate `setState()`
  
## Handling Events
### Syntax
- React events are named using camelcasing
- Pass a function for event handler in JSX
- Call `preventDefault()` to prevent default behavior instead of returning `false`
- When using `this` since class methods are not bound need to manually bind them  
OR use arrow functions in the callback
- For ES6 class, the eventhandler is a method in class
```JavaScript
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {isToggleOn: true};

    // This binding is necessary to make `this` work in the callback
    this.handleClick = this.handleClick.bind(this);
  }
  // Using camelcasing and a method in class
  handleClick() {
    this.setState(state => ({
      isToggleOn: !state.isToggleOn
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}
```
### Passing Arguments to Event Handlers
In side a loop, it is commont to pass an extra parameter to the event handler.  
Can use `this.method.bind` or an arrow function
```JavaScript
<button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>
<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
```

## Conditional Rendering
Rendering distinct components based on the state of the application.  
==> Using conditional statements such as `if` and `else`.

### Element Variables
We can use variables to store elements. Based on the condition we can render elements conditionally
rendering without changing the rest of the output.

### Inline If with Logical && Operator
- If the statement is `true && expression` the expression after the && appears.
- If the statement is `false && expresssion` the expression after the && is skipped.

### Inline If-Else with Conditional Operator
We can conditionally render elements using `condition ? true : false`. Meaning based on the condition either true or false is returned.

### Preventing Component from Rendering
In cases we want to hide the component even when rendered by another component ===> return `null` to prevent it from showing.
source:
- https://reactjs.org/docs/state-and-lifecycle.html
- https://www.geeksforgeeks.org/reactjs-state-react/#:~:text=What%20is%20State%3F,the%20lifetime%20of%20the%20component.
- https://reactjs.org/docs/handling-events.html
- https://reactjs.org/docs/conditional-rendering.html
