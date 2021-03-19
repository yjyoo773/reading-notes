# Thinking in React
Process of creating an app

## 1. Break the UI into a Component Hierarchy
- Draw boxes around every component and subcomponent
- Give those boxes names
- A component should do only one thing

## 2. Build a Static Version in React
- Implement the app by building a version of the outline created with no interactivity
- Build components that reuse other components and pass data using *props*
- Do not use `state` at this part of building the static version
- For simple projects its easy to build from top to bottom
- For complex projects its easier to build from bottom to top

## 3. Identify the Minimal Representation of UI State
- Think of the minimal set of mutable state that the app needs
- **Don't Repeat Yourself**
- Find the absolute minimal representation of the state the application needs -> ompute everything else
For example)  
When creating a TODO list, keep an array of the TODO items around. ==> do not seperate state variable

*Things to keep in mind if data is state*
- Is it passed in from parent via props? --> not state
- Does it remain unchanged over time? --> not state
- Can you compute it based on any other state or props in your component? --> not state

## 4. Identify Where Your State Should Live
It is one of the most challenging parts creating an app. --> where to place the state  
*Finding where the state should be*
1. Identify every component that renders something based on that state
2. Find a common owner component
3. Either the common owner or anothr component higher up in the hierarchy should own the state
4. If you can’t find a component where it makes sense to own the state, create a new component
solely for holding the state and add it somewhere in the hierarchy above the common owner component.

## 5.Add Inverse Data Flow
- Now that `props` & `state` are flowing down hierarchy support data flowing opposite direction
- Use a callback function that pass from parent to child component to update state of parent component.
