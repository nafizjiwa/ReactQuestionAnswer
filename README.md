# ReactQuestionAnswer
## What is React?
React is a JS library for SPA's (single page applications)

## Advantage of React?
Uses a Virtual DOM (virtual representation of the real DOM) to render the view. </br> 
Each time the data changes in a react app, a new virtual DOM gets created. Creating a virtual DOM is much faster than rendering the UI inside the browser.</br>

## REACT
1. Why do we need to `import React from "react"` in our files?</br>
React defines JSX. JSX is a syntax extension that looks like HTML but is actually JavaScript. </br>
JSX gets transformed into React.createElement() calls, which React uses to create and manage virtual DOM elements.</br>

2. If I were to console.log(page) in index.js, what would show up?</br>
Page refers to a JavaScript object containing React elements that describe the structure and content of the UI that React will eventually render to real DOM.</br>

3. What's wrong with this code:</br>
```
const page = (
   <h1>Hello</h1>
   <p>This is my website!</p>
)
```
We need our JSX to be nested under a single parent element. </br>

        const page = (
            <div> ----> Parent
                <h1>Hello</h1> ----> Child
                <p>This is my website!</p> -----> Child
            </div>
        )


4. What does it mean for something to be "declarative" instead of "imperative"?</br>

   `Declarative` means I can tell the computer WHAT to do </br>
   and expect it to handle the details.</br>
   `Imperative` means I need to tell it HOW to do each step.</br>

5. What does it mean for something to be "composable"?</br>

   We have small pieces that we can put together to make something</br>
   larger/greater than the individual pieces.</br>

6. How is JSX is transpiled?</br>

By Babel, it's converted into standard JavaScript using React.createElement()</br>
Each JSX element becomes a React.createElement call:</br>
React.createElement(HTML Tag, Attribute or null, children elements)</br>

    Example:
    const page = (
      <div>
        <h1>Hello</h1>
        <p>This is my website!</p>
      </div>
    );

    const page = React.createElement(
          "div",
          null,
                  React.createElement("h1", null, "Hello"),
                  React.createElement("p", null, "This is my website!")
        );
        
7. What is the difference between `helloWorld` and `HelloWorld`?</br>

JavaScript prefers lower camel case names like `helloWorld`, </br>
React components use Pascal case (or upper camel case) variable names, like `HelloWorld`,</br>
This makes it clear that a given JSX element is a React component and not a regular HTML tag.</br>

## CUSTOM COMPONENTS
1. What is a React component?
A function that returns React elements. (UI)</br>
They are reusable modules that renders a part of our overall application. </br>

2. What's wrong with this code?
```
function MyComponent() {
    return (
        <small>I'm tiny text!</small>
    )
}
```
First, it's rendered inside another component or Second, within ReactDOM.createRoot().render(<MyComponent />) in your main file</br>
optionally ReactDOM.render(<Header />, document.getElementById("root")).

3. What's wrong with this code?
```
function Header() {
    return (
        <header>
            <nav>
                <img src="./react-logo.png" width="40px" />
            </nav>
        </header>
    )
}

ReactDOM.render(<Header />, document.getElementById("root"))</br>
```
ReactDOM.render() is outdated after React 18 </br>
USE ReactDOM.createRoot():  </br>
const root = ReactDOM.createRoot(document.getElementById("root"));</br>
root.render(<Header />);</br>

## PROPS
1. What do props help us accomplish?</br>
Make a component more reusable.</br>


2. How do you pass a prop into a component?</br>
   <MyAwesomeHeader title="???" /></br>

function Header(props) {
    return <h1>{props.title}</h1>;
}


3. Can I pass a custom prop (e.g. `blahblahblah={true}`) to a native DOM element? (e.g. <div blahblahblah={true}>) Why or why not? </br>
No, because the JSX we use to describe native DOM elements will be turned into REAL DOM elements by React. </br>
And real DOM elements only have the properties/attributes specified in the HTML specification. (Which doesn't include properties like `blahblahblah`) </br>


4. How do I receive props in a component?</br>
function Navbar(props) {
    console.log(props.blahblahblah)
    return (
        <header>
            ...
        </header>
    )
}

## MAP
1. What does the `.map()` array method do?</br>
Returns a new array. Whatever gets returned from the callback</br>
function provided is placed at the same index in the new array.</br>
Usually we take the items from the original array and modify them</br>
in some way.


2. What do we usually use `.map()` for in React?
Convert an array of raw data into an array of JSX elements
that can be displayed on the page.


3. Why is using `.map()` better than just creating the components
   manually by typing them out?
It makes our code more "self-sustaining" - not requiring
additional changes whenever the data changes.

for(let i = 0; i < someArray.length; i++) {
    
}


## PROPS VS STATE
1. How would you describe the concept of "state"?
A way for React to remember saved values from within a component.
This is similar to declaring variables from within a component,
with a few added bonuses (which we'll get to later).
useState hook returns an array of two items, the first item contains the current state, and the second item is a function used to update the state.

3. When would you want to use props instead of state?
Anytime you want to pass data into a component so that
component can determine what will get displayed on the
screen.


4. When would you want to use state instead of props?
Anytime you want a component to maintain some values from
within the component. (And "remember" those values even
when React re-renders the component).


5. What does "immutable" mean? Are props immutable? Is state immutable?
Unchanging. Props are immutable. State is mutable.

## CHANGING STATE 
#### Remember useState hook returns an array of two items, the first: current state, and the second: a function to update the state.

1. You have 2 options for what you can pass in to a
   state setter function (e.g. `setCount`). What are they?
   Remember useState hook returns an array of two items, the first: current state, and the second: a function to update the state.
   
a. New value of state (setCount(42))
b. Callback function - whatever the callback function 
   returns === new value of state


2. When would you want to pass the first option (from answer
   above) to the state setter function?
Whenever you don't need the previous value of state to determine
what the new value of state should be.


3. When would you want to pass the second option (from answer
   above) to the state setter function?
Whenever you DO need the previous value to determine the new value

## CONDITIONAL RENDERING
1. What is "conditional rendering"?
When we want to only sometimes display something on the page
based on a condition of some sort


2. When would you use &&?
When you want to either display something or NOT display it


3. When would you use a ternary?
When you need to decide which thing among 2 options to display


4. What if you need to decide between > 2 options on
   what to display?
Use an `if...else if... else` conditional or a `switch` statement


function App() {
    let someVar
    if () {
        someVar = <SomeJSX />
    } else if() {
        ...
    } else {
        ...
    }
    return (
        <div>{someVar}</div>
    )
}
## FORMS
1. In a vanilla JS app, at what point in the form submission
   process do you gather all the data from the filled-out form?
Right before the form is submitted.


2. In a React app, when do you gather all the data from
   the filled-out form?
As the form is being filled out. The data is all held in local state.


3. Which attribute in the form elements (value, name, onChange, etc.)
   should match the property name being held in state for that input?
`name` property.


4. What's different about saving the data from a checkbox element
   vs. other form elements?
A checkbox uses the `checked` property to determine what should
be saved in state. Other form elements use the `value` property instead.


5. How do you watch for a form submit? How can you trigger
   a form submit?
- Can watch for the submit with an onSubmit handler on the `form` element.
- Can trigger the form submit with a button click.

## HOOKS
1. What is a "side effect" in React? What are some examples?
- Any code that affects an outside system.
- local storage, API, websockets, two states to keep in sync


2. What is NOT a "side effect" in React? Examples?
- Anything that React is in charge of.
- Maintaining state, keeping the UI in sync with the data, 
  render DOM elements


3. When does React run your useEffect function? When does it NOT run
   the effect function?
- As soon as the component loads (first render)
- On every re-render of the component (assuming no dependencies array)
- Will NOT run the effect when the values of the dependencies in the
  array stay the same between renders


4. How would you explain what the "dependecies array" is?
- Second paramter to the useEffect function
- A way for React to know whether it should re-run the effect function

5. WHy should we use Hooks with function components?
- Hooks add state to function components


6. useEffect takes a function as its parameter. If that function
   returns something, it needs to be a cleanup function.
   Otherwise, it should return nothing. If we make it an async function,
   it automatically retuns a promise instead of a function or nothing.
   Therefore, if you want to use async operations inside of useEffect,
   you need to define the function separately inside of the callback
   function.

           useEffect(() => {
                   // Your effect
              return function Cleanup () {
                   // Cleanup
                   // Can return an arrow function also
                   // ( ) => { }
                  };
            }, []);
   
