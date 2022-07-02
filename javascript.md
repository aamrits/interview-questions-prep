# Questions
## JavaScript
- [How does JavaScript works. JS engine archietecture. How JavaScript is so fast.](#Q1)
- [Explain event loop.](#Q2)
- [Explain execution context.](#Q3)
- [What is hoisting? Explain with example.](#Q4)
- [Scope chain.](#Q5)
- [var, let, const,Temporal Dead Zone.](#Q6)
- [What is type of null, undefined, function, NaN.](#Q7)
- [null and undefined.](#Q8)
- [typeOf() ](#Q9)
- [Difference between == and === ](#Q10)
- [How does this keyword work? Provide some examples.](#Q11)
- [Difference between call, apply and bind. Give example. ](#Q12)
- [What is closure and what are the advantages of using closure. ](#Q13)
- [Function statement, Function Expression, Anonymous Function, Named Function Expression, First Class Function, Higher-order Function.](#Q14)
- [Difference between arguments and parameters.](#Q15)
- [Function overiding and overloading.](#Q16)
- [OOPs concept in JS](#Q17)
   - Objects
   - classes
   - Encapsulation (constructor functions)
   - Inheritance (prototypal inheritance) with example
- [Implement debouncing.](#Q18)
- [Implement throttling.](#Q19)
- [IIFE (Immediately Invoked Function Expression)](#Q20)
- [Function currying with example.](#Q21)
- [Difference between setTimeout vs setInterval.](#Q22)
- [Implement setInterval using setTimeout](#Q23)
- [What is the difference between window, screen, and document in Javascript?](#Q24)
- [Falsy values in js.](#Q25)
- [What is a strict mode in js?](#Q26)
- [What is eval()?](#Q27)
- [What are reference error and syntax error?](#Q28)
- [JavaScript data types.](#Q29)
- [Insert content in HTML using JavaScript. ](#Q30)
- [HTML DOM (Document Object Model)](#Q31)
- [BOM (Browser Object Model)](#Q32)
- [alert, confirm and popup](#Q33)
- [cookies, sessions and localstorage](#Q34)
- [Array methods](#Q35)
- [String methods](#Q36)
- [Different errors in JS.](#Q37)
- [isNaN() ](#Q38)

## JavaScript ES6
- [Explain features of ES6.](#QA1)
- [Difference between the arrow and normal function.](#QA2)
- [Explain what the callback function is and provide a simple example.](#QA3)
- [Promises](#QA4)
- [Async-await](#QA5)
- [Spread operator, rest and destructing.](#QA6)
- [Iterators.](#QA7)
- [Import and export.](#QA8)
- [Pollyfill for map, reduce, filter and forEach.](#QA9) 
- [Pollyfill for call, apply,bind.](#QA10)
- [Polyfill for flat method](#QA11)
   - Infinite depth flatten and flatten by a certain number
   - Implement both recursive and iterative approaches
- [Polyfill for promises and Promise.all](#QA12)
- [Event bubbling, event capturing/trickling, and event delegation.](#QA13)
- [Explain map(), forEach(), filter() and reduce() higher order functions](#QA14) 
- [Difference between stop propagation and prevent default method.](#QA15)
- [JavaScript Design Patterns](#QA16)

## JavaScript Array, Objects, etc.
- [Explain with examples of a deep and shallow copy.](#QB1)
- [Remove falsy values from Array.](#QB2)
- [splice vs slice method.](#QB3)
- [What is array destructuring.](#QB4)
- [Different ways of creating an object.](#QB5)
- [Object creation patterns.](#QB6)
- [Deep copy of an object.](#QB7)
- [Add/remove properties from Objects.](#QB8)
- [Looping through Array and Objects.](#QB9)

## JavaScript Misc
- [What are the advantages of using Axios over Fetch API.](#QC1)
- [Explain the CORS mechanism.](#QC2)
- [Explain JWT in detail.](#QC3)
- [Use AJAX and XMLHttpRequest to get reponse from an URL. ](#QC4)

## Web Performance
- [Critical rendering path (must watch)](#QD1)
- [Caching](#QD2)
   - HTTP requests: Headers like Cache-Control, ETag, and Transfer-Encoding
- [Network waterfall](#QD3)
- [Async, defer script attributes](#QD4)
- [preconnect, preload, prefetch](#QD5)
- [Image optimization (jpeg v/s png v/s svg)](#QD6)
- [Bundle size optimisation ( good to have webpack basics)](#QD7)

## Web security
- [XSS ( understand why we need cookies )](#QE1)
- [CSRF](#QE2)
- [Content security policy](#QE3)

# Answers
#### Q1 
### ✍How does JavaScript works. JS engine archietecture. How JavaScript is so fast.
JavaScript is a **dynamically** typed language unlike C++.

```js
var x = 17;
```

- When we define `x`, we don't worry about the type of the variable or the memory it will take. This makes prototyping fast.
- JS Engine use JIT (Just In Time) Compilation. It interpretes and compiles at the same time.
- Modern JS engines are 2 compilers, one is optimizing compiler. Its job is to re-compile `hot functions` with type information and optimize it in the process.
- If the type is changed, then it has to de-optimize (small performance hit).
- Google Chrome browser's V8 engine is the fastest. Here, the baseline compiler is Ignition. The optimising compiler is Turbofan. The machine code is called Bytecode.

![JS Engine 1](assets/js-engine1.png)
![JS Engine](assets/js-engine.png)

**[⬆](#Questions)**
---
#### Q2
### ✍Explain event loop.
![Event Loop](assets/event-loop1.png)

JavaScript is a **single threaded language**, i.e., it can execute one line at a time.
1. The JavaScript Engine has a **memory heap** and **call stack** . Even before executing a single line of code, JS stores variables and functions in the heap. *Variables are assigned **undefined** and functions are stored as it*.

2. After that **Global Execution Context** is created in the call stack. Each line is executed synchronously and after execution, gets popped out of the call stack.

3. All the asynchronous events like `setTimeout` or **DOM APIs** or `XMLHttpRequest` are part of the **WebAPI**. When the timer expires or the response is fetched, it goes to the **callback queue**, where it waits for the call stack to be clear. Event loop checks this functionality.

5. Once the call stack is empty, event loop pushes the callback functions, which are waiting in the callback queue, to the call stack, to be executed. 

6. Suppose, there is a fetch request (**Promise**) and also a setTimeout. In this case, Promises gets pushed to the **microtask queue** or **priority queue**, after getting response. Microtask queue has more priority than callback queue (or task queue). So once the call stack is cleared, functions in the microtask queue gets pushed. After that callback functions in callback queue gets executed.
![Event Loop 2](assets/event-loop2.png)

**[⬆](#Questions)**
---
#### Q3
### ✍Explain execution context.
1. Before even code is executed, there is Global Execution Context. In GEC, `window` and `this` is available to us. Here, `this` refers to `window` Object.

2. Once code is executed, variable names are assigned value. For a function, a separate Execution Context is created. Here, `arguments` and `this` is available to us. For each function call, seperation Execution Contexts are created.

3. Execution Context has 2 phases: **Creation** and **Execution**.
![Execution Context](assets/execution-context.png)

**[⬆](#Questions)**
---
#### Q4
### ✍What is hoisting? Explain with example.
JavaScript Hoisting refers to the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.

`var` variables are initialized with undefined, `let` and `const` variables are not initialized.

Functions are hoisted as it is. Hence, we can run a function before we declare.

**[⬆](#Questions)**
---
#### Q5
### ✍Scope chain.
It refers to the **lexical environment**. If a variable or a function is not declared in its scope, but it is declared in its lexical parent, then that variable can be accessed in the function also.

```js
function name() {
   var name = "Amrit";
   function displayName() {
      console.log(name);
   }
   displayName();
}
name();
```

**[⬆](#Questions)**
---
#### Q6
### ✍var, let, const,Temporal Dead Zone.
- `var` declarations are globally scoped or function scoped while `let` and `const` are block scoped.

- `var` variables can be updated and re-declared within its scope; `let` variables can be updated but not re-declared; `const` variables can neither be updated nor re-declared.

- They are all hoisted to the top of their scope. But while var variables are initialized with undefined, `let` and `const` variables are not initialized.

- While `var` and `let` can be declared without being initialized, `const` must be initialized during declaration.

**[⬆](#Questions)**
---
#### Q7
### ✍What is type of null, undefined, function, NaN.

```js
console.log(typeof null);  // "object"
console.log(typeof undefined); // "undefined"
console.log(typeof function demo() {}); // "function"
console.log(typeof NaN); // "number"
```

**[⬆](#Questions)**
---
#### Q8
### ✍null and undefined.

- the type of undefined is `undefined`, whereas null is `object`.

- When a variable is declared but no value is assigned, then it shows undefined. But we can assign to a variable. So `null` is an assignment value.

**[⬆](#Questions)**
---
#### Q9
### ✍typeOf() 

```js
console.log(typeof undefined); // "undefined"
console.log(typeof null);  // "object"
console.log(typeof "John"); // "string"
console.log(typeof 3.14); // "number"
console.log(typeof x); // "undefined"
console.log(typeof true); // "boolean"
console.log(typeof {'Name': 'Amrit', 'age': 23}); // "object"
console.log(typeof [1, 2, 3]); // "object"
console.log(typeof function demo() {}); // "function"
```

**[⬆](#Questions)**
---
#### Q10
### ✍Difference between `==` and `===` .
`==` converts the variable values to the same type before performing comparison. This is called **type coercion**.

`===` does not do any type conversion (coercion) and returns true only if both values and types are identical.

**[⬆](#Questions)**
---
#### Q11
### ✍How does `this` keyword work? Provide some examples.
- Case 1
```js
function displayName() {
   console.log('John Doe', this);
}
displayName();
```

In case `this` is the window object as internally `window.displayName()` is getting called.

- Case 2
```js
let obj1 = {
   displayName: function() {
      console.log('John Doe', this);
   }
}
obj1.displayName();
```

In case 2, this will refer to `obj1`.

- Case 3: `this` keyword works dynamically. Let's take another example.
```js
const obj = {
   name: 'Amrit',
   sayHello: function() {
      console.log('Hello', this);
      var sayBye = function() {
         console.log('Bye', this);
      }
      sayBye();
   }
}
obj.sayHello();
// Hello {name: 'Amrit', sayHello: ƒ}
// Bye Window {window: Window, self: Window, document: document, name: '', location: Location, …}
```

- In case 3, `sayHello()` will refer to obj as we're calling as `obj.sayHello()`. But `sayBye()` will refer to `window` object as we're simply calling the function `sayBye()`.
- But if we will use arrow function in `sayBye()`, arrow function will check the surrounding environment where is defined and log `this`. 

```js
const obj = {
   name: 'Amrit',
   sayHello: function() {
      console.log('Hello', this);
      var sayBye = () => {
         console.log('Bye', this);
      }
      sayBye();
   }
}
obj.sayHello();
// Hello {name: 'Amrit', sayHello: ƒ}
// Bye {name: 'Amrit', sayHello: ƒ} // the surrounding env is sayHello function
```
In this case, arrow function is defined within `obj`. So this will log `obj` object.

**[⬆](#Questions)**
---
### Q12
✍Difference between `call`, `apply` and `bind`. Give example.

When we call this below function, internally `displayName()` is called as `displayName.call()`. Also we can call this function with `apply()` like this also, `displayName.apply()` 

```js
function displayName() {
   console.log('John Doe');
}
displayName(); // John Doe
displayName.call(); // John Doe
```

- `call()`
```js
let user1 = {
   name: 'John',
   battery: 30,
   chargeBattery: function(isCharging, isNotSwitchedOff) {
      this.battery = (isCharging && isNotSwitchedOff) ? 100 : '';
   }
}
let user2 = {
   name: 'Ron',
   battery: 70
}
// call the chargeBattery() present in user1 and use it in user2 
user1.chargeBattery.call(user2, true, true); /
console.log(user1); // {name: 'John', battery: 30, chargeBattery: ƒ}
console.log(user2); //{name: 'Ron', battery: 100}
```

- for `apply()`, all the arguments should be in array.

```js
let user1 = {
   name: 'John',
   battery: 30,
   chargeBattery: function(isCharging, isNotSwitchedOff) {
      this.battery = (isCharging && isNotSwitchedOff) ? 100 : '';
   }
}
let user2 = {
   name: 'Ron',
   battery: 70
}
// call the chargeBattery() present in user1 and use it in user2 
user1.chargeBattery.apply(user2, [true, true]); // for apply(), all the arguments should be in array
console.log(user1); // {name: 'John', battery: 30, chargeBattery: ƒ}
console.log(user2); // {name: 'Ron', battery: 100}
```

- `bind()` returns a function so that later we can call that function.
```js
let user1 = {
   name: 'John',
   battery: 30,
   chargeBattery: function(isCharging, isNotSwitchedOff) {
      this.battery = (isCharging && isNotSwitchedOff) ? 100 : '';
   }
}
let user2 = {
   name: 'Ron',
   battery: 70
}
let output = user1.chargeBattery.bind(user2, true, true);
output();
console.log(user2); //{name: 'Ron', battery: 100}
```

**[⬆](#Questions)**
---
#### Q13
### ✍What is closure and what are the advantages of using closure.
**Functions bundled with its lexical scope is called closure.**

```js
function x() {
   let a = 8;
   function y() {
      console.log(a);
   }
   return y;
}
let z = x(); // returns the function y
console.log(z); // 8
```

- Here, we have to understand when we call `x()`, the `function y` will be returned along with its lexical scope. So even if `function x()` is no longer executed and it doesn't exist anymore, in the variable z, the `function y()` is present along with its lexical scope. So the reference of `a` is present.
- So when we call `z()`, 8 gets printed. In other words, it remembers its lexical scope. The reference to `a` is also stored in variable `z`. Hence 8 gets printed as `a = 8`. 
- The reference of `a` is stored. Hence, if we change `a = 12` after `function y()`, the value will change to 12 and it will console log 12.

- Uses of Closure
   - Module Design Pattern
   - Currying
   - Functions like once()
   - Memoize
   - Maintaining state in async world
   - setTimeouts
   - Iterators
- Limitations
   - The variables and functions are not garbage collected as its there in scope. So leads to memory leaks and memory waste.

**[⬆](#Questions)**
---
#### Q14
### ✍Function statement, Function Expression, Anonymous Function, Named Function Expression, First Class Function, Higher-order Function.
- **Function Statement or Function Declaration**

```js
function a() {
   console.log('a is called');
}
a(); // a is called
```

- **Function Expression**: Here, it is treated as a variable, so it is not hoisted. On the other hand, Function Statement is hoisted.
```js
let b = function () {
   console.log('b is called');
}
b();  // b is called
```

- **Anonymous Functions** are used when functions are used as values, just like Function Expression as an example.

- **Named Function Expression**
```js
let c = function abc() {
   console.log('c is called', abc);
}
c(); 
// c is called ƒ abc() {
//    console.log("c is called", abc);
// }
```

We can't call this function like `abc()` as it is defined as a value .
- **First Class Function** (or First Class Citizens)
The ability to pass functions as values or pass functions inside a function as arguments is known as First Class Function. We can also return a function from function. 

- **Higher-order function** is a function that accepts functions as parameters and/or returns a function.

**[⬆](#Questions)**
---
#### Q15
### ✍Difference between arguments and parameters.
```js
function sum(a,b) {
   return a+b;
}
console.log(sum(2, 3));
```
a, b are the parameters. 2, 3 are **arguments**.
The values which we pass insde a function are called as **arguments** and the labels or identiers which gets those values are known as **parameters**.

**[⬆](#Questions)**
---
#### Q16
### ✍Function overiding and overloading.
*Function overloading* is a feature of object oriented programming where two or more functions can have the same name but different parameters. When a function name is overloaded with different jobs it is called Function Overloading. But this is present C++. **In JavaScript, there is no Function Overloading**.

JavaScript supports *overriding*, so if you define two functions with the same name, the last one defined will override the previously defined version and every time a call will be made to the function, the last defined one will get executed.

**[⬆](#Questions)**
---

#### Q17
### ✍OOPs concept in JS (Objects, Classes, Encapsulation(constructor), Inheritance(prototypal with example))
- consider the below object
```js
function DogObject(name, age) {
    this.name = name;
    this.age = age;
}
DogObject.prototype.speak = function() {
    return "I am a dog";
}
let john = new DogObject("John", 45);
```
- Here, `speak()` function is attached to the DogObject by using `prototype`. This is known as **prototype chaining**.

- `class`
```js
class Animals { // encapsulation: class holds the data variables along with the functions
   constructor(name, specie) {
      this.name = name;
      this.specie = specie;
   }
   sing() {
      return `${this.name} can sing`;
   }
   dance() {
      return `${this.name} can dance`;
   }
}
let bingo = new Animals("Bingo", "Hairy"); // inheritance
console.log(bingo);

// OUTPUT
// {
//   name: "Bingo",
//   specie: "Hairy"
// }
```
- As you see, `Class` behaves the same way as `Object`. It is just a syntactic sugar on objects.

**[⬆](#Questions)**
---
#### Q18
### ✍Implement debouncing.
In JavaScript, a *debounce* function makes sure that your code is only triggered once per user input.

Let's say that we want to show suggestions for a search query, but only after a visitor has finished typing it. We have to avoid API call on every key change.

The *debounce* is a special function that handles two tasks:
- Allocating a scope for the timer variable
- Scheduling your function to be triggered at a specific time

```js
function debounce(func, timeout = 300){
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => { func.apply(this, args); }, timeout);
  };
}
function saveInput(){
  console.log('Saving data');
}
const processChange = debounce(() => saveInput());

// HTML
<input type="text" onkeyup="processChange()" />
```

When a visitor writes the first letter and releases the key, the debounce first resets the timer with clearTimeout(timer). Then it schedules the provided function, `saveInput()` to be invoked in 300 ms.

Now let's say that the visitor keeps writing, so each key release triggers the debounce again. Every invocation needs to reset the timer, or, in other words, cancel the previous plans with `saveInput()`, and reschedule it for a new time, 300 ms in the future. This goes on as long as the visitor keeps hitting the keys under 300 ms.

**[⬆](#Questions)**
---
#### Q19
### ✍Implement throttling.
*Throttling* is used to call a function after every millisecond or a particular interval of time only the first click is executed immediately.

Suppose a button is clicked 500 times then the function will be clicked 500 times. By throttling, we can avoid this.

```html
<button id="throttle">Click Me</button>
```

```js
const throttleFunction = (func, delay) => {
   let prev = 0;
   return (...args) => {
      let now = new Date().getTime();

      if((now - prev) > delay) {
         prev = now;
         return func(...args);
      }
   }
}

document.querySelector("#throttle").addEventListener("click", throttleFunction(() => {
   console.log("button is clicked");
}, 1500));

```

**[⬆](#Questions)**
---
#### Q20
### ✍IIFE (Immediately Invoked Function Expression)
An Immediately-Invoked Function Expression, or IIFE for short executes immediately after it’s created. The primary reason to use an IIFE is to obtain data privacy. Because JavaScript's var scopes variables to their containing function, any variables declared within the IIFE cannot be accessed by the outside world.
```js
var budgetController = (function() {
    var x = 23;

    function add(a) {
        return x + a;
    }

    return {
        publicTest: function (b) {
            console.log(add(b)); 
        } // has access to x and add() as its a closure. even if IIFE is returned immediately, closure still has access to x and add().
    }
})();

// this is a IIFE which helps in data privacy. x and add() are private and so can't be accessed from outside. We use return object in order to get the value when we access from outside.

budgetController.x
// undefined

budgetController.add(5)
// Uncaught TypeError: budgetController.add is not a function\

budgetController.publicTest(5)
// 28
```

**[⬆](#Questions)**
---
#### Q21
### ✍Function currying with example.
Currying is a transformation of functions that translates a function from callable as `f(a, b, c)` into callable as `f(a)(b)(c)`.

Currying doesn’t call a function. It just transforms it.
```js
function curry(a) {
   return function (b) {
      return function (c) {
         return a * b * c;
      };
   };
}
console.log(curry(11)(2)(3));
```

**[⬆](#Questions)**
---
#### Q22
### ✍Difference between setTimeout vs setInterval.
###### setTimeout(function, milliseconds)
Executes a function, after waiting a specified number of milliseconds.

```js
function showTime() {
   setTimeout(function() {
       alert('Hello');
   }, 1000);
}
```

###### setInterval(function, milliseconds)
Same as `setTimeout()`, but repeats the execution of the function continuously.

```js
<button onclick="showTime()">Show Time</button>
<p id="time"></p>

function showTime() {
   setInterval(function() {
       var d = new Date();
       var t = d.toLocaleTimeString();
       document.getElementById("time").innerHTML = t;
   }, 1000);
}
```

###### clearInterval()
The `clearInterval()` method stops the execution of the function specified in `setInterval()`.

```js
<button onclick="startTime()">Start</button>
<button onclick="stopTime()">Stop</button>

function startTime() {
   myVar = setInterval(function(){ myTimer() }, 1000);

   function myTimer() {
       var d = new Date();
       var t = d.toLocaleTimeString();
       document.getElementById("time").innerHTML = t;
   }
}

function stopTime() {
   clearInterval(myVar);
}
```

**[⬆](#Questions)**
---
#### Q23
### ✍Implement setInterval using setTimeout.

```js
function customSetInterval (cb, interval) {
  return setTimeout( () => {
    if (typeof cb == 'function') {
      cb();
      customSetInterval(cb, interval);
    } else {
      console.error(new Error('Expecting a function as a callback'))
    }
  }, interval);
}

function resetCustomSetInterval (id) {
  clearTimeout(id);
}

function hello (){
  console.log('hello');
}
 
let id = customSetInterval(hello, 1000);
```

**[⬆](#Questions)**
---
#### Q24
### ✍What is the difference between window, screen, and document in Javascript?
The`window` is the actual global object.
The`screen` is the screen, it contains properties about the user's display.
The`document` is where the DOM is.

Below are the main differences between window and document.

| Window | Document |
|---- | ---------
| It is the root level element in any web page  | It is the direct child of the `window` object. This is also known as Document Object Model(DOM) |
| By default `window` object is available implicitly in the page | You can access it via `window.document` or document.  |
| It has methods like `alert()`, `confirm()` and properties like `document`, `location` | It provides methods like `getElementById`, `getElementsByTagName`, `createElement` etc  |

![My image](https://i.stack.imgur.com/BkAjU.jpg)

**[⬆](#Questions)**
---
#### Q25
### ✍Falsy values in js.
There are only six falsey values in JavaScript, `undefined` , `null` , `NaN` , `0` , "" (empty string), and `false`.

You can apply the filter method on the array by passing Boolean as a parameter. This way it removes all falsy values(0, undefined, null, false and "") from the array.

```js
const myArray = [false, null, 1,5, undefined]
myArray.filter(Boolean); // [1, 5] // is same as myArray.filter(x => x);
```

**[⬆](#Questions)**
---
#### Q26
### ✍What is a strict mode in js
Strict Mode is a new feature in ECMAScript 5 that allows you to place a program, or a function, in a “strict” operating context.

- Strict mode makes it easier to write **secure** JavaScript.
- Strict mode changes previously accepted **bad syntax** into real errors.
- As an example, in normal JavaScript, mistyping a variable name creates a new global variable. In **strict** mode, this will throw an error, making it impossible to accidentally create a global variable.

```js
x = 3.14;   // This will cause an error because x is not declared
myFunction();

function myFunction() {
  "use strict";
  y = 3.14;   // This will cause an error
}
```

**[⬆](#Questions)**
---
#### Q27
### ✍What is eval()
The eval() function evaluates JavaScript code represented as a string. The string can be a JavaScript expression, variable, statement, or sequence of statements.

```js
console.log(eval('1 + 2')); //  3
```

**[⬆](#Questions)**
---
#### Q28
### ✍What are reference error and syntax error?
The `ReferenceError` object represents an error when a variable that doesn't exist (or hasn't yet been initialized) in the current scope is referenced.

Syntax error is due wrong syntax written in the code.

**[⬆](#Questions)**✍
---

#### Q29
### ✍JavaScript data types.
- Number
- String
- Boolean
- Undefined
- Null

**[⬆](#Questions)**
---
#### Q30
### ✍Insert content in HTML using JavaScript.
- `document.getElementById('id').innerHTML`

**[⬆](#Questions)**
---
#### Q31
### ✍HTML DOM (Document Object Model)\
HTML *Document Object Model (DOM)* is a standard Object model and programming interface for HTML. It defines all HTML elements as objects, the properties of HTML elements, the methods to access all HTML elements and the events for all HTML objects.

In general, the HTML DOM is a standard for how to get, change, add, or delete HTML elements.

Some examples of DOM
- `document.getElementById()`
```js
<input type="text" id="text1" />
document.getElementById('text1').value = 9999;
```

- `document.querySelector()`
```js
document.querySelector('.demo').innerHTML = "Hello";
```

- `document.getElementsByTagName()`
```js
<h4 id="demo">Check the console for details.</h4>
<ul>
       <li>Ice cream</li>
       <li>Honey</li>
       <li>Vanilla</li>
</ul>

// The getElementsByTagName() method returns a collection of all elements in the document with the specified tag name.
var x = document.getElementsByTagName("li");
document.getElementById("demo").innerHTML = x[1].innerHTML;
```

- `document.getElementsByClassName()`
```js
<h4 id="demo" class="demo">Check the console for details.</h4>
var x = document.getElementsByClassName('demo');
x[0].innerHTML = 'hello';
```

- `element.innerHTML` (new html content)
```js
<h4 id="demo" class="demo">Check the console for details.</h4>
document.getElementById('demo').innerHTML = "inner html changed";
```

- `element.attribute` (new value)
```js
<a href="#" id="link">Link</a>
<button id="text1">Click me</button>
var a = document.getElementById('link').attributes.length;
console.log(a); //2

document.getElementById('link').setAttribute('href', 'https://www.google.co.in/');
document.getElementById('text1').setAttribute('type', 'button');
```

- `element.style.property` (new style)
```js
document.getElementById('link').style.color = "red";
document.getElementById('link').style.textTransform = "uppercase";
```

- `document.createElement` (element), `document.removeChild` (element), `document.appendChild` (element),  `document.replaceChild` (element), `document.removeChild` (element)

```js
// document.createElement(element), document.removeChild(element),  document.appendChild(element),  document.replaceChild(element),  document.removeChild(element)
var btn = document.createElement("button");
var t = document.createTextNode("Click Me");
var nw = document.createTextNode("New");
btn.appendChild(t);
btn.replaceChild(nw, t);
document.getElementById('link').appendChild(btn);
document.getElementById('link').removeChild(btn);
```

**[⬆](#Questions)**
---
#### Q32
### ✍BOM (Browser Object Model)
The Browser Object Model (BOM) allows JavaScript to "talk to" the browser.
- The Window Object
   - `window.innerHeight`: the inner height of the browser window (in pixels)
   - `window.innerWidth`: the inner width of the browser window (in pixels)
   - `window.open()`: open a new window
   - `window.close`: closes the current window
   - `window.moveTo`: moves the current window
   - `window.resizeTo`: resize the current window
```js
// window.innerHeight()
console.log("Window innerWidth: " + innerWidth);
console.log("Window innerHeight: " + innerHeight);

// window.open()
<button type="button" id="btn" onclick="a()">Click me</button>

function a() {
   var x = window.open("", "MsgWindow", "width=200,height=100");
   x.document.write("<p>This is 'MsgWindow'. I am 200px wide and 100px tall!</p>")
}
```

- The Window Screen
The window.screen object contains information about the user's screen.
   - `screen.width`
   - `screen.height`
   - `screen.availWidth`
   - `screen.availHeight`
   - `screen.colorDepth`
   - `screen.pixelDepth`

- The Window Location
The `window.location` object can be used to get the current page address (URL) and to redirect the browser to a new page.
   - `window.location.href` returns the href (URL) of the current page
   - `window.location.hostname` returns the domain name of the web host
   - `window.location.pathname` returns the path and filename of the current page
   - `window.location.protocol` returns the web protocol used (http: or https:)
   - `window.location.assign` loads a new document

- The Window History
   - `history.back()` -same as clicking back in the browser
   - `history.forward()` -same as clicking forward in the browser

- The Window Navigator
The `window.navigator` object contains information about the visitor's browser. The `window.navigator` object can be written without the window prefix.

**[⬆](#Questions)**
---
#### Q33
### ✍alert, confirm and popup
- Alert box: `window.alert()` instructs the browser to display a dialog with an optional message, and to wait until the user dismisses the dialog.

```js
alert('Hi There!');
```

- Confirm box: `window.confirm()` instructs the browser to display a dialog with an optional message, and to wait until the user either confirms or cancels the dialog.

```js
if (confirm("Press a button!")) {
   console.log('You pressed OK');
} else {
   console.log('You pressed cancelled.');
}
```

- Prompt box: `window.prompt()` instructs the browser to display a dialog with an optional message prompting the user to input some text, and to wait until the user either submits the text or cancels the dialog.

```js
var person = prompt("Please enter your name", "");

if (person == null || person == "") {
   console.log('You cancelled the prompt');
} else {
   console.log("Hello " + person + "! How are you today?");
}
```

**[⬆](#Questions)**
---
#### Q34
### ✍cookies, sessions and localstorage
| Cookies                   | Sessions           | Localstorage  |
| ------------------------  |:------------------------:| ------------------------:|
| The storage capacity of Cookies is 4KB | The storage capacity of session storage is 5MB |  The storage capacity of local storage is 5MB/10MB |
| Cookies expire based on the setting and working per tab and window | It’s session-based and works per window or tab. This means that data is stored only for the duration of a session, i.e., until the browser (or tab) is closed | As it is not session-based, it must be deleted via javascript or manually |
| Both clients and servers can read and write the cookies | The client can only read local storage | The client  can only read local storage |
| Data transfer to the server is exist | There is no transfer of data to the server | There is no transfer of data to the server |
| It is supported by all the browser including older browser | There are fewer old browsers that support it | There are fewer old browsers that support it |

**[⬆](#Questions)**
---
#### Q35
### ✍Array methods
Some of the common Array methods are
- `Array.prototype.concat()`: The `concat()` method is used to merge two or more arrays. This method returns a new array.
- `Array.prototype.indexOf()`: The `indexOf()` method returns the first index at which a given element can be found in the array, or -1 if it is not present.
- `Array.prototype.join()`: The `join()` method creates and returns a new string by concatenating all of the elements in an array, separated by commas or a specified separator string.
- `Array.prototype.shift()`: The `shift()` method removes the first element from an array and returns that removed element. This method changes the length of the array.
- `Array.prototype.unshift()`: The `unshift()` method adds one or more elements to the beginning of an array and returns the new length of the array.
- `Array.prototype.pop()`:The `pop()` method removes the last element from an array and returns that element. This method changes the length of the array.
- `Array.prototype.push()`: The `push()` method adds one or more elements to the end of an array and returns the new length of the array.
- `Array.prototype.reverse()`: The `reverse()` method reverses an array in place. The first array element becomes the last, and the last array element becomes the first.
- `Array.prototype.slice()`: The `slice()` method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. The original array will not be modified.
- `Array.prototype.sort()`: The `sort()` method sorts the elements of an array in place and returns the sorted array.
- `Array.prototype.splice()`: The `splice()` method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place. To access part of an array without modifying it, we use `slice()`.
- `Array.prototype.toString()`: The `toString()` method returns a string representing the specified array and its elements.
- `Array.prototype.map()`: The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array.
- `Array.prototype.filter()`: The `filter()` method creates a new array with all elements that pass the test implemented by the provided function.
- `Array.prototype.reduce()`: The `reduce()` method executes a user-supplied *reducer* callback function on each element of the array, in order, passing in the return value from the calculation on the preceding element. The final result of running the reducer across all elements of the array is a single value.
- `Array.prototype.includes()`: The `includes()` method determines whether an array includes a certain value among its entries, returning `true` or `false` as appropriate.
- `Array.prototype.find()`: The `find()` method returns the value of the first element in the provided array that satisfies the provided testing function. If no values satisfy the testing function, `undefined` is returned.
- `Array.prototype.some()`: The `some()` method tests whether at least one element in the array passes the test implemented by the provided function. It returns a `Boolean`.
- `Array.prototype.fill()`: The `fill()` method changes all elements in an array to a static value, from a start index (default 0) to an end index (default array.length). It returns the modified array.
- `Array.from()`: The `Array.from()` static method creates a new, shallow-copied Array instance from an array-like or iterable object.
- `Array.of()`: The `Array.of()` method creates a new Array instance from a variable number of arguments, regardless of number or type of the arguments
- `Array.isArray()`: The `Array.isArray()` method determines whether the passed value is an `Array`.

```js
/* 
Array.prototype.concat()
Syntax: 
concat()
concat(value0)
concat(value0, value1)
concat(value0, value1, ... , valueN) 
Returns a new Array instance
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var arr2 = ["india", "usa", "uk","china", "russia", "germany"];
console.log(arr1.concat(arr2));

RESULT:
["cricket", "football", "hockey", "baseball", "kabaddi", "india", "usa", "uk", "china", "russia", "germany"]

/* 
Array.prototype.indexOf()
Syntax: 
indexOf(searchElement)
indexOf(searchElement, fromIndex)
Returns first index at which a given element can be found, or -1, if not found
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
console.log(arr1.indexOf("hockey"));
console.log(arr1.indexOf("golf"));

RESULT:
2
-1

/* 
Array.prototype.join()
Syntax: 
join()
join(separator)
Returns String
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
console.log(arr1.join());

RESULT:
cricket,football,hockey,baseball,kabaddi

/* 
Array.prototype.shift()
Syntax: 
shift()
Returns the removed element
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
console.log(arr1.shift());
console.log(arr1);

RESULT:
Cricket
["football", "hockey", "baseball", "kabaddi"]

/* 
Array.prototype.unshift()
Syntax: 
unshift(element0)
unshift(element0, element1)
unshift(element0, element1,... , elementN)
Returns the new length of the array.
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
console.log(arr1.unshift("golf"));
console.log(arr1);

RESULT:
6
["golf", "cricket", "football", "hockey", "baseball", "kabaddi"]

/* 
Array.prototype.pop()
Syntax: 
pop()
Returns that element
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
console.log(arr1.pop());
console.log(arr1);

RESULT:
Kabaddi
["cricket", "football", "hockey", "baseball"]

/* 
Array.prototype.push()
Syntax: 
push(element0)
push(element0, element1)
push(element0, element1, ... , elementN)
Returns the new length of the array.
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
console.log(arr1.push("golf"));
console.log(arr1);

RESULT:
6
["cricket", "football", "hockey", "baseball", "kabaddi", "golf"]

/* 
Array.prototype.reverse()
Syntax: 
reverse()
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
console.log(arr1.reverse());

RESULT:
["kabaddi", "baseball", "hockey", "football", "cricket"]

/* 
Array.prototype.slice()
Syntax: 
slice()
slice(start)
slice(start, end)
Returns a new Array.
*/
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
console.log(arr1.slice(2));
console.log(arr1.slice(1, 3));

RESULT:
["hockey", "baseball", "kabaddi"]
["football", "hockey"]

/* 
Array.prototype.sort()
Syntax: 
sort()
Returns the same Array.
*/
const months = ['March', 'Jan', 'Feb', 'Dec'];
const array1 = [1, 30, 4, 21, 100000];
console.log(months.sort());
console.log(array1.sort());

// ascending order
var numbers = [1, 30, 4, 21, 100000];
numbers.sort(function(a, b) {
  return a - b;
});
console.log(numbers);

RESULT:
["Dec", "Feb", "Jan", "March"]
[1, 100000, 21, 30, 4]
[1, 4, 21, 30, 100000]

/* 
Array.prototype.splice()
Syntax: 
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, item2, itemN)
Returns the same Array.
*/
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb'); // inserts at index 1
console.log(months);

months.splice(4, 1, 'May'); // replaces 1 element at index 4
console.log(months);

RESULT:
["Jan", "Feb", "March", "April", "June"]
["Jan", "Feb", "March", "April", "May"]

/* 
Array.prototype.toString()
Syntax: 
toString()
Returns String.
*/
const array1 = [1, 2, 'a', '1a'];
console.log(array1.toString());

RESULT:
"1,2,a,1a"

/* 
Array.prototype.map()
Syntax: 
map((element) => { ... })
map((element, index) => { ... })
map((element, index, array) => { ... })
Returns new Array.
*/
const array1 = [1, 4, 9, 16];
const map1 = array1.map(x => x * 2);
console.log(map1);

RESULT:
[2, 8, 18, 32]

/* 
Array.prototype.filter()
Syntax: 
filter((element) => { ... })
filter((element, index) => { ... })
filter((element, index, array) => { ... })
Returns new Array.
*/
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result);

RESULT:
["exuberant", "destruction", "present"]

/* 
Array.prototype.reduce()
Syntax: 
reduce((previousValue, currentValue) => { ... } )
reduce((previousValue, currentValue, currentIndex) => { ... } )
reduce((previousValue, currentValue, currentIndex, array) => { ... } )
reduce((previousValue, currentValue, currentIndex, array) => { ... }, initialValue)
Returns new Array.
*/
const array1 = [1, 2, 3, 4];
//  If initialValue is not specified, previousValue is initialized to the first value (of array or string), and currentValue is initialized to the second value (of array or string).
const reducer = (previousValue, currentValue) => previousValue + currentValue; // 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));

console.log(array1.reduce(reducer, 5)); // 5 + 1 + 2 + 3 + 4

RESULT:
10
15

/* 
Array.prototype.includes()
Syntax: 
includes(searchElement)
includes(searchElement, fromIndex)
Returns Boolean.
*/
const array1 = [1, 2, 3, 5, 8, 0];
console.log(array1.includes(2));
console.log(array1.includes(2, 2));

RESULT:
true
false

/* 
Array.prototype.find()
Syntax: 
find((element) => { ... } )
find((element, index) => { ... } )
find((element, index, array) => { ... } )
Returns value of first element.
*/
const array1 = [5, 12, 8, 130, 44];
const found = array1.find(element => element > 10);
console.log(found);

RESULT:
12

/* 
Array.prototype.some()
Syntax: 
some((element) => { ... } )
some((element, index) => { ... } )
some((element, index, array) => { ... } )
Returns Boolean.
*/
const array = [1, 2, 3, 4, 5];
const even = (element) => element % 2 === 0; // checks whether an element is even
console.log(array.some(even));

RESULT:
true

/* 
Array.prototype.fill()
Syntax: 
fill(value)
fill(value, start)
fill(value, start, end)
Returns new Array.
*/
const array1 = [1, 2, 3, 4];
console.log(array1.fill(0, 2, 4)); // fill with 0 from position 2 until position 4
console.log(array1.fill(5, 1)); // fill with 5 from position 1
console.log(array1.fill(6)); // fill with 6 from position 0 to 4 array1.length

RESULT:
[1, 2, 0, 0]
[1, 5, 5, 5]
[6, 6, 6, 6]

/* 
Array.from()
Syntax: 
Array.from(arrayLike, (element) => { ... } )
Array.from(arrayLike, (element, index) => { ... } )
Returns new Array instance.
*/
console.log(Array.from('foo'));
console.log(Array.from([1, 2, 3], x => x + x));

RESULT:
["f", "o", "o"]
[2, 4, 6]

/* 
Array.of()
Syntax: 
Array.of(element0)
Array.of(element0, element1)
Array.of(element0, element1, ..., elementN)
Returns new Array instance.
*/
Array.of(7); // [7]
Array(7); // array of 7 empty slots

Array.of(1, 2, 3); // [1, 2, 3]
Array(1, 2, 3);    // [1, 2, 3]

RESULT:
[7]
[,,,,,,]
[1, 2, 3]
[1, 2, 3]

/* 
Array.isArray()
Syntax: 
Array.isArray(value)
Returns Boolean
*/
Array.isArray([1, 2, 3]);
Array.isArray({foo: 123});
Array.isArray('foobar');
Array.isArray(undefined);

RESULT:
true
false
false
false
```

**[⬆](#Questions)**
---
#### Q36
### ✍String methods
Some of the common String methods are
- `String.prototype.slice()`: The `slice()` method extracts a section of a string and returns it as a new string, without modifying the original string.
- `String.prototype.substring()`: The `substring()` method returns the part of the `string` between the start and end indexes, or to the end of the string.
- `String.prototype.replace()`: The `replace()` method returns a new `string` with some or all matches of a pattern replaced by a replacement. The pattern can be a `string` or a `RegExp`, and the replacement can be a `string` or a `function` to be called for each match. If `pattern` is a string, only the first occurrence will be replaced.
- `String.prototype.toUpperCase()`: The `toUpperCase()` method returns the calling string value converted to uppercase (the value will be converted to a string if it isn't one).
- `String.prototype.toLowerCase()`: The `toLowerCase()` method returns the calling string value converted to lower case.
- `String.prototype.concat()`: The `concat()` method concatenates the string arguments to the calling string and returns a new string.
- `String.prototype.trim()`: The `trim()` method removes whitespace from both ends of a string and returns a new string, without modifying the original string. Whitespace in this context is all the whitespace characters (space, tab, no-break space, etc.) and all the line terminator characters (LF, CR, etc.).
- `String.prototype.padStart()`: The `padStart()` method pads the current string with another string (multiple times, if needed) until the resulting string reaches the given length. The padding is applied from the start of the current string.
- `String.prototype.padEnd()`: The `padEnd()` method pads the current string with a given string (repeated, if needed) so that the resulting string reaches a given length. The padding is applied from the end of the current string.
- `String.prototype.charAt()`: This `charAt` method returns a new string consisting of the single UTF-16 code unit located at the specified offset into the string.
- `String.prototype.charCodeAt()`: The `charCodeAt()` method returns an integer between 0 and 65535 representing the UTF-16 code unit at the given index.
- `String.prototype.split()`: The `split()` method divides a `String` into an ordered list of substrings, puts these substrings into an array, and returns the array.
- `String.prototype.match()`: The `match()` method retrieves the result of matching a string against a `regular expression`.
- `String.prototype.matchAll()`: The `matchAll()` method returns an iterator of all results matching a string against a `regular expression`, including `capturing groups`.
- `String.prototype.search()`: The `search()` method executes a search for a match between a regular expression and this String object.
- `String.prototype.toString()`: The `toString()` method returns a string representing the specified object.
- `String.prototype.valueOf()`: The `valueOf()` method returns the primitive value of a `String` object.
- `String.prototype.indexOf()`: The `indexOf()` method, given one argument: a substring to search for, searches the entire calling string, and returns the index of the first occurrence of the specified substring. Given a second argument: a number, the method returns the first occurrence of the specified substring at an index greater than or equal to the specified number.
- `String.prototype.includes()`: The `includes()` method performs a case-sensitive search to determine whether one string may be found within another string, returning true or false as appropriate.

```js
/* 
String.prototype.slice()
Syntax: 
slice(beginIndex)
slice(beginIndex, endIndex)
Returns a new String
*/
const str = 'The quick brown fox jumps over the lazy dog.';
console.log(str.slice(31));
console.log(str.slice(4, 19));
console.log(str.slice(-4)); // If negative, slice() begins extraction from str.length + beginIndex

RESULT:
"the lazy dog."
"quick brown fox"
"dog."

/* 
String.prototype.substring()
Syntax: 
substring(indexStart)
substring(indexStart, indexEnd)
Returns a new String
*/
const str = 'Mozilla';
console.log(str.substring(2));
console.log(str.substring(1, 3));

RESULT:
"zilla"
"oz"

/* 
String.prototype.replace()
Syntax: 
replace(regexp, newSubstr)
replace(regexp, replacerFunction)
Returns a new String 
*/
const p = 'The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?';
console.log(p.replace('dog', 'monkey'));

const regex = /Dog/i;
console.log(p.replace(regex, 'ferret'));

RESULT:
"The quick brown fox jumps over the lazy monkey. If the dog reacted, was it really lazy?"
"The quick brown fox jumps over the lazy ferret. If the dog reacted, was it really lazy?"

/* 
String.prototype.toUpperCase()
Syntax: 
toUpperCase()
Returns a new String converted to uppercase
*/
const sentence = 'The quick brown fox jumps over the lazy dog.';
console.log(sentence.toUpperCase());

RESULT:
"THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG."

/* 
String.prototype.toLowerCase()
Syntax: 
toLowerCase()
Returns a new String converted to lowercase 
*/
const sentence = 'The quick brown fox jumps over the lazy dog.';
console.log(sentence.toLowerCase());

RESULT:
"the quick brown fox jumps over the lazy dog."

/* 
String.prototype.concat()
Syntax: 
concat(str1)
concat(str1, str2)
concat(str1, str2, ... , strN)
Returns a new String
*/
const str1 = 'Hello';
const str2 = 'World';

console.log(str1.concat(' ', str2));
console.log(str2.concat(', ', str1));

RESULT:
"Hello World"
"World, Hello"

/* 
String.prototype.trim()
Syntax: 
trim()
Returns a new String
*/
const greeting = '   Hello world!   ';
console.log(greeting.trim());

RESULT:
"Hello world!"

/* 
String.prototype.padStart()
Syntax: 
padStart(targetLength)
padStart(targetLength, padString)
Returns a String of the specified targetLength with padString applied from the start.
*/
const str1 = '5';
console.log(str1.padStart(2, '0'));

const fullNumber = '2034399002125581';
const last4Digits = fullNumber.slice(-4);
console.log(last4Digits);
const maskedNumber = last4Digits.padStart(fullNumber.length, '*');
console.log(maskedNumber);

RESULT:
"05"
"5581"
"************5581"

/* 
String.prototype.padEnd()
Syntax: 
padEnd(targetLength)
padEnd(targetLength, padString)
Returns a String of the specified targetLength with ith the padString applied at the end of the current str.
*/
const str1 = 'Breaded Mushrooms';
console.log(str1.padEnd(25, '.'));

const str2 = '200';
console.log(str2.padEnd(5));

RESULT:
"Breaded Mushrooms........"
"200  "

/* 
String.prototype.charAt()
Syntax: 
charAt(index)
Returns a string representing the character
*/
const sentence = 'The quick brown fox jumps over the lazy dog.';
const index = 4;
console.log(`The character at index ${index} is ${sentence.charAt(index)}`);

RESULT:
"The character at index 4 is q"

/* 
String.prototype.charCodeAt()
Syntax: 
charCodeAt(index)
Returns a number representing the UTF-16 code unit value
*/
const sentence = 'The quick brown fox jumps over the lazy dog.';
const index = 4;
console.log(`The character code ${sentence.charCodeAt(index)} is equal to ${sentence.charAt(index)}`);

RESULT:
"The character code 113 is equal to q"

/* 
String.prototype.split()
Syntax: 
split()
split(separator)
split(separator, limit)
Returns An Array of strings
*/
const str = 'The quick brown fox jumps over the lazy dog.';
const words = str.split(' ');
console.log(words);

const chars = str.split('');
console.log(chars[8]);

const strCopy = str.split();
console.log(strCopy);

RESULT:
["The", "quick", "brown", "fox", "jumps", "over", "the", "lazy", "dog."]
"k"
["The quick brown fox jumps over the lazy dog."]

/* 
String.prototype.match()
Syntax: 
match(regexp)
Returns an Array
*/
const paragraph = 'The quick brown fox jumps over the lazy dog. It barked.';
const regex = /[A-Z]/g;
const found = paragraph.match(regex);
console.log(found);

RESULT:
["T", "I"]

/* 
String.prototype.matchAll()
Syntax: 
matchAll(regexp)
Returns an iterator (which is not a restartable iterable) of matches.
*/
const regexp = /t(e)(st(\d?))/g;
const str = 'test1test2';
const array = [...str.matchAll(regexp)];

console.log(array[0]);
console.log(array[1]); 

RESULT:
["test1", "e", "st1", "1"]
["test2", "e", "st2", "2"]

/* 
String.prototype.search()
Syntax: 
search(regexp)
Returns the index of the first match between the regular expression and the given string, or -1 if no match was found.
*/
const paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';
const regex = /[^\w\s]/g; // any character that is not a word character or whitespace

console.log(paragraph.search(regex));
console.log(paragraph[paragraph.search(regex)]);

RESULT:
43
"."

/* 
String.prototype.toString()
Syntax: 
toString()
Returns a string representing the calling object.
*/
const stringObj = new String('foo');

console.log(stringObj);
console.log(stringObj.toString());

RESULT:
{ "foo" }
"foo"

/* 
String.prototype.valueOf()
Syntax: 
valueOf()
Returns a string representing the primitive value of a given String object.
*/
const stringObj = new String('foo');

console.log(stringObj);
console.log(stringObj.valueOf());

RESULT:
{ "foo" }
"foo"

/* 
String.prototype.indexOf()
Syntax: 
indexOf(searchString)
indexOf(searchString, position)
Returns the index of the first occurrence of searchString found, or -1 if not found.
*/
const paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';
const searchTerm = 'dog';
const indexOfFirst = paragraph.indexOf(searchTerm);

console.log(`The index of the first '${searchTerm}' from the beginning is ${indexOfFirst}`);
console.log(`The index of the 2nd '${searchTerm}' is ${paragraph.indexOf(searchTerm, (indexOfFirst + 1))}`);

RESULT:
"The index of the first 'dog' from the beginning is 40"
"The index of the 2nd 'dog' is 52"

/* 
String.prototype.includes()
Syntax:
includes(searchString)
includes(searchString, position) 
Returns Boolean
*/
const sentence = 'The quick brown fox jumps over the lazy dog.';
const word = 'fox';
console.log(`The word '${word}' ${sentence.includes(word) ? 'is' : 'is not'} in the sentence`);

RESULT:
"The word 'fox' is in the sentence"
```

**[⬆](#Questions)**
---
#### Q37
### ✍Different errors in JS.
- `Error` objects are thrown when runtime errors occur. The `Error` object can also be used as a base object for user-defined exceptions.

`Error()`: Creates a `new Error` object.

| Error Name | Description |
|---- | ---------
| EvalError  | An error has occurred in the eval() function |
| RangeError | An error has occurred with a number "out of range"  |
| ReferenceError | An error due to an illegal reference|
| SyntaxError | An error due to a syntax error|
| TypeError | An error due to a type error |
| URIError | An error due to encodeURI() |
| AggregateError | Creates an instance representing several errors wrapped in a single error when multiple errors need to be reported by an operation, for example by `Promise.any()` |

**[⬆](#Questions)**
---
#### Q38
### ✍isNaN()
```js
console.log(isNaN('the'));      //true
console.log(isNaN(25));         //false
console.log(isNaN('23'));       //false
console.log(isNaN(NaN));       // true
console.log(isNaN(undefined)); // true
console.log(isNaN({}));        // true
console.log(isNaN(true));      // false
console.log(isNaN(null));      // false
console.log(isNaN(37));        // false
```

**[⬆](#Questions)**
---
#### QA1
### ✍Explain features of ES6.
- `const` is more powerful than `var`. Once used, the variable can’t be reassigned. In other words, it’s an immutable variable except when it used with objects.
```js
const a = 6;
a = 7;
console.log(a); //Uncaught TypeError: Assignment to constant variable.
```

But if we use an array or an object, we can modify it.
```js
const arr = [1, 2, 3];
arr.push(8);
console.log(arr); //[1, 2, 3, 8]

const arr1 = {
   name: 'amrit',
   age: 30
};
arr1.job = 'developer';
console.log(arr1); //{name: "amrit", age: 30, job: "developer"}
```

- var and let: `let` is block scoped. `var` is function scoped.
- Default parameters in ES6: In ES6, if we use the default parameter, it won’t return `undefined`, and it will use its value when we forget to assign a parameter!
```js
const person = function (name, age = 22) {
   return `Name is ${name} and age is ${age}`
} 
console.log(person('amrit')); //Name is amrit and age is 22
```

- Import and export: `export` allows you to export a module to be used in another JavaScript component. We use `import` to import that module to use it in our component.

**[⬆](#Questions)**
---
#### QA2
### ✍Difference between the arrow and normal function.
The *arrow function* will check where the function is defined and not how the function is called. Please check Q11 about [`this` keyword](#Q11) for more example.
```js
// Example
var x = function() {
   this.val = 1;
   setTimeout(function() {
      this.val++;
      console.log(this.val);
   }, 1);
}
var xx = new x(); //returns NAN as inside setTimeout there is no "this". It doesn't recognize parent "this".

// solution 1
var x1 = function() {
   var that = this; // declare a varibale "that" and assign it "this". (clumpsy)
   this.val = 1;
   setTimeout(function() {
      that.val++;
      console.log(that.val);
   }, 1);
}
var xx1 = new x1(); // 2

//solution 2: using fat arrow as it checks where it is defined. As it is defined within x2, the variable `val` will get updated.
var x2 = function() {          
   this.val = 1;
   setTimeout(() => {
      this.val++;
      console.log(this.val);
   }, 1);
}
var xx2 = new x2(); // 2
```

**[⬆](#Questions)**
---
#### QA3
### ✍Explain what the callback function is and provide a simple example.
- A higher order function is a function that may receive a function as parameter or even return a function. 
- A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

```js
let add = function(num1, num2) {
  return num1 + num2;
}

let multiply = function(num1, num2) {
  return num1 * num2;
}

let divide = function(dividend, divisor) {
  return dividend / divisor;
}

// higher order function
let operation = function(num1, num2, callback) {
  return callback(num1, num2);
}

let sum = operation(3, 5, add);
let multiplyNumber = operation(5, 11, multiply);    
let divideNumber = operation(10, 5, divide);

console.log('The sum is ' + sum); // The sum is 8
console.log('The result of multiplication is ' + multiplyNumber); // The result of multiplication is 55
console.log('The result of division is ' + divideNumber); // The result of division is 2
```

**[⬆](#Questions)**
---
#### QA4
### ✍Promises
Promises are a new feature of ES6. It’s a method to write asynchronous code. It can be used when, for example, we want to fetch data from an API, or when we have a function that takes time to be executed.

The `Promise` Object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

A promise is a returned object to which you attach callbacks, instead of passing callbacks into a function.

Instead of passing like this:
```javascript
createAudioFileAsync(audioSettings, successCallback, failureCallback);
// NOTE: successCallback and failureCallback are callback functions.
```
we would attach like this:
```javascript
createAudioFileAsync(audioSettings).then(successCallback, failureCallback);
```

The `.then()` method takes up to two arguments; the first argument is a callback function for the resolved case of the promise, and the second argument is a callback function for the rejected case. Each `.then()` returns a newly generated promise object.

A Promise is in one of these states:
- **pending**: initial state, neither fulfilled nor rejected.
- **fulfilled**: meaning that the operation was completed successfully.
- **rejected**: meaning that the operation failed.

Promise chain is one of the great things about using promises.

If we were to use 2 or more asynchronous operations, where the subsequent operation starts when the previous operation succeeds, we can simply use the `.then()` function, as it returns a new promise.

```javascript
// Before ES6: classic callback pyramid of doom
doSomething(function(result) {
  doSomethingElse(result, function(newResult) {
    doThirdThing(newResult, function(finalResult) {
      console.log('Got the final result: ' + finalResult);
    }, failureCallback);
  }, failureCallback);
}, failureCallback);

// ES6:
doSomething()
.then(function(result) {
  return doSomethingElse(result);
})
.then(function(newResult) {
  return doThirdThing(newResult);
})
.then(function(finalResult) {
  console.log('Got the final result: ' + finalResult);
})
.catch(failureCallback);

// ES6: with arrow functions
doSomething()
.then(result => doSomethingElse(result))
.then(newResult => doThirdThing(newResult))
.then(finalResult => {
  console.log(`Got the final result: ${finalResult}`);
})
.catch(failureCallback);

// Another example
let cleanRoom = function() {
   return new Promise(function(resolve, reject) {
      resolve("Room is cleaned.");
   });
};

let garbage = function(message) {
   return new Promise(function(resolve, reject) {
      resolve(message + "Garbage is taken.");
   });
};

let iceCream = function(message) {
   return new Promise(function(resolve, reject) {
      resolve(message + "Give Icecream.");
   });
};

cleanRoom().then(function(result) {
   return garbage(result);
}).then(function(result) {
   return iceCream(result);
}).then(function(result) {
   console.log("All tasks finished." + result)
})
```
The arguments to then are optional, and catch(failureCallback) is short for then(null, failureCallback).

From ECMAScript 2017, async/await is used as a wrapper (syntactic sugar) of promises.
```javascript
async function foo() {
  try {
    const result = await doSomething();
    const newResult = await doSomethingElse(result);
    const finalResult = await doThirdThing(newResult);
    console.log(`Got the final result: ${finalResult}`);
  } catch(error) {
    failureCallback(error);
  }
}
```
Whenever a promise is rejected, one of two events is sent to the global scope:
- **rejectionhandled**: Sent when a promise is rejected, after that rejection has been handled by the executor's reject function.
- **unhandledrejection**: Sent when a promise is rejected but there is no rejection handler available.

In both cases, the event has a promise property indicating the promise that was rejected and a reason property that provides the reason given for the promise to be rejected.
```javascript
// Creating a Promise around setTimeout:
setTimeout(() => saySomething("10 seconds passed"), 10*1000);

// Using Promise:
const wait = ms => new Promise(resolve => setTimeout(resolve, ms));
wait(10*1000).then(() => saySomething("10 seconds")).catch(failureCallback);
```

`Promise.resolve()` and `Promise.reject()` are shortcuts to manually create an already resolved or rejected promise respectively.

`Promise.all()` and `Promise.race()` are two composition tools for running asynchronous operations in parallel.

`Promise.all()`:
```javascript
Promise.all([func1(), func2(), func3()])
.then(([result1, result2, result3]) => { /* use result1, result2 and result3 */ });

// NOTE: However, even if one promise fail, Promise.all() will throw error and abort other calls. 
// To avoid this, we can use Promise.allSettled(), which ensures all operations are complete (fulfilled or rejected) before resolving.
```

Promise callbacks are handled as a **MicroTask** and it has *more priority than task queues*.
```javascript
const promise = new Promise(function(resolve, reject) {
  console.log("Promise callback");
  resolve();
}).then(function(result) {
  console.log("Promise callback (.then)");
});

setTimeout(function() {
  console.log("event-loop cycle: Promise (fulfilled)", promise)
}, 0);

console.log("Promise (pending)", promise);

// Output:
// Promise callback
// Promise (pending) Promise {<pending>}
// Promise callback (.then)
// event-loop cycle: Promise (fulfilled) Promise {<fulfilled>}

// Bad example!
doSomething().then(function(result) {
  doSomethingElse(result) // Forgot to return promise from inner chain + unnecessary nesting
  .then(newResult => doThirdThing(newResult));
}).then(() => doFourthThing());
// Forgot to terminate chain with a catch!

// Good example!
doSomething()
.then(function(result) {
  return doSomethingElse(result);
})
.then(newResult => doThirdThing(newResult))
.then(() => doFourthThing())
.catch(error => console.error(error));
```

Few other **methods** of `Promise`:

`Promise.any()`: It takes an iterable of Promise objects. It returns a single promise that resolves as soon as any of the promises in the iterable fulfills, with the value of the fulfilled promise. If no promises in the iterable fulfill (if all of the given promises are rejected), then the returned promise is rejected with an AggregateError, a new subclass of Error that groups together individual errors.

**Syntax:**

`Promise.any(iterable)`

**Return value**
* If iterable passed is empty, then rejected Promise
* If iterable passed contains no promises, then asynchronously resolved Promise.
* A pending Promise in all other cases. The returning Promise is either resolved/rejected asynchronously.

This method is useful for returning the first Promise that fulfills. Unlike `Promise.all()`, which returns an array of fulfillment values, we only get one fulfillment value(assuming at least one promise fulfills). This can be beneficial if we need only one promise to fulfill but we do not care which one does.

Also unlike `Promise.race()`, which returns the first settled value (either fulfillment or rejection), *this method returns the first fulfilled value*. This method will ignore all rejected promises up until the first promise that fulfills.

```javascript
Example:
const pErr = new Promise((resolve, reject) => {
  reject("Always fails");
});

const pSlow = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, "Done eventually");
});

const pFast = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, "Done quick");
});

Promise.any([pErr, pSlow, pFast]).then((value) => {
  console.log(value); // pFast fulfills first
})
// expected output: "Done quick"

// Promise.any() rejects with an AggregateError if no promise fulfills.
Example:
const pErr = new Promise((resolve, reject) => {
  reject('Always fails');
});

Promise.any([pErr]).catch((err) => {
  console.log(err);
})
// expected output: "AggregateError: No Promise in Promise.any was resolved"
```

`Promise.prototype.finally()`: The `finally()` method returns a Promise. When the promise is finally either fulfilled or rejected, the specified callback function is executed. This provides a way for code to be run whether the promise was fulfilled successfully, or instead rejected.
This helps to avoid duplicating code in both the promise's `then()` and `catch()` handlers.

Few use cases:
* Unlike `Promise.resolve(2).then(() => {}, () => {})` (which will be resolved with undefined), `Promise.resolve(2).finally(() => {})` will be resolved with 2.

* Similarly, unlike `Promise.reject(3).then(() => {}, () => {})` (which will be fulfilled with undefined), `Promise.reject(3).finally(() => {})` will be rejected with 3.

**[⬆](#Questions)**
---
#### QA5
### ✍Async-await
**Async** keyword is used to define an asynchronous function, which returns a AsyncFunction object.

**Await** keyword is used to pause async function execution until a Promise is fulfilled, that is resolved or rejected, and to resume execution of the async function after fulfillments. When resumed, the value of the await expression is that of the fulfilled Promise.

Key points:
- `Await` can only be used inside an async function.
- Functions with the `async` keyword will always return a promise.
- Multiple awaits will always run in sequential order under a same function.
- If a promise resolves normally, then await promise returns the result. But in case of a rejection it throws the error, just if there were a throw statement at that line.
- `Async` function cannot wait for multiple promises at the same time.
- Performance issues can occur if using await after await as many times one statement doesn't depend on the previous one.

```js
async function asyncFunction() {

  const promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("i am resolved!"), 1000)
  });

  const result = await promise; 
  // wait till the promise resolves (*)

  console.log(result); // "i am resolved!"
}

asyncFunction();
```

**[⬆](#Questions)**
---
#### QA6
### ✍Spread operator, rest and destructing.
```javascript
// example 1: spread operator
var a = [1, 2, 3];
var b = [4, 5, 6];

a.push(...b); //using spread operator
// Array.prototype.push.apply(a, b);
console.log(a);

// example 2: rest
var dowhatever = ['talk', 'run', 'watch tv'];
var life = ['born', 'walk', 'eat', ...dowhatever, 'die'];
console.log(life);

// example 3: destructuring
const arr = ['a', 'b', 'c'];

for (let [index, elem] of arr.entries()) {
  console.log(index, ': ', elem);
}
```

**[⬆](#Questions)**
---
#### QA7
### ✍Iterators
An iterator is an object which defines a sequence and a return value upon its termination. It implements the Iterator protocol with a next() method which returns an object with two properties: value (the next value in the sequence) and done (which is true if the last value in the sequence has been consumed).

```javascript
var i = [1, 3, 5];

var iterator = i[Symbol.iterator]();

console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
```

**[⬆](#Questions)**
---
#### QA8
### ✍Import and Export
Refer the question about [Features of ES6](#QA1)

**[⬆](#Questions)**
---
#### QA9
### ✍Pollyfill for map, reduce, filter and forEach.
**Pollyfill for forEach**
```js
let albums = ["Bobby Tarantino", "The Incredible True Story", "Supermarket", "Under Pressure"];

// .forEach()
Array.prototype.polyfillForEach = function (callback) {
   for (var i = 0; i < this.length; i++) {
         callback(this[i], i); // currentValue, index
   }
};

albums.polyfillForEach((item, index) => {
   console.log(item, index);
   // Bobby Tarantino,
   // The Incredible True Story,
   // Supermarket,
   // Under Pressure;
});
```

**Pollyfill for map**
```js
Array.prototype.polyfillForMap = function (callback) {
   let arr = [];
   for (let i = 0; i < this.length; i++) {
         arr.push(callback(this[i], i));
   }
   return arr;
}

const resultAlbums = albums.polyfillForMap((item, i) => {
   return `${i} is ${item}`;
});

console.log(resultAlbums);
// ['0 is Bobby Tarantino', '1 is The Incredible True Story', '2 is Supermarket', '3 is Under Pressure']
```

**Pollyfill for filter**
```js
const names = [
   {name: 'Sachin', age: 40},
   {name: 'Rahul', age: 20},
   {name: 'Rohit', age: 30},
   {name: 'Mohan', age: 35},
   {name: 'Shakti', age: 18}
];

Array.prototype.polyfillForFilter = function(callback) {
   let arr = [];
   for (let i = 0; i < this.length; i++) {
      if (callback(this[i], i)) {
         arr.push(this[i]);
      }
   }
   return arr;
}

let filteredNames = names.polyfillForFilter(item => {
   return item.age > 30
});

console.log(filteredNames);
// [{"name": "Sachin", "age": 40}, {"name": "Mohan", "age": 35}]
```

**Pollyfill for reduce**
```js
let logicAlbums = [
   "Bobby Tarantino",
   "The Incredible True Story",
   "Supermarket",
   "Under Pressure",
];

Array.prototype.pollyfillForReduce = function (callback, initialValue) {
   let accumulator = initialValue === undefined ? undefined : initialValue;

   for (let i = 0; i < this.length; i++) {
      if (accumulator !== undefined) {
         accumulator = callback.call(accumulator, this[i], i, this);
      } else {
         accumulator = this[i];
      }
   }
   return accumulator;
};

let combineAlbums = logicAlbums.pollyfillForReduce(function (a, b) {
   return a + " , " + b;
}, "Young Sinatra"); 

console.log(combineAlbums);
```

**[⬆](#Questions)**
---
#### QA10
### ✍Pollyfill for call, apply, bind.
```js
const test = {
	a: 123,
   b: 456,
   // _this: function tester (a, b) {
   //    return `a: ${this.a} and b: ${this.b} | arguments - a: ${a} and ${b}`;
   // }
}

function tester (a, b) {
	return `a: ${this.a} and b: ${this.b} | arguments - a: ${a} and ${b}`;
}

// original - bind(), call(), apply()
const bindExecutor = tester.bind(test, 80, 90);
console.log(bindExecutor()); // "a: 123 and b: 456 | arguments - a: 80 and 90"

console.log(tester.call(test, 80, 90)); // "a: 123 and b: 456 | arguments - a: 80 and 90"

console.log(tester.apply(test, [80, 90])); // "a: 123 and b: 456 | arguments - a: 80 and 90"

// pollyfill - bind(), call(), apply()
Function.prototype.myBind = function (scope, ...args) {
	scope._this = this; // put 'this' inside object's scope.
  return function () {
  	return scope._this(...args);
  }
}

const bindExecutor1 = tester.myBind(test, 80, 90);
console.log(bindExecutor1()); // "a: 123 and b: 456 | arguments - a: 80 and 90"

Function.prototype.myCall = function (scope, ...args) {
	scope._this = this;
  return scope._this(...args);
}
console.log(tester.myCall(test, 80, 90)); // "a: 123 and b: 456 | arguments - a: 80 and 90"

Function.prototype.myApply = function (scope, args) {
	scope._this = this;
  return scope._this(...args);
}
console.log(tester.myApply(test, [80, 90])); // "a: 123 and b: 456 | arguments - a: 80 and 90"
```

**[⬆](#Questions)**
---
#### QA11
### ✍Polyfill for flat method
   - Infinite depth flatten and flatten by a certain number
   - Implement both recursive and iterative approaches

**[⬆](#Questions)**
---
#### QA12
### ✍Polyfill for promises and Promise.all
- Polyfill for Promise()
```js
class PromiseSimple {
  constructor(executionFunction) {
    this.promiseChain = [];
    this.handleError = () => {};

    this.onResolve = this.onResolve.bind(this);
    this.onReject = this.onReject.bind(this);

    executionFunction(this.onResolve, this.onReject);
  }

  then(handleSuccess) {
    this.promiseChain.push(handleSuccess);

    return this;
  }

  catch(handleError) {
    this.handleError = handleError;

    return this;
  }

  onResolve(value) {
    let storedValue = value;

    try {
      this.promiseChain.forEach((nextFunction) => {
         storedValue = nextFunction(storedValue);
      });
    } catch (error) {
      this.promiseChain = [];

      this.onReject(error);
    }
  }

  onReject(error) {
    this.handleError(error);
  }
}

// Execution: API related stuff
fakeApiBackend = () => {
  const user = {
    username: 'treyhuffine',
    favoriteNumber: 42,
    profile: 'https://gitconnected.com/treyhuffine'
  };

  // Introduce a randomizer to simulate the probability of encountering an error
  if (Math.random() > .05) {
    return { 
      data: user, 
      statusCode: 200,
    };
  } else {
    const error = {
      statusCode: 404,
      message: 'Could not find user',
      error: 'Not Found',
    };

    return error;
  }
};

// Promise call
const makeApiCall = () => {
  return new PromiseSimple((resolve, reject) => {
    // Use a timeout to simulate the network delay waiting for the response.
    // This is THE reason you use a promise. It waits for the API to respond
    // and after received, it executes code in the `then()` blocks in order.
    // If it executed is immediately, there would be no data.
    setTimeout(() => {
      const apiResponse = fakeApiBackend();

      if (apiResponse.statusCode >= 400) {
        reject(apiResponse);
      } else {
        resolve(apiResponse.data);
      }
    }, 5000);
  });
};

// Promise execution
makeApiCall()
  .then((user) => {
    console.log('In the first .then()');
    return user;
  })
  .then((user) => {
    console.log(`User ${user.username}'s favorite number is ${user.favoriteNumber}`);
    return user;
  })
  .then((user) => {
    console.log('The previous .then() told you the favoriteNumber')
    return user.profile;
  })
  .then((profile) => {
    console.log(`The profile URL is ${profile}`);
  })
  .then(() => {
    console.log('This is the last then()');
  })
  .catch((error) => {
    console.log(error.message);
  });
```

- Polyfill for Promise.all()
```js
function task(time) {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      resolve(time);
    }, time);
  });
}
const taskList = [task(1000), task(5000), task(3000)];
// returns promise with results in an array
function myPromiseAll(taskList) {
  const results = []
  let promisesCompleted = 0;
  return new Promise((resolve, reject) => {
    taskList.forEach((promise, index) => {
      promise.then((val) => {
        results[index] = val;
        promisesCompleted += 1;
        if (promisesCompleted === taskList.length) {
          resolve(results)
        }
      })
        .catch(error => {
          reject(error)
        })
    })
  });
}
myPromiseAll(taskList)
  .then(results => {
    console.log("got results", results)
  })
  .catch(console.error)
```
NOTE: Promise.all will fail if even one of the promises fail. The order of the results array is maintained and is equal to the task list.

**[⬆](#Questions)**
---
#### QA13
### ✍Event bubbling, event capturing/trickling, and event delegation.
- **Event bubbling** goes from the target element straight up.
- In other words,`event.stopPropagation()` stops the move upwards, but on the current element all other handlers will run.
- To stop the bubbling and prevent handlers on the current element from running, there’s a method`event.stopImmediatePropagation()`. After it no other handlers execute.
```js
<div onclick="alert('The handler!')">
  <em>If you click on <code>EM</code>, the handler on <code>DIV</code> runs.</em>
</div>

<body onclick="alert(`the bubbling doesn\'t reach here`)">
  <button onclick="event.stopPropagation()">Click me</button>
</body>
```
- **Event capturing** is a type of event propagation where the event is first captured by the outermost element and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the inner DOM element.

**[⬆](#Questions)**
---
#### QA14
### ✍Explain map(), forEach(), filter() and reduce() higher order functions.
- map(): `map()` takes a callback and run it against every element on the array but whats makes it unique is it generate a new array based on your existing array.
```js
var arr = [10, 20, 30];

var mapped = arr.map(function(elem) {
   return elem * 10;
});
console.log(mapped); // [100, 200, 300]
```

- forEach(): It takes a callback function and run that callback function on each element of array one by one.
```js
var arr = [10, 20, 30];

arr.forEach(function (elem, index){
   console.log(elem + ' comes at ' + index);
});
// 10 comes at 0
// 20 comes at 1
// 30 comes at 2
```

- filter(): The main difference between `forEach()` and `filter()` is that forEach just loop over the array and executes the callback but filter executes the callback and check its return value. If the value is true element remains in the resulting array but if the return value is false the element will be removed for the resulting array. `filter()` will return a new filtered array every time.
```js
var arr = [10, 20, 30]; 

var result = arr.filter(function(elem){
    return elem !== 20;
})
console.log(result); // [10, 30]
```

- reduce(): `reduce()` method of the array object is used to reduce the array to one single value.
```js
var arr = [10, 20, 30];

var sum = arr.reduce(function(sum, elem) {
    return sum + elem;
});
console.log(sum); // Output: 60
```

**[⬆](#Questions)**
---
#### QA15
### ✍Difference between stop propagation and prevent default method.
- `stopPropagation` prevents further propagation of the current event in the capturing and bubbling phases.
- `preventDefault` prevents the default action the browser makes on that event.


**[⬆](#Questions)**
---
#### QA16
### ✍JavaScript Design Patterns.
A design pattern is a reusable solution that can be applied to commonly occurring problems in software design.

- **The Constructor Pattern**: A constructor is a special method used to initialize a newly created object. Since almost everything is an object in JavaScript, object constructors are used to create specific types of objects.

- **The Module Pattern**: Modules help in keeping the units of code for a project cleanly separately and organized. It is used to organize objects, functions, classes or variables so that they can be easily exported or imported into other files.

- **The Singleton Pattern**: The singleton pattern restricts the instantiation of a class to one object. The singleton instance can be exposed through module export.

- **The Observer Pattern**: The observer pattern allows one object to be notified when another object changes, without requiring the object to have knowledge of its dependents. The methods notify() and update() can be used to implement the observer pattern in JS.

- **The Prototype Pattern**: The prototype pattern allows to create objects based on a template of an existing object through cloning. The constructors in JS use the prototype pattern under the hood.

**[⬆](#Questions)**
---
#### QB1
### ✍Explain with examples of a deep and shallow copy.
**Shallow copy** is a bit-wise copy of an object. A new object is created that has an exact copy of the values in the original object. If any of the fields of the object are references to other objects, just the reference addresses are copied i.e., only the memory address is copied.

```js
let obj = {
  a: 1,
  b: 2,
};
let objCopy = Object.assign({}, obj);
console.log(objCopy); // Result - { a: 1, b: 2 }
objCopy.a = 5;
console.log(objCopy); // Result - { a: 5, b: 2 }
console.log(obj); // Result - { a: 5, b: 2 }
```

A **deep copy** copies all fields, and makes copies of dynamically allocated memory pointed to by the fields. A deep copy occurs when an object is copied along with the objects to which it refers.

```js
let obj = { 
  a: 1,
  b: { 
    c: 2,
  },
}
let newObj = JSON.parse(JSON.stringify(obj));
obj.b.c = 20;
console.log(obj); // { a: 1, b: { c: 20 } }
console.log(newObj); // { a: 1, b: { c: 2 } } (New Object Intact!)
```

**[⬆](#Questions)**
---
#### QB2
### ✍Remove falsy values from Array.
There are only six falsey values in JavaScript, `undefined` , `null` , `NaN` , `0` , "" (empty string), and `false`.

You can apply the filter method on the array by passing Boolean as a parameter. This way it removes all falsy values(0, undefined, null, false and "") from the array.

```js
const myArray = [false, null, 1,5, undefined]
myArray.filter(Boolean); // [1, 5] // is same as myArray.filter(x => x);
```

**[⬆](#Questions)**
---
#### QB3
### ✍splice vs slice method.
Some of the major difference in a tabular form

| Slice                   | Splice           | 
| ------------------------  |:------------------------:|
| Doesn't modify the original array(immutable) | Modifies the original array(mutable) |
| Returns the subset of original array | Returns the deleted elements as array |
| Used to pick the elements from array | Used to insert or delete elements to/from array |

**[⬆](#Questions)**
---
#### QB4
### ✍What is array destructuring.
```js
const arr = ['a', 'b', 'c'];

for (let [index, elem] of arr.entries()) {
  console.log(index, ': ', elem);
}
```

**[⬆](#Questions)**
---
#### QB5
### ✍Different ways of creating an object.
```js
// Initialize object literal with curly brackets
const objectLiteral = {};

// Initialize object constructor with new Object
const objectConstructor = new Object();

// Object.create
var employee = {
  name: 'Alex',
  displayName: function () {
    console.log(this.name);
  }
};

var emp1 = Object.create(employee);
console.log(emp1.displayName());  // output "Alex"
```

**[⬆](#Questions)**
---
#### QB6
### ✍Object creation patterns.

**[⬆](#Questions)**
---
#### QB7
### ✍Deep copy of an object.
```js
let obj = { 
  a: 1,
  b: { 
    c: 2,
  },
}
let newObj = JSON.parse(JSON.stringify(obj));
obj.b.c = 20;
console.log(obj); // { a: 1, b: { c: 20 } }
console.log(newObj); // { a: 1, b: { c: 2 } } (New Object Intact!)
```

**[⬆](#Questions)**
---
#### QB8
### ✍Add/remove properties from Objects.


**[⬆](#Questions)**
---
#### QB9
### ✍Looping through Array and Objects.
`for...in`:
- The `for...in` statement iterates a specified variable over all the enumerable properties of an object. 

`for...of`
The `for...of` statement creates a loop Iterating over iterable objects (including Array, Map, Set, arguments object and so on).

Difference between for...in and for...of statement
```javascript
const arr = [3, 5, 7];
arr.foo = 'hello';

for (let i in arr) {
   console.log(i); // logs "0", "1", "2", "foo"
}

for (let i of arr) {
   console.log(i); // logs 3, 5, 7
}
```

**[⬆](#Questions)**
---
#### QC1
### ✍What are the advantages of using Axios over Fetch API.

**[⬆](#Questions)**
---
#### QC2
### ✍Explain the CORS mechanism.
CORS stands for Cross Origin Resource Sharing, and it’s a protocol that allows servers to receive requests from different domains.

Developers often make external API requests to fetch data form external servers. Sometimes these servers could be from different domains too.

Example:
👉 My app in rootlearn[.]com making a GET request to rootlearn[.]com is a same origin request
👉 My app in rootlearn[.]com making a GET request to google[.]com is a cross origin request

But these cross domain requests are restricted by the browser ❌

Once developers have configured CORS on the server to accepts requests from other domains the browser will kick in a preflight check ✅

It is to verify whether resource sharing is allowed on the destination server. The preflight request uses the HTTP method OPTIONS.

![CORS mechanism](assets/cors-infographic.png)

**[⬆](#Questions)**
---
#### QC3
### ✍Explain JWT in detail.
JSON Web Token (JWT) is a token-based standard that allows us to securely transfer information between two parties without storing anything in a database.

JWT token consists of three parts:
- ✔️ Header
- ✔️ Payload
- ✔️ Signature
Each one being BaseURL64 encoded to form the token.

JWT authentication follows a 4 step process:
- Client (Browser) sends post request with credentials to auth server to authenticate themselves
- Auth Server authenticates user credential and generates a JWT. Server does not store anything and sends the token to the browser to save. It allows users to authenticate without their credentials in the future. It's best advised to store the token in an http only cookie.
- Thereafter for every request the client sends the JWT in the authorization header. Validation happens using token introspection with the auth server.
- Once validated, resource server sends the necessary data to the client.

![JWT](assets/jwt-infographic.png)

**[⬆](#Questions)**
---
#### QC4
### ✍Use AJAX and XMLHttpRequest to get reponse from an URL.

**[⬆](#Questions)**
---
#### QD1
### ✍Critical rendering path (must watch)

**[⬆](#Questions)**
---
#### QD2
### ✍Caching
   - HTTP requests: Headers like Cache-Control, ETag, and Transfer-Encoding

**[⬆](#Questions)**
---
#### QD3
### ✍Network waterfall

**[⬆](#Questions)**
---
#### QD4
### ✍Async, defer script attributes
- Async scripts are executed as soon as the script is loaded, so it doesn't guarantee the order of execution (a script you included at the end may execute before the first script file )
```js
<script async src="https://examples.com/long.js"></script>
```
- Defer scripts guarantees the order of execution in which they appear in the page.
```js
<script defer src="https://examples.com/long.js"></script>
```
![Async and Defer](assets/async-defer.png)

**[⬆](#Questions)**
---
#### QD5
### ✍preconnect, preload, prefetch

**[⬆](#Questions)**
---
#### QD6
### ✍Image optimization (jpeg v/s png v/s svg)

**[⬆](#Questions)**
---
#### QD7
### ✍Bundle size optimisation ( good to have webpack basics)

**[⬆](#Questions)**
---
#### QE1
### ✍XSS ( understand why we need cookies )

**[⬆](#Questions)**
---
#### QE2
### ✍CSRF
Cross-Site Request Forgery (CSRF) is an attack that forces users to submit a request to a web application when they are authenticated. It happens through a link that tricks user to send a forged request.

Ways to prevent:
- The application has to validate the token before processing it.
- Logging off the application after sometime.
- Not allowing browsers to remember credentials.

**[⬆](#Questions)**
---
#### QE3
### ✍Content security policy

**[⬆](#Questions)**
---




