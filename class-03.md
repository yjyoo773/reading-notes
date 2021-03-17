# Passing Functions as Props

## Lifting State Up
When several components reflect same changing data "lift shared state" up to closest common ancestor  
### Sharing state 
1. Move state that needs same changing data to the closest common ancestor component.
2. Change the local state from the decesendant component into a props.
*Example*
```JavaScript
const temperature = this.state.temperature
// Changes into
const temperature = this.props.temperature
```
3. Change `this.setState` as props.
```JavaScript
handleChange(e) {
  this.setState({temperature:e.target.value});
}
// Changes into
handleChange(e) {
  this.props.onChangeTemp(e.target.value);
}
```
  **By doing so the props are now controlled by the ancestor component and decesendants have no control**
  
4. Change the parent/ancestor components accordingly to states.

*Hence after finding the common ancestor, create states that correspond to the decesendants and have those states flow down as props to them.

## List and Keys

### Rendering Multiple Components
1. Loop through array using `map()`
2. Return each element inside `<li>`
3. Assignt the resulting array a name such as `listings`
4. Include the result array inside `<ul>` and render in DOM
```JavaScript
ReactDOM.render(
  <ul>{listings}</ul>,
  document.getElementById('root')
);
```

### Basic List Components
When rendering lists inside a components, a key is needed. A *key* is a string attribute that gives the element an identity.
```JavaScript
  <li key={number.toString()}>
      {number}
  </li>
 ```
 
 ### Keys
 When assigning keys, the best way is to give it a string that uniquey identifies the list item.
 Attributes such as `id` is ideal. However, if that is not possible as a last resort the index of the item can be used.
 ```JavaScript
 const todoItems = todos.map((todo) =>
  <li key={todo.id}>
    {todo.text}
  </li>
);
```

### Extracting Components with Keys
When extracting keys keep keys on the components elements rather than on the `<li>` element
*Bad Example*
```JavaScript
<li key={value.toString()}>
  {value}
</li>
```
*Correct Example*
```JavaScript
function ListItem(props) {
  return <li>{props.value}</li>;
}
const listItems = numbers.map((number) =>
  <ListItem key={number.toString()} value={number} />
);
```
As a rule of thumb put keys where `map()` calls.

**Keys must be unique among siblings**

## Spread Operator (...)
When `...arr` is used in a function call it expands the object `arr`
```JavaScript
const x = ['a','b','c']
[...x] //=> [abc]
```
Spread Operators can be used in several ways.
### Copy Array
`const nums = [1,2,3]` and `const nums2 = [...nums]`
`nums` and `nums2` are identical

### Concat Array
```JavaScript
const arr1 =['a','b']
const arr2 = ['1','2']
const arr3 = [...arr1,...arr2] // ['a','b','1','2']
```

### Use Math Function
```JavaScript
Math.max(1,2,3) // 5
Math.max([1,2,3]) // NaN
Math.max(...[1,2,3]) // 5
```

### Use Array As Argument
By spreading an array, a function that accepts multiple arguments can benenfit from it.

### Combining Objects
```JavaScript
const objectOne = {hello: "🤪"}
const objectTwo = {world: "🐻"}
const objectThree = {...objectOne, ...objectTwo, laugh: "😂"} // { hello: "🤪", world: "🐻", laugh: "😂" }
```

### Convert NodeList into Array

### Adding to State in React

source:
- https://reactjs.org/docs/lifting-state-up.html
- https://reactjs.org/docs/lists-and-keys.html
- https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab
