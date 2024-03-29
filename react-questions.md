# Questions
## React Theoretical Questions
- [How Virtual DOM works. Explain in detail.](#Q1)
- [React steps to find differences in both Virtual DOM? (how diffing works in React)](#Q2)
- [What is the difference between Shadow DOM and Virtual DOM?](#Q3)
- [Why React is so popular?](#Q4)
- [Enlist advantages and lmitations of React.](#Q5)
- [What is React reconciliation? How does it work?](#Q6)
- [What makes DOM manipulation slow.](#Q7)
- [Difference between class components and functional components.](#Q8)
- [What is the difference between state and props.](#Q9)
- [What are the limitations with HOCs?](#Q10)
- [What are error boundaries in ReactJs?](#Q11)
- [Why should we not update the state directly?](#Q12)
- [How to enable production mode in React?](#Q13)
- [What are service workers.](#Q14)
- [What is CRA and its benefits?](#Q15)
- [What is React Router? How React Router is different from history library?](#Q16) 
- [Explain Atomic Design Pattern.](#Q17)
- [What do you mean by ~ or ^ in react package.json?](#Q18)
- [What are synthetic events in React?](#Q19)

## React Hook based Questions
- [Explain usestate and useEffect.](#QA1)
- [How does useEffect work internally. Explain by fetching data with React Hooks?](#QA2)
- [How to pass data from child component to parent components?](#QA3)
- [Differences between controlled and uncontrolled components. Difference between state and ref. Give example.](#QA4)
- [What is a higher-order component? Give example.](#QA5)
- [Case of infinity loop in useEffect.](#QA6)
- [What is React router dom? Explain with an example.](#QA7)
- [How to re-render the view when the browser is resized?](#QA8)
- [How to handle asynchronous calls?](#QA9)
- [What is render props pattern? Explain some of the React Design Pattern.](#QA10)
- [What is code-splitting or dynamic import? Explain `React.lazy()` and `Suspense()`.](#QA11)
- [What are Pure Components. Why they are used. Explain how they are implemented in both Hooks and Class based React component. ](#QA12)
- [Explain difference between `useMemo` and `useCallback`.](#QA13)
- [Explain `useReducer` hook.](#QA14)
- [What is prop drilling? How can we avoid it by context API. Give example.](#QA15)
- [What is Flux?](#QA16)
- [What is Redux? What are the core principles of Redux? Explain the flow.](#QA17)
- [Explain Redux Saga with an example.](#QA18)
- [How you implement Server-Side Rendering or SSR?](#QA19)
- [Optimization hooks](#QA20)

## React Class based Questions
- [Lifecycle methods](#QB1)
- [Difference between state and ref.](#QB2)
- [What are pure components? Explain with example](#QB3)
- [What are React Event Handlers?](#QB4)
- [What is the difference between mapStateToProps() and mapDispatchToProps()? Explain the flow of Redux in Class based component.](#QB5)

---

# Answers
## React Theoretical Questions
#### Q1
### ✍How Virtual DOM works. Explain in detail
The *Virtual DOM (VDOM)* is an in-memory representation of Real DOM. The representation of a UI is kept in memory and synced with the "real" DOM. It's a step that happens between the render function being called and the displaying of elements on the screen. This entire process is called *reconciliation*.

The *Virtual DOM* works in three simple steps.

1. Whenever any underlying data changes, the entire UI is re-rendered in Virtual DOM representation.

![vdom](https://i.ibb.co/PYF21vk/vdom1.jpg)

2. Then the difference between the previous DOM representation and the new one is calculated.

![vdom2](https://i.ibb.co/WWHM5zS/vdom2.png)

3. Once the calculations are done, the real DOM will be updated with only the things that have actually changed.

![vdom3](https://i.ibb.co/gjggh5D/vdom3.png)

- Updating virtual DOM in ReactJS is faster because ReactJS uses
ReactJS uses observable’s to find the modified components. Whenever setState() method is called on any component, ReactJS makes that component dirty and re-renders it. Creating the whole Virtual DOM from scratch is fast and doesn't affect performance. ReactJS maintains two virtual DOM, one with the updated state Virtual DOM and other with the previous state Virtual DOM.

- Efficient diffing algorithm
If the state of a component has changed, then ReactJS re-renders all the child components even if child components are not modified. To prevent the unwanted re-render of the child components we can use shouldComponentUpdate() component life cycle method.
ReactJS traverse the tree using BFS.
Reconciliation. It is the process to determine which parts of the Real DOM need to be updated.

- Batched update operations
ReactJS using the diff algorithm to find the minimum number of steps to update the Real DOM. Once it has these steps, it executes all the steps in one event loop without involving the steps to repaint the Real DOM.

**[⬆](#Questions)**
---
#### Q2
### ✍React steps to find differences in both Virtual DOM? (how diffing works in React)
Below is the DOM structure

![html-dom](https://i.ibb.co/j3LvgJF/react-html-dom.png)

Since DOM is represented as a tree structure, changes to the DOM is pretty quick but the changed element, and it’s children’s has to go through **Reflow/Layout** stage and then the changes has to be **Re-painted** which are slow. Therefore more the items to reflow/repaint, more slow your app becomes.

*What Virtual-DOM does is, it tries to minimize these two stages, and thereby getting a better performance for a big complex app.*

- First, making the component dirty.
- Next step is to update the *virtual DOM* and then use the *diffing algorithm* to do the *reconciliation* and update the actual DOM.

The reconciliation process is where React
- Compares the previous internal instance with the next internal instance.
- Updates the internal Instance which is a Component Tree structure in JavaScript Object(**Virtual DOM**).
- And updates the actual DOM only at the node where there is an actual change along with it’s children.

**[⬆](#Questions)**
---
#### Q3
### ✍What is the difference between Shadow DOM and Virtual DOM?
The *Shadow DOM* is a browser technology designed primarily for scoping variables and CSS in *web components*. The *Virtual DOM* is a concept implemented by libraries in JavaScript on top of browser APIs.

**[⬆](#Questions)**
---
#### Q4
### ✍Why React is so popular?
- React is declarative. When you write a component, you just tell React what do you want the DOM to look like, and just let React handle it from there.
- It uses VirtualDOM instead of RealDOM considering that RealDOM manipulations are expensive.
- Supports server-side rendering.
- Follows Unidirectional data flow or data binding.
- Uses reusable/composable UI components to develop the view.

**[⬆](#Questions)**
---
#### Q5
### ✍Enlist advantages and lmitations of React.
Main advantages of React
- Increases the application's performance with Virtual DOM.
- JSX makes code easy to read and write.
- It renders both on client and server side (SSR).
- Easy to integrate with frameworks (Angular, Backbone) since it is only a view library.
- Easy to write unit and integration tests with tools such as Jest.

Some limitations of React
- React is just a view library, not a full framework.
- There is a learning curve for beginners who are new to web development.
- Integrating React into a traditional MVC framework requires some additional configuration.
- The code complexity increases with inline templating and JSX.
- Too many smaller components leading to over engineering or boilerplate.

**[⬆](#Questions)**
---
#### Q6
### ✍What is React reconciliation? How does it work?
When a component's props or state change, React decides whether an actual DOM update is necessary by comparing the newly returned element with the previously rendered one. When they are not equal, React will update the DOM. This process is called *reconciliation*.

**[⬆](#Questions)**
---
#### Q7
### ✍What makes DOM manipulation slow.
The re-rendering or re-painting of the UI is what makes it slow. Therefore, the more UI components you have, the more expensive the DOM updates could be, since they would need to be re-rendered for every DOM update.

**[⬆](#Questions)**
---
#### Q8
### ✍Difference between class components and functional components.
- Syntax
A functional component is just a plain JavaScript function which accepts props as an argument and returns a React element. A class component requires you to extend from React.Component and create a render function which returns a React element.

- Handling state in Functional Components
To use state variables in a functional component, we need to use useState Hook, which takes an argument of initial state.

- Handling state in Class Components
The constructor for a React component is called before it is mounted. When implementing the constructor for a React.Component subclass, you should call super(props) before any other statement. Otherwise, this.props will be undefined in the constructor, which can lead to bugs.

- Passing Props
Inside a class component
```
<Component name="Amrit" />
```
Inside a functional component, we are passing props as an argument of the function (by destructuring).

*If the component needs state or lifecycle methods then use class component otherwise use function component. However, from React 16.8 with the addition of Hooks, you could use state , lifecycle methods and other features that were only available in class component right in your function component.* 

*So, it is always recommended to use Function components, unless you need a React functionality whose Function component equivalent is not present yet, like Error Boundaries*

**[⬆](#Questions)**
---
#### Q9
### ✍What is the difference between state and props.
- Both *props* and *state* are plain JavaScript objects. While both of them hold information that influences the output of render, they are different in their functionality with respect to component. Props get passed to the component similar to function parameters whereas state is managed within the component similar to variables declared within a function.
- *State* is owned locally and updated by the component itself. *Props* are owned by a parent component and are read-only. *Props* can only be updated if a callback function is passed to the child to trigger an upstream change.
- The *state* of a parent component can be passed a prop to the child. They are referencing the same value, but only the parent component can update it.

**[⬆](#Questions)**
---
#### Q10
### ✍What are the limitations with HOCs?
- **Don’t use HOCs inside the render method**: A new version of component will be created at every render, leading to performance issue.
- **Static methods must be copied over**: When you apply a HOC to a component the new component does not have any of the static methods of the original component
```jsx
// Define a static method
WrappedComponent.staticMethod = function() {/*...*/}
// Now apply a HOC
const EnhancedComponent = enhance(WrappedComponent);

// The enhanced component has no static method
typeof EnhancedComponent.staticMethod === 'undefined' // true
```

You can overcome this by copying the methods onto the container before returning it,

```jsx
function enhance(WrappedComponent) {
  class Enhance extends React.Component {/*...*/}
  // Must know exactly which method(s) to copy :(
  Enhance.staticMethod = WrappedComponent.staticMethod;
  return Enhance;
}
```

- **Refs aren’t passed through**: For HOCs you need to pass through all props to the wrapped component but this does not work for refs. This is because ref is not really a prop similar to key. In this case you need to use the `React.forwardRef` API

**[⬆](#Questions)**
---
#### Q11
### ✍What are error boundaries in ReactJs?
Error boundaries were introduced in React 16 as a way to catch and handle JavaScript errors that occur in the UI parts of our component. So error boundaries only catch errors that occur in a lifecycle method, render method, and inside Hooks like useEffect. 

A class component becomes an error boundary if it defines a new lifecycle method called `componentDidCatch(error, info)` or `static getDerivedStateFromError()` :
```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props)
    this.state = { hasError: false }
  }

  componentDidCatch(error, info) {
    // You can also log the error to an error reporting service
    logErrorToMyService(error, info)
  }

  static getDerivedStateFromError(error) {
     // Update state so the next render will show the fallback UI.
     return { hasError: true };
   }

  render() {
    if (this.state.hasError) {
      // You can render any custom fallback UI
      return <h1>{'Something went wrong.'}</h1>
    }
    return this.props.children
  }
}
```
To create an error boundary, we simply have to create a class component and define a state variable for determining whether the error boundary has caught an error. Our class component should also have at least three methods:
- A static method called `static getDerivedStateFromError`, which is used to update the error boundary’s state
- A `componentDidCatch` lifecycle method for performing operations when our error boundaries catch an error, such as logging to an error logging service.
- A `render` method for rendering our error boundary’s child or the fallback UI in case of an error.

After that, use it in a regular component.
```jsx
<ErrorBoundary>
  <MyWidget />
</ErrorBoundary>
```
React v15 provided very basic support for *error boundaries* using `unstable_handleError` method. It has been renamed to `componentDidCatch` in React v16.

**[⬆](#Questions)**
---
#### Q12
### ✍Why should we not update the state directly?
If you try to update the state directly then it won't re-render the component.
```jsx
//Wrong
this.state.message = 'Hello world'
```
Instead use `setState()` method. It schedules an update to a component's state object. When state changes, the component responds by re-rendering.
```jsx
//Correct
this.setState({ message: 'Hello World' });
```
**Note**: You can directly assign to the state object either in constructor or using latest javascript's class field declaration syntax.

**[⬆](#Questions)**
---
#### Q13
### ✍How to enable production mode in React?
You should use Webpack's `DefinePlugin` method to set `NODE_ENV` to `production`, by which it strip out things like propType validation and extra warnings. Apart from this, if you minify the code, for example, Uglify's dead-code elimination to strip out development only code and comments, it will drastically reduce the size of your bundle.

**[⬆](#Questions)**
---
#### Q14
### ✍What are service workers.
Service workers are scripts that are run by the browser. They do not have any direct relationship with the DOM. They provide many out of the box network-related features. Service workers are the foundation of building an offline experience. They enable features such as push notifications and background sync.

- They improve the performance of your website. Caching key parts of your website only helps in making it load faster.
- Enhances user experience through an offline-first outlook. Even if one loses connectivity, one can continue to use the application normally.
- They enable notification and push APIs, which are not available through traditional web technologies.
- They enable you to perform background sync. You can defer certain actions until network connectivity is restored to ensure a seamless experience to the user.

**[⬆](#Questions)**
---
#### Q15
### ✍What is CRA and its benefits?
The `create-react-app` CLI tool allows you to quickly create & run React applications with no configuration step.

```console
# Installation
$ npm install -g create-react-app

# Create new project
$ create-react-app todo-app
$ cd todo-app

# Build, test and run
$ npm run build
$ npm run test
$ npm start
```

It includes everything we need to build a React app:
- React, JSX, ES6, and Flow syntax support.
- Language extras beyond ES6 like the object spread operator.
- Autoprefixed CSS, so you don’t need -webkit- or other prefixes.
- A fast interactive unit test runner with built-in support for coverage reporting.
- A live development server that warns about common mistakes.
- A build script to bundle JS, CSS, and images for production, with hashes and sourcemaps.

**[⬆](#Questions)**
---
#### Q16
### ✍What is React Router? How React Router is different from history library?
React Router is the standard routing library for React. From the docs: *“React Router keeps your UI in sync with the URL. It has a simple API with powerful features like lazy code loading, dynamic route matching, and location transition handling built right in.*

React Router is a wrapper around the `history` library which handles interaction with the browser's `window.history` with its browser and hash histories. It also provides memory history which is useful for environments that don't have global history, such as mobile app development (React Native) and unit testing with Node.

**[⬆](#Questions)**
---
#### Q17
### ✍Explain Atomic Design Pattern.
Atomic design, developed by Brad Frost and Dave Olsen, is a methodology for crafting design systems with five fundamental building blocks, which, when combined, promote consistency, modularity, and scalability.

The five distinct levels of atomic design — atoms > molecules > organisms > templates > pages — map incredibly well to React’s component-based architecture.
- **Atoms**: Basic building blocks of matter, such as a button, input or a form label. They’re not useful on their own.
- **Molecules**: Grouping atoms together, such as combining a button, input and form label to build functionality.
- **Organisms**: Combining molecules together to form organisms that make up a distinct section of an interface (i.e. navigation bar)
- **Templates**: Consisting mostly of groups of organisms to form a page — where clients can see a final design in place.
- **Pages**: An ecosystem that views different template renders. We can create multiple ecosystems into a single environment — the application.

**[⬆](#Questions)**
---
#### Q18
### ✍What do you mean by ~ or ^ in react package.json?
Example : the react version is specified as *^16.6.3*, which means that npm will install the most recent major version matching 16.x.x. In contrast if you see something like *~5.6.7* in package.json, it means that it will install the most recent minor version matching 5.6.x.

**[⬆](#Questions)**
---
#### Q19
### ✍What are synthetic events in React?
React has its own event handling system which is very similar to handling events on DOM elements. The react event handling system is known as Synthetic Events. The synthetic event is a cross-browser wrapper of the browser's native event.

Handling events with react have some syntactic differences from handling events on DOM. These are:
- React events are named as camelCase instead of lowercase.
- With JSX, a function is passed as the event handler instead of a string. For example:
```jsx
<button onclick="showMessage()">  
  Hello React  
</button> 

// Event declaration in React:
<button onClick={showMessage}>  
  Hello React  
</button> 
```

**[⬆](#Questions)**
---
## React Hook based Questions
#### QA1
### ✍Explain usestate and useEffect.
- `useState` is a hook that encapsulates local state management. `useState` saves us from having to create class-based components for state-related responsibilities, since it gives functional components the power and flexibility to handle it themselves.

```jsx
const [state, setState] = useState(initialstate)
```

- `useEffect` is a hook for encapsulating code that has ‘side effects,’ and is like a combination of componentDidMount, componentDidUpdate, and componentWillUnmount. Previously, functional components didn’t have access to the component life cycle, but with `useEffect` you can tap into it.

```jsx
useEffect(callback[, dependencies]);
```

```jsx
// componentDidMount
useEffect(() => {
  
}, []);

// componentDidUpdate
useEffect(() => {
  
}, [value]);

// componentWillUnmount
useEffect(() => {

  // using return inside useEffect is same as componentWillUnmount
  return(() => {

  });
}, []);
```

**[⬆](#Questions)**
---
#### QA2
### ✍How does useEffect work internally. Explain by fetching data with React Hooks?
By default, `useEffect` runs after each render of the component where it’s called.

When you call `useEffect` in your component, this is effectively queuing or scheduling an effect to maybe run, after the render is done.

After rendering finishes, `useEffect` will check the list of dependency values against the values from the last render, and will call your effect function if any one of them has changed.

```jsx
import React, { useState, useEffect } from 'react';
import "./style.css";

export default function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    const getData = async() => {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      const result = await response.json();
      setData(result);
    }

    getData();
  }, []);

  return (
    <div>
      {data.length > 0 ? (
        data.map((item) => (
          <ul>
            <li>{item.title}</li>
          </ul>
        ))
      ) : ''}
    </div>
  );
}
```
Code Link: [Click here](https://stackblitz.com/edit/react-hmj9yc?file=src/App.js)

**[⬆](#Questions)**
---
#### QA3
### ✍How to pass data from child component to parent components?
- Create a callback function in the parent component. This callback function will get the data from the child component.
- Pass the callback function in the parent as a prop to the child component.
- The child component calls the parent callback function using `props`.

```jsx
// Parent
import React, { useState } from 'react';
import InputForm from './InputForm';

export default function App() {

  const [input, setInput] = useState('');
  const [text, setText] = useState('');

  // from child we are getting 'e' from handleChange
  const handleChange = (e) => {
    setInput(e.target.value)
  }

  // from child we are getting addInputValue
  const addInputValue = () => {
    setText(input);
    setInput('');
  }

  return (
    <div>
      <InputForm 
        text={input}
        handleChange={handleChange}
        addInputValue={addInputValue}
      />

      <p>{text}</p>
    </div>
  );
}

// InputForm.js (Child)
import React from 'react';

const InputForm = ({text, handleChange, addInputValue}) => {
  
  const handleOnchange = (e) => {
    handleChange(e);
  }

  const addValue = () => {
    addInputValue();
  }

  return (
    <>
      <input 
        type="text" 
        name="input"
        value={text}
        onChange={handleOnchange}
      />
      <button onClick={addValue}>Add</button>
    </>
  )
}

export default InputForm;
```
Code Link: [Click Here](https://stackblitz.com/edit/react-coiiac?file=src/App.js)

**[⬆](#Questions)**
---
#### QA4
### ✍Differences between controlled and uncontrolled components. Difference between state and ref. Give example.
The **Uncontrolled Components** are the ones that store their own state internally, and you query the DOM using a ref to find its current value when you need it. This is a bit more like traditional HTML.

- In most cases, it's recommend to use controlled components to implement forms. In a controlled component, form data is handled by a React component. The alternative is uncontrolled components, where form data is handled by the DOM itself. Instead of writing an event handler for all of your state updates, you use a ref to retrieve values from the DOM. Example: manage focus, getting width and height of DIV element.

`useState` would be used in the cases when we want to maintain and update the properties during the re-rendering of view. We use the combination of `useRef` and `forwardRef` hook, if we want to persist the values throughout the lifetime of the component.

The *ref* is used to return a reference to the element. *They should be avoided in most cases*, however, they can be useful when you need a direct access to the DOM element or an instance of a component.

You can use `ref` in hooks like this:
```jsx
// App.js
import React from "react";
import Component1 from './Component1'

export default function App() {
  return (
    <div>
      <Component1 />
    </div>
  );
}

// Component1.js
import React, { forwardRef } from "react";
import getDimensions from './getDimensions';

const Component1 = (props, ref) => {
  return <div ref = {ref}>
    I'm Component 1 and width is: {props.width}
  </div>
}

// React HOC Pattern
export default getDimensions(forwardRef(Component1));

// getDimensions.js
import React, { useState, useEffect, useRef } from "react";

const getDimensions = (Element) => {
  function GetDimensions(props) {

    const [width, setWidth] = useState(0);
    const ref1 = useRef();

    useEffect(() => {
      if (ref1.current) {
        setWidth(ref1.current.offsetWidth);
      }
    }, [ref1])

    return <Element ref={ref1} width={width} {...props} />
  }

  return GetDimensions;
}

export default getDimensions;
```
Code Link: [Click Here](https://stackblitz.com/edit/react-u1atqp?file=src/App.js)

**[⬆](#Questions)**
---
#### QA5
### ✍What is a higher-order component? Give example.
A *higher-order component (HOC)* is a function that takes a component, adds some logic and returns that component with that additional logic. Basically, it's a pattern that is derived from React's compositional nature.

HOCs can also be called **Pure components**, which means they only re-run or re-render only if the input data (or values in dependency array) changes.

```js
const EnhancedComponent = higherOrderComponent(WrappedComponent)
```
HOC can be used for many use cases:
- Code reuse, logic and bootstrap abstraction.
- Render hijacking.
- State abstraction and manipulation.
- Props manipulation.

However, it is to be noted that we can't use HOC inside the `render()` method.

**[⬆](#Questions)**
---
#### QA6
### ✍Case of infinity loop in useEffect.
When we call `useEffect` without any dependencies argument, it generates *an infinite loop of component re-renderings*. Hence we have to include a dependency argument.

**Component Update without dependency argument**
```jsx
import { useEffect, useState } from 'react';
function CountInputChanges() {
  const [value, setValue] = useState('');
  const [count, setCount] = useState(-1);

  useEffect(() => setCount(count + 1));

  const onChange = ({ target }) => setValue(target.value);

  return (
    <div>
      <input type="text" value={value} onChange={onChange} />
      <div>Number of changes: {count}</div>
    </div>
  )
}
```

![without-dependency-arg](https://i.ibb.co/wSyr83z/react-infinite-loop-without-dependency-arg.webp)

**Component Update with dependency argument**
```jsx
import { useEffect, useState } from 'react';
function CountInputChanges() {
  const [value, setValue] = useState('');
  const [count, setCount] = useState(-1);

  useEffect(() => setCount(count + 1), [value]);

  const onChange = ({ target }) => setValue(target.value);

  return (
    <div>
      <input type="text" value={value} onChange={onChange} />
      <div>Number of changes: {count}</div>
    </div>
  )
}
```

![with-dependency-arg](https://i.ibb.co/HPch5Sj/react-infinite-loop-with-dependency-arg.webp)

**[⬆](#Questions)**
---
#### QA7
### ✍What is React router dom? Explain with an example.
`react-router-dom` is a specialized package that you can use only in web-browser-based application development.

The above example is for `react-router-dom` **v6.4.3**

```jsx
import React from 'react';
import { BrowserRouter, Routes, Route, Link, Navigate } from "react-router-dom";
import Home from "./Home";
import About from "./About";
import GetBio from "./GetBio";

export default function App() {
  return (
    <BrowserRouter>
      <div>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            <Link to="/bio/5656">GetBio</Link>
          </li>
        </ul>

        <Routes>
          <Route exact path="/" element={ <Home /> } />
          <Route exact path="/about" element={< About /> } />
          {/* use params */}
          <Route exact path="bio/:id" element={<GetBio />} />
          {/* redirects if route not found */}
          <Route exact path="*" element={<Navigate to="/" />} />
        </Routes>

      </div>
    </BrowserRouter>
  );
}

// Home.js
import React from 'react';

const Home = () => {
  return (
    <div>Home</div>
  )
}

export default Home;

// About.js
import React from 'react';

const About = () => {
  return (
    <div>About</div>
  )
}

export default About;

// GetBio.js
import React from 'react';
import { useParams } from "react-router-dom"

const GetBio = () => {
  let { id } = useParams();
  return (
    <div>User ID: {id} </div>
  )
}

export default GetBio;
```
Code Link: [Click Here](https://stackblitz.com/edit/react-nyq86f?file=src/App.js)

**[⬆](#Questions)**
---
#### QA8
### ✍How to re-render the view when the browser is resized?
Refer to QA4 [Differences between controlled and uncontrolled components. Difference between state and ref. Give example.](#QA4)

**[⬆](#Questions)**
---
#### QA9
### ✍How to handle asynchronous calls?
Refer to QA2 [How does useEffect work internally. Explain by fetching data with React Hooks?](#QA2)

**[⬆](#Questions)**
---
#### QA10
### ✍What is render props pattern? Explain some of the React Design Pattern.
The term **render props** refers to a simple technique for sharing code between React components using a prop whose value is a function.
```jsx
<Route path='/page' component={Page} />
const extraProps = { color: 'red' }

<Route path='/page' render={(props) => (
  <Page {...props} data={extraProps}/>
)}/>
```
Some of the React Design Pattern are:
- React HOC Pattern
- React Render Props Pattern
- React Compound Pattern (While implementing a Multiple Tab Component)
- React Hooks Pattern

Example of these patterns are given below
Code Link: [Click here](https://react-hzgrec.stackblitz.io)

**[⬆](#Questions)**
---
#### QA11
### ✍What is code-splitting or dynamic import? Explain `React.lazy()` and `Suspense()`.
The `code-splitting` or `dynamic import()` syntax is a ECMAScript proposal not currently part of the language standard. It is expected to be accepted in the near future. You can achieve code-splitting into your app using dynamic import.

**Normal import**
```js
import { add } from './math';
console.log(add(10, 20));
```
**Dynamic import**
```js
import("./math").then(math => {
  console.log(math.add(10, 20));
});
```

The `React.lazy` function lets you render an dynamic import as a regular component. It will automatically load the bundle containing the OtherComponent when the component gets rendered. This must return a Promise which resolves to a module with a default export containing a React component.
```jsx
const OtherComponent = React.lazy(() => import('./OtherComponent'));
```

If the module containing the dynamic import is not yet loaded by the time parent component renders, you must show some fallback content while you’re waiting for it to load using a loading indicator. This can be done using **Suspense** component.
```jsx
import React, { Suspense } from 'react';

const Header = React.lazy(() => import("./Header"));
const Footer = React.lazy(() => import("./Footer"));

export default function App() {
  return (
    <div className="App">
      <Suspense fallback={<div>Header Loading...</div>}>
        <Header />
      </Suspense>
      <Suspense fallback={<div>Footer Loading...</div>}>
        <Footer />
      </Suspense>
    </div>
  )
}
```

**[⬆](#Questions)**
---
#### QA12
### ✍What are Pure Components. Why they are used. Explain how they are implemented in both Hooks and Class based React component. 
Normally, when we update the state either by `this.setState` or `useState`, the component re-renders, even if the props values doesn't change. When we use Pure Components, it makes sure that the component re-renders only when the props value changes. 

The oldest way to optimize components performance was to use the lifecycle method `shouldComponentUpdate`:
```jsx
class ContactList extends React.Component {
  shouldComponentUpdate(nextProps) {
    return nextProps.contacts !== this.props.contacts;
    // the render function will be called only when the props `contacts` changes
  }
  render() {
    const { contacts } = this.props;
    return <List data={contacts} />;
  }
}
```
With React v15.3, `PureComponent` was added.
```jsx
class ContactList extends React.PureComponent {
  //   ^^^^^^^^^^^^^ magic happens here
  render() {
    const { contacts } = this.props;
    return <List data={contacts} />;
  }
}
```
With the coming of functional components, we can use like this:
```jsx
import React, { memo } from 'react';

export default memo(
  function ContactList({ contacts }) {
    return <List data={contacts} />;
  }
);
```
It can also take a 2nd parameter, which is equivalent to `shouldComponentUpdate` in Class components.
```jsx
import React, { memo } from 'react';

function areEqual(prevProps, nextProps) {
  return prevProps.contacts === nextProps.contacts;
  // the component will be updated only on `contact` props changes.
}

export default memo(
  function ContactList({ title, contacts }) {
    return <List title={title} data={contacts} />;
  },
  areEqual
);
```
With React v16.8, we can use `useMemo` hook which is more convenient.
```jsx
import React, { useMemo } from 'react';

function ContactList({ title, contacts }) {
  const listComponent = useMemo(() => {
    return <List title={title} data={contacts} />;
  }, [contacts]);
  //  ^^^^^^^^ `props.contacts` dependency
  
  return listComponent;
}
```

**[⬆](#Questions)**
---
#### QA13
### ✍Explain difference between `useMemo` and `useCallback`.
The difference is that `useCallback` returns its function when the dependencies change while `useMemo` calls its function and returns the result. 
```jsx
function foo() {
  return 'bar';
}

const memoizedCallback = useCallback(foo, []);
const memoizedResult = useMemo(foo, []);

memoizedCallback;
// ƒ foo() {
//   return 'bar';
// }
memoizedResult; // 'bar' (we're getting the result)
memoizedCallback(); // 'bar' (We're calling it as a function to get result)
memoizedResult(); // TypeError 
```

**[⬆](#Questions)**
---
#### QA14
### ✍Explain `useReducer` hook.
`useReducer` is an alternative to `useState`. Accepts a reducer of type `(state, action) => newState`, and returns the current state paired with a `dispatch` method.

```jsx
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

`useReducer` is usually preferable to useState when you have complex state logic that involves multiple sub-values or when the next state depends on the previous one. `useReducer` also lets you optimize performance for components that trigger deep updates because you can pass dispatch down instead of callbacks.

```jsx
import React, { useReducer } from "react";

const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

export default function App() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}

```
Code Link: [Click Here](https://stackblitz.com/edit/react-e9c19h?file=src/App.js)

**[⬆](#Questions)**
---
#### QA15
### ✍What is prop drilling? How can we avoid it by context API. Give example.
When there is a lot of nested Parent-Child components, we have to pass data to all those nested components, the reason being React is uni-directional. This is called Prop drilling.

We can avoid prop drilling by using a centralized store for state management such as Redux or Context API.

`useContext` is a hook that accepts a context object (the value returned from `React.createContext`) and returns the current context value for that context. The current context value is determined by the value prop of the nearest `<MyContext.Provider>` above the calling component in the tree.

When the nearest `<MyContext.Provider>` above the component updates, this Hook will trigger a rerender with the latest context value passed to that MyContext provider. Even if an ancestor uses `React.memo` or `shouldComponentUpdate`, a rerender will still happen starting at the component itself using `useContext`.

```jsx
import React, { useContext } from "react";

const themes = {
  light: {
    foreground: "#000000",
    background: "#eeeeee"
  },
  dark: {
    foreground: "#ffffff",
    background: "#222222"
  }
};

const ThemeContext = React.createContext(themes.light);

export default function App() {
  return (
    <div>
      <ThemeContext.Provider value={themes.dark}>
        <Toolbar />
      </ThemeContext.Provider>
    </div>
  );
}

function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return (
    <button style={{ background: theme.background, color: theme.foreground }}>
      I am styled by theme context!
    </button>
  );
}
```
Code Link: [Click Here](https://stackblitz.com/edit/react-ostxwl?file=src/App.js)

**[⬆](#Questions)**
---
#### QA16
### ✍What is Flux?
*Flux is an application design paradigm* used as a replacement for the more traditional MVC pattern. It is a new kind of architecture that complements React and the concept of Unidirectional Data Flow.

The workflow between dispatcher, stores and views components with distinct inputs and outputs as follows:

![flux](https://i.ibb.co/G3Dfx7G/react-flux.png)

**[⬆](#Questions)**
---
#### QA17
### ✍What is Redux? What are the core principles of Redux? Explain the flow.
*Redux* is a predictable state container for JavaScript apps based on the *Flux design pattern*. Redux can be used together with React, or with any other view library. It is tiny (about 2kB) and has no dependencies.

![redux](https://i.ibb.co/m5vFBqn/reduxasyncdataflowdiagram.gif)

The core principles of Redux:
- **Single source of truth**: The state of your whole application is stored in an object tree within a single store. The single state tree makes it easier to keep track of changes over time and debug or inspect the application.
- **State is read-only**: The only way to change the state is to emit an action, an object describing what happened. This ensures that neither the views nor the network callbacks will ever write directly to the state.
- **Changes are made with pure functions**: To specify how the state tree is transformed by actions, you write reducers. Reducers are just pure functions that take the previous state and an action as parameters, and return the next state.

##### Initial setup
- Install `redux`, `react-redux` and `@reduxjs/toolkit`.
- Wrap `<App>` with `<Provider />`
```jsx
import { Provider } from "react-redux";
import store from "./redux/configureStore";

<Provider store={store}>
  <App />
</Provider>
```

- Configure the store
<!-- configureStore.js -->
```jsx
import { configureStore } from '@reduxjs/toolkit';
import countReducer from './store/countReducer';

export default configureStore({
	reducer: {
		counter: countReducer,
	},
});
```

- Create a reducer - add action, based on action change the state
```jsx
export const INCREMENT = 'increment';
export const DECREMENT = 'decrement';

export const increment = () => ({
  type: INCREMENT
});

export const decrement = () => ({
  type: DECREMENT
});

const initialState = {
  count: 0
};

export default (state = initialState, action) => {
  switch(action.type) {
    case INCREMENT:
      return { ...state, count: state.count + 1 }
    case DECREMENT:
      return { ...state, count: state.count - 1 }
    default:
      return { ...state }
  }
}
```
- use it in the component using `useDispatch` and `useSelector`
```jsx
import React from 'react';
import { useDispatch, useSelector } from 'react-redux';
import { increment, decrement } from "./redux/store/countReducer";

const Counter = () => {
  const count = useSelector((state) => state.counter.count);
  const dispatch = useDispatch();

  const handleIncrement = () => {
    dispatch(increment());
  }

  const handleDecrement = () => {
    dispatch(decrement());
  }

  return (
    <div>
      <h3>Counter: {count}</h3>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
    </div>
  )
}

export default Counter;
```
Code Link: [Click Here](https://stackblitz.com/edit/react-7bavk8?file=src/App.js)

**Note**: Redux is synchronous. We add middleware like thunk and saga to handle asynchronous functions.

**[⬆](#Questions)**
---
#### QA18
### ✍Explain Redux Saga with an example.


**[⬆](#Questions)**
---
#### QA19
### ✍How you implement Server-Side Rendering or SSR?
React is already equipped to handle rendering on Node servers. A special version of the DOM renderer is available, which follows the same pattern as on the client side.
```jsx
import ReactDOMServer from 'react-dom/server'
import App from './App'

ReactDOMServer.renderToString(<App />)
```
This method will output the regular HTML as a string, which can be then placed inside a page body as part of the server response. On the client side, React detects the pre-rendered content and seamlessly picks up where it left off.

**[⬆](#Questions)**
---
#### QA20
### ✍Optimization hooks
Some hooks we can use are:
- useMemo() Hook: Refer QA12 [What are Pure Components. Why they are used. Explain how they are implemented in both Hooks and Class based React component. ](#QA12)
- useCallback() Hook Refer QA13 [Explain difference between `useMemo` and `useCallback`.](#QA13)

Some minor improvements are
- `let` and `const`: With `const`, the code is explicitly telling the JavaScript Engine that the value cannot change
- Use Fragments: This mostly has benefit on deep trees, but rendering one less DOM node is still one less step in the process.

**[⬆](#Questions)**
---
## React Class based Questions
#### QB1
### ✍Lifecycle methods
The component lifecycle has three distinct lifecycle phases:
- **Mounting**: The component is ready to mount in the browser DOM. This phase covers initialization from `constructor()`, `getDerivedStateFromProps()`, `render()`, and `componentDidMount()` lifecycle methods.
- **Updating**: In this phase, the component gets updated in two ways, sending the new props and updating the state either from `setState()` or `forceUpdate()`. This phase covers `getDerivedStateFromProps()`, `shouldComponentUpdate()`, `render()`, `getSnapshotBeforeUpdate()` and `componentDidUpdate()` lifecycle methods.
- **Unmounting**: In this last phase, the component is not needed and gets unmounted from the browser DOM. This phase includes `componentWillUnmount()` lifecycle method.

It's worth mentioning that React internally has a concept of phases when applying changes to the DOM. They are separated as follows:
- **Render** The component will render without any side-effects. This applies for Pure components and in this phase, React can pause, abort, or restart the render.
- **Pre-commit** Before the component actually applies the changes to the DOM, there is a moment that allows React to read from the DOM through the `getSnapshotBeforeUpdate()`.
- **Commit** React works with the DOM and executes the final lifecycles respectively `componentDidMount()` for mounting, `componentDidUpdate()` for updating, and `componentWillUnmount()` for unmounting.

React 16.3+ Phases
![react-after-16-3](https://i.ibb.co/YBDHfNc/react-react16-3-after.png)

Before React 16.3+ 
![react-before-16-3](https://i.ibb.co/pfpknxm/react-react16-3-before.png)

The lifecycle methods of React before 16.3
Before React 16.3
- **componentWillMount**: Executed before rendering and is used for App level configuration in your root component.
- **componentDidMount**: Executed after first rendering and here all AJAX requests, DOM or state updates, and set up event listeners should occur.
- **componentWillReceiveProps**: Executed when particular prop updates to trigger state transitions.
- **shouldComponentUpdate**: Determines if the component will be updated or not. By default it returns `true`. If you are sure that the component doesn't need to render after state or props are updated, you can return false value. It is a great place to improve performance as it allows you to prevent a re-render if component receives new prop.
- **componentWillUpdate**: Executed before re-rendering the component when there are props & state changes confirmed by `shouldComponentUpdate()` which returns true.
- **componentDidUpdate**: Mostly it is used to update the DOM in response to prop or state changes.
- **componentWillUnmount**: It will be used to cancel any outgoing network requests, or remove all event listeners associated with the component.

The lifecycle methods of React after 16.3
- **getDerivedStateFromProps**: Invoked right before calling `render()` and is invoked on every render. This exists for rare use cases where you need derived state.
- **componentDidMount**: Executed after first rendering and where all AJAX requests, DOM or state updates, and set up event listeners should occur.
- **shouldComponentUpdate**: Determines if the component will be updated or not. By default it returns true.
- **getSnapshotBeforeUpdate**: Executed right before rendered output is committed to the DOM. Any value returned by this will be passed into `componentDidUpdate()`. This is useful to capture information from the DOM i.e. scroll position.
- **componentDidUpdate**: Mostly it is used to update the DOM in response to prop or state changes. This will not fire if `shouldComponentUpdate()` returns `false`.
- **componentWillUnmount** It will be used to cancel any outgoing network requests, or remove all event listeners associated with the component.

###### The lifecycle methods are called in the following order when an instance of a component is being created and inserted into the DOM.
- `constructor()`
- `static getDerivedStateFromProps()`
- `render()`
- `componentDidMount()`

**[⬆](#Questions)**
---
#### QB2
### ✍Difference between state and ref.
The *ref* is used to return a reference to the element. *They should be avoided in most cases*, however, they can be useful when you need a direct access to the DOM element or an instance of a component.

- You can create *ref* by using `React.createRef()` method
```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props)
    this.myRef = React.createRef()
  }
  render() {
    return <div ref={this.myRef} />
  }
}
```
- You can also use *ref callbacks approach* regardless of React version. For example, the search bar component's input element accessed as follows:
```jsx
class SearchBar extends Component {
   constructor(props) {
      super(props);
      this.txtSearch = null;
      this.state = { term: '' };
      this.setInputSearchRef = e => {
         this.txtSearch = e;
      }
   }
   onInputChange(event) {
      this.setState({ term: this.txtSearch.value });
   }
   render() {
      return (
         <input
            value={this.state.term}
            onChange={this.onInputChange.bind(this)}
            ref={this.setInputSearchRef} />
      );
   }
}
```

**[⬆](#Questions)**
---
#### QB3
### ✍What are pure components? Explain with example
`React.PureComponent` is exactly the same as `React.Component` except that it handles the `shouldComponentUpdate()` method for you. When props or state changes, PureComponent will do a shallow comparison on both props and state. Component on the other hand won't compare current props and state to next out of the box. Thus, the component will re-render by default whenever shouldComponentUpdate is called.

A React component is considered pure if it renders the same output for the same state and props.
Pure components have some performance improvements and render optimizations since React implements the shouldComponentUpdate() method for them with a shallow comparison for props and state.

```jsx
// FUNCTIONAL COMPONENT
function PercentageStat({ label, score = 0, total = Math.max(1, score) }) {
  return (
    <div>
      <h6>{ label }</h6>
      <span>{ Math.round(score / total * 100) }%</span>
    </div>
  )
}

// CONVERTED TO PURE COMPONENT
class PercentageStat extends React.PureComponent {
  render() {
    const { label, score = 0, total = Math.max(1, score) } = this.props;

    return (
      <div>
        <h6>{ label }</h6>
        <span>{ Math.round(score / total * 100) }%</span>
      </div>
    )
  }
}
```

**[⬆](#Questions)**
---
#### QB4
### ✍What are React Event Handlers?
- **binding in constructor**:

```jsx
class Foo extends Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    console.log('Click happened');
  }
  render() {
    return <button onClick={this.handleClick}>Click Me</button>;
  }
}
```

- **Public class fields syntax**:
```jsx
handleClick = () => {
  console.log('this is:', this)
}

<button onClick={this.handleClick}>
  {'Click me'}
</button>
```

- **Arrow functions in callbacks**:
```jsx
handleClick() {
  console.log('Click happened');
}
render() {
  return <button onClick={() => this.handleClick()}>Click Me</button>;
}
```
**Note**: If the callback is passed as prop to child components, those components might do an extra re-rendering. In those cases, it is preferred to go with .bind() or public class fields syntax approach considering performance.

**[⬆](#Questions)**
---
#### QB5
### ✍What is the difference between mapStateToProps() and mapDispatchToProps()? Explain the flow of Redux in Class based component.
`mapStateToProps()` is a utility which helps your component get updated state (which is updated by some other components):

```jsx
const mapStateToProps = (state) => {
  return {
    todos: getVisibleTodos(state.todos, state.visibilityFilter)
  }
}
```

`mapDispatchToProps()` is a utility which will help your component to fire an action event (dispatching action which may cause change of application state):

```jsx
const mapDispatchToProps = (dispatch) => {
  return {
    onTodoClick: (id) => {
      dispatch(toggleTodo(id))
    }
  }
}
```

You can dispatch an action in `componentDidMount()` method and in `render()` method you can verify the data.

```jsx
class App extends Component {
  componentDidMount() {
    this.props.fetchData()
  }

  render() {
    return this.props.isLoaded
      ? <div>{'Loaded'}</div>
      : <div>{'Not Loaded'}</div>
  }
}

const mapStateToProps = (state) => ({
  isLoaded: state.isLoaded
})

const mapDispatchToProps = { fetchData }

export default connect(mapStateToProps, mapDispatchToProps)(App)
```

**[⬆](#Questions)**
---

