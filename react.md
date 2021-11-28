# Questions
## Common
- [How Virtual DOM works. Explain in detail.](#Q1)
- [Principles why React is so popular?](#Q2)
- [What is React reconciliation? How does it work?](#Q3)
- [What makes DOM manipulation slow.](#Q4)
- [What is JSX?](#Q5)
- [Difference between class components and functional components.](#Q6)
- [What is the difference between state and props.](#Q7)
- [What is render prop pattern? Explain.](#Q8)
- [Lifecycle methods](#Q9)
- [Differences between controlled and uncontrolled components. Give example.](#Q10)
- [What is a higher-order component? Give example.](#Q11)
- [What are service workers.](#Q12)
- [What is context API? or How can we avoid prop drilling?](#Q13)
- [react-redux vs context API vs passing props](#Q14)
- [How to prevent re-renders on React functional components?](#Q15)
- [What is React router?](#Q16)
- [Difference between state and ref.](#Q17)
- [What are error boundaries in ReactJs?](#Q18)
- [How to pass data from child component to parent components?](#Q19)
- [Explain Atomic Design Pattern.](#Q20)
- [What are pure components? Explain with example](#Q21)
- [What do you mean by ~ or ^ in react package.json?](#Q22)
- [React steps to find differences in both Virtual DOM?](#Q23)
- [Case of infinity loop in useEffect.](#Q24)
- [What are React Event Handlers?](#Q25)
- [How to handle asynchronous calls?](#Q26)

## Hooks
- [How does React state usestate and useEffect work internally](#QA1)
- [How does useEffect work internally](#QA2)
- [Optimization hooks](#QA3)
- [useMemo](#QA4)
- [useCallback](#QA5)
- [How is React.memo different from useMemo ( two very different things )](#QA6)
- [useReducer, useContext hook](#QA7)
- [What is a reducer?](#QA8)

# Answers
---
### Q1
✍How Virtual DOM works.Explain in detail
Virtual DOM is an in-memory representation of real DOM. It is a lightweight JavaScript object which is a copy of Real DOM.

- Updating virtual DOM in ReactJS is faster because ReactJS uses
ReactJS uses observable’s to find the modified components. Whenever setState() method is called on any component, ReactJS makes that component dirty and re-renders it. Creating the whole Virtual DOM from scratch is fast and doesn't affect performance. ReactJS maintains two virtual DOM, one with the updated state Virtual DOM and other with the previous state Virtual DOM.

- Efficient diff algorithm
If the state of a component has changed, then ReactJS re-renders all the child components even if child components are not modified. To prevent the unwanted re-render of the child components we can use shouldComponentUpdate() component life cycle method.
ReactJS traverse the tree using BFS.
Reconciliation. It is the process to determine which parts of the Real DOM need to be updated.

- Batched update operations
ReactJS using the diff algorithm to find the minimum number of steps to update the Real DOM. Once it has these steps, it executes all the steps in one event loop without involving the steps to repaint the Real DOM.

**[⬆](#Questions)**
---
### Q2
✍Principles why React is so popular?
- React is declarative. When you write a component, you just tell React what do you want the DOM to look like, and just let React handle it from there.
- Reusable components.
- One way data flow
- Just UI

**[⬆](#Questions)**
---
### Q3
✍What is React reconciliation? How does it work?
- If a node has changed its type (H1 -> MARKUEE or View -> Text), the old one is dismissed and the new one is recursively rendered from scratch.
- If two nodes in both trees have equal key props, they are the same node and are reused without creating a new one.

**[⬆](#Questions)**
---
### Q4
✍What makes DOM manipulation slow?
The re-rendering or re-painting of the UI is what makes it slow. Therefore, the more UI components you have, the more expensive the DOM updates could be, since they would need to be re-rendered for every DOM update.

**[⬆](#Questions)**
---
### Q5
✍What is JSX?
JSX stands for JavaScript XML. JSX allows us to write HTML in React. JSX makes it easier to write and add HTML in React. JSX is not valid and is translated to regular JavaScript at runtime.

**[⬆](#Questions)**
---
### Q6
✍Difference between class components and functional components.
- Syntax
A functional component is just a plain JavaScript function which accepts props as an argument and returns a React element. A class component requires you to extend from React.Component and create a render function which returns a React element.

- State
To use state variables in a functional component, we need to use useState Hook, which takes an argument of initial state.

- Handling state in Class Components
The constructor for a React component is called before it is mounted. When implementing the constructor for a React.Component subclass, you should call super(props) before any other statement. Otherwise, this.props will be undefined in the constructor, which can lead to bugs.

- Passing Props
Inside a class component
```
<Component name="Riya" />
```
Inside a functional component, we are passing props as an argument of the function (by destructuring).

**[⬆](#Questions)**
---
### Q7
✍What is the difference between state and props?
The difference is all about which component owns the data. State is owned locally and updated by the component itself. Props are owned by a parent component and are read-only. Props can only be updated if a callback function is passed to the child to trigger an upstream change.

The state of a parent component can be passed a prop to the child. They are referencing the same value, but only the parent component can update it.

**[⬆](#Questions)**
---
### Q8
✍What is render prop pattern? Explain.
The term “render prop” refers to a simple technique for sharing code between React components using a prop whose value is a function.
```
<Route path='/page' component={Page} />
const extraProps = { color: 'red' }
<Route path='/page' render={(props) => (
  <Page {...props} data={extraProps}/>
)}/>
```

**[⬆](#Questions)**
---
### Q9
✍Lifecycle methods
- On Mounting (componentDidMount):
- On Unmounting (componentWillUnmount)

**[⬆](#Questions)**
---
### Q10
✍Differences between controlled and uncontrolled components. Give example.
- Controlled component: The value of input element is controlled by React. Takes value through props and notifies changes through callback like onChange.
Examples: form validation,disable submit button unless all fields have valid data,specific format needed like credit card format.
- Uncontrolled Component Uncontrolled components act more like traditional HTML form elements. The data for each input element is stored in the DOM, not in the component. Instead of writing an event handler for all of your state updates, you use a ref to retrieve values from the DOM.
Example: manage focus.

**[⬆](#Questions)**
---
### Q11
✍What is a higher-order component? Give example.
A HOC is structured like a higher-order function:
It is a component. It takes another component as an argument. Then, it returns a new component. The component it returns can render the original component that was passed to it.

**[⬆](#Questions)**
---
### Q12
✍What are service workers?
Service workers are scripts that are run by the browser. They do not have any direct relationship with the DOM. They provide many out of the box network-related features. Service workers are the foundation of building an offline experience. They enable features such as push notifications and background sync.

- They improve the performance of your website. Caching key parts of your website only helps in making it load faster.
- Enhances user experience through an offline-first outlook. Even if one loses connectivity, one can continue to use the application normally.
- They enable notification and push APIs, which are not available through traditional web technologies.
- They enable you to perform background sync. You can defer certain actions until network connectivity is restored to ensure a seamless experience to the user.

**[⬆](#Questions)**
---
### Q13
✍What is context API? or How can we avoid prop drilling?

**[⬆](#Questions)**
---
### Q14

**[⬆](#Questions)**
---
### Q15
✍How to prevent re-renders on React functional components?
To optimize, and prevent multiple React renders, I’m going to use another React tool called React.memo().
In programming, memoization is an optimization technique. It’s primarily used to speed up computing by story the result of a function and returning the cached result, when the same inputs occur again.

**[⬆](#Questions)**
---
### Q16
✍What is React router?
React Router is the standard routing library for React. From the docs: “React Router keeps your UI in sync with the URL. It has a simple API with powerful features like lazy code loading, dynamic route matching, and location transition handling built right in.

**[⬆](#Questions)**
---
### Q17
✍Difference between state and ref.
useState would be used in the cases when we want to maintain and update the properties during the re-rendering of view.useRef we will use if we want to persist the values throughout the lifetime of the component.

**[⬆](#Questions)**
---
### Q18
✍What are error boundaries in ReactJs?
Error boundaries were introduced in React 16 as a way to catch and handle JavaScript errors that occur in the UI parts of our component. So error boundaries only catch errors that occur in a lifecycle method, render method, and inside Hooks like useEffect. 

To create an error boundary, we simply have to create a class component and define a state variable for determining whether the error boundary has caught an error. Our class component should also have at least three methods:
- A static method called getDerivedStateFromError, which is used to update the error boundary’s state
- A componentDidCatch lifecycle method for performing operations when our error boundaries catch an error, such as logging to an error logging service.
- A render method for rendering our error boundary’s child or the fallback UI in case of an error.

**[⬆](#Questions)**
---
### Q19
✍How to pass data from child component to parent components? 
- Create a callback function in the parent component. This callback function will get the data from the child component.
- Pass the callback function in the parent as a prop to the child component.
- The child component calls the parent callback function using props.
import React from 'react';
```
class Parent extends React.Component{
    constructor(props){
        super(props);
        this.state = {
            data: null
        }
    }

    handleCallback = (childData) =>{
        this.setState({data: childData})
    }

    render(){
        const {data} = this.state;
        return(
            <div>
                <Child parentCallback = {this.handleCallback}/>
                {data}
            </div>
        )
    }
}

class Child extends React.Component{

    onTrigger = (event) => {
        this.props.parentCallback("Data from child");
        event.preventDefault();
    }

    render(){
        return(
        <div>
            <form onSubmit = {this.onTrigger}>
                <input type = "submit" value = "Submit"/>
            </form>
        </div>
        )
    }
}

export default Parent;
```

**[⬆](#Questions)**
---
### Q20
✍Explain Atomic Design Pattern.
Atomic design, developed by Brad Frost and Dave Olsen, is a methodology for crafting design systems with five fundamental building blocks, which, when combined, promote consistency, modularity, and scalability.

The five distinct levels of atomic design — atoms > molecules > organisms > templates > pages — map incredibly well to React’s component-based architecture.
- Atoms: Basic building blocks of matter, such as a button, input or a form label. They’re not useful on their own.
- Molecules: Grouping atoms together, such as combining a button, input and form label to build functionality.
- Organisms: Combining molecules together to form organisms that make up a distinct section of an interface (i.e. navigation bar)
- Templates: Consisting mostly of groups of organisms to form a page — where clients can see a final design in place.
- Pages: An ecosystem that views different template renders. We can create multiple ecosystems into a single environment — the application.

**[⬆](#Questions)**
---
### Q21
✍What are pure components? Explain with example.
A React component is considered pure if it renders the same output for the same state and props.
Pure components have some performance improvements and render optimizations since React implements the shouldComponentUpdate() method for them with a shallow comparison for props and state.
```
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
### Q22
✍What do you mean by ~ or ^ in react package.json?
Example : the react version is specified as ^16.6.3, which means that npm will install the most recent major version matching 16.x.x. In contrast if you see something like ~5.6.7 in package.json, it means that it will install the most recent minor version matching 5.6.x.

**[⬆](#Questions)**
---
### Q23

**[⬆](#Questions)**
---
### Q24

**[⬆](#Questions)**
---
### Q25

**[⬆](#Questions)**
---
### Q26

**[⬆](#Questions)**
---
### QA1
✍How does React state usestate and useEffect work internally
- useState is a hook that encapsulates local state management. useState saves us from having to create class-based components for state-related responsibilities, since it gives functional components the power and flexibility to handle it themselves.
```
const [state, setState] = useState(initialstate)
```
- useEffect is a hook for encapsulating code that has ‘side effects,’ and is like a combination of componentDidMount, componentDidUpdate, and componentWillUnmount. Previously, functional components didn’t have access to the component life cycle, but with useEffect you can tap into it.
```
useEffect(callback[, dependencies]);
```

**[⬆](#Questions)**
---
### QA2

**[⬆](#Questions)**
---
### QA3

**[⬆](#Questions)**
---
### QA4

**[⬆](#Questions)**
---
### QA5

**[⬆](#Questions)**
---
### QA6
✍What is memo used for? How is React.memo different from useMemo ( two very different things )
React.memo() is similar to PureComponent in that it will help us control when our components rerender. With PureComponent and React.memo(), we can have only some components render.

**[⬆](#Questions)**
---
### QA7

**[⬆](#Questions)**
---
### QA8
✍What is a reducer?
A reducer is a function which takes two arguments, i.e., the current state and an action and returns based on both arguments a new state. 

**[⬆](#Questions)**
---

