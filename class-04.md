# Forms 
Unlike default HTML, in React when submitting forms the page does not refresh. However, it is convenient to have a JS function that handles the submission of forms and has access
to the data the use inputs.

### Controlled Components
In react mutable state is kept in `state` and is updated with `setState()`.

```JavaScript
class NameForm extends React.Components{
  constructro(props){
    super(props);
    this.state = {value: ''}: // empty value
  }
  
  // When the function is called the state will change to the 
  // target value occured at event
  handleChange = (e) =>{
    this.setState({this.state.value : e.target.value}_;
  }
  
  // After state has changed alert what it has been chagned to
  handleSubmit = (e)=>{
    alert('Name was submitted: ' + this.state.value);
  }
  
  render(){
    return(
      <form onSubmit = {this.handleSubmit}> // when form submit call handleSubmit
        <label>
          Name:
          <input type ="text" value={this.state.value} onChange={this.handleChange}/>
        </label>
        <input type="submit" value="Submit"/>
      </form>
      );
   }
}
```
### textarea Tag
`<textarea>` uses a `value` attribute in React. Hence can create a form similar to a single-line input.
```JavaScript
constructor(props) {
    super(props);
    this.state = {
      value: 'Please write an essay about your favorite DOM element.'
    };
}
```
```JavaScript
 <form onSubmit={this.handleSubmit}>
        <label>
          Essay:
          <textarea value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
```
With the `this.state.value` in the constructer set with text, the text area starts with text in it.

### select Tag
`<select>` is used to create a drop-down list to choose from with `<options>` to create list items. By setting `<select value = {some.kind.of.value}` it will be the
root attribute for the `select` tag.

### Handling Multiple Inputs
When dealing with multple controlled `input` elements, using a `name` attribute to each element let the handler function choose what to do. The `name` attribute is
similar to `className` or `id` giving it identification. Based on the value of `event.target.name` the handler function would work accordingly.
```JavaScript
  handleInputChange(event) {
    const target = event.target;
    const value = target.type === 'checkbox' ? target.checked : target.value;
    const name = target.name; // based on the target.name it sets the state below

    this.setState({
      [name]: value
    });
  }
```
### Controlled Input Null Value
Specifying the value prop to be a value rather than undefined or null can prevent the user from changing the input unless desired so. If you’ve specified a value but
the input is still editable, you may have accidentally set value to undefined or null.
```JavaScript
ReactDOM.render(<input value="hi" />, mountNode);

setTimeout(function() {
  ReactDOM.render(<input value={null} />, mountNode); // when value is null creates short delay
}, 1000);
```
