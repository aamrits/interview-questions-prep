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
- [Difference between stop propagation and prevent default method.](#QA14)

## JavaScript Array, Objects, etc.
- [How to empty an array.](#QB1)
- [Remove duplicate values from an array.](#QB2)
- [Explain with examples of a deep and shallow copy.](#QB3)
- [Remove falsy values from Array.](#QB4)
- [Shuffle elements in an array.](#QB5)
- [splice vs slice method.](#QB6)
- [What is array destructuring.](#QB7)
- [Different ways of creating an object.](#QB8)
- [Object creation patterns.](#QB9)
- [Deep copy of an object.](#QB10)
- [Check if a given object is empty or not.](#QB11)
- [Add/remove properties from Objects.](#QB12)
- [Given a string, reverse each word in the sentence.](#QB13)
- [Given two strings, return true if they are anagrams of one another.](#QB14)
- [Find a maximum consecutive repeating char in a given string.](#QB15)

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

## Old Questions
* [JavaScript can display data in following ways](#javascript-can-display-data-in-following-ways)
* [JavaScript Data Types](#javascript-data-types)
* [JavaScript Objects](#some-of-the-javascript-objects-are)
* [Creating an object](#creating-an-object)
* [isNAN()](#isnan)
* [void(0)](#void0)
* [Tainted property in javascript](#tainted-property-in-javascript)

# Answers
### Q1
✍How does JavaScript works. JS engine archietecture. How JavaScript is so fast.
JavaScript is a dynamically typed language unlike C++.
```javascript
var x = 17;
```
- when we define "x", we don't worry about the type of the variable or the memory it will take. This makes prototyping fast.
- JS Engine use JIT (Just In Time) Compilation. It interpretes and compiles at the same time.
- Modern JS engines are 2 compilers, one is optimizing compiler. Its job is to re-compile "hot functions" with type information and optimize it in the process.
- If the type is changed, then it has to de-optimize (small performance hit).
- Google Chrome browser's V8 engine is the fastest. Here, the baseline compiler is Ignition. The optimising compiler is Turbofan. The machine code is called Bytecode.
![JS Engine 1](assets/js-engine1.png)
![JS Engine](assets/js-engine.png)

**[⬆](#Questions)**
---
### Q2
✍Explain event loop.
![Event Loop](assets/event-loop1.png)
JavaScript is a single threaded language, i.e., it can execute one line at a time.
1. The JavaScript Engine has a memory heap and call stack. Even before executing a single line of code, JS stores variables and functions in the heap. Variables are assigned "undefined" and functions are stored as it.
2. After that Global Execution Context is created in the call stack. Each line is executed synchronously and after execution, gets popped out of the call stack.
3. All the asynchronous events like setTimeout or DOM APIs or XMLHttpRequest are part of the WebAPI. When the timer expires or the reponse is fetched, it goes to the callback queue, where it waits for the call stack to be clear. Event loop checks this functionality.
5. Once the call stack is empty, event loop pushes the callback functions, which are waiting in the callback queue, to the call stack, to be executed. 
6. Suppose, there is a fetch request (Promise) and also a setTimeout. In this case, Promises gets pushed to the microtask queue, after getting response. Microtask queue has more priority than callback queue (or task queue). So once the call stack is cleared, functions in the microtask queue gets pushed. After that callback functions in callback queue gets executed.
![Event Loop 2](assets/event-loop2.png)

**[⬆](#Questions)**
---
### Q3
✍Explain execution context.
1. Before even code is executed, there is Global Execution Context. In GEC, 'window' and 'this' is available to us. Here, 'this' refers to 'window' Object.
2. Once code is executed, variable names are assigned value. For a function, a separate Execution Context is created. Here, 'arguments' and 'this' is available to us. For each function call, seperation Execution Contexts are created.
3. Execution Context has 2 phases: Creation and Execution.
![Execution Context](assets/execution-context.png)

**[⬆](#Questions)**
---
### Q4
✍What is hoisting? Explain with example.
- JavaScript Hoisting refers to the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.
- "var" variables are initialized with undefined, "let" and "const" variables are not initialized.
- Functions are hoisted as it is. Hence, we can run a function before we declare.

**[⬆](#Questions)**
---
### Q5
✍Scope chain.
It refers to the lexical environment. If a variable or a function is not declared in its scope, but it is declared in its lexical parent, then that variable can be accessed in the function also.
```javascript
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
### Q6
✍var, let, const,Temporal Dead Zone.
- "var" declarations are globally scoped or function scoped while "let" and "const" are block scoped.
- "var" variables can be updated and re-declared within its scope; "let" variables can be updated but not re-declared; "const" variables can neither be updated nor re-declared.
- They are all hoisted to the top of their scope. But while var variables are initialized with undefined, "let" and "const" variables are not initialized.
- While "var" and "let" can be declared without being initialized, "const" must be initialized during declaration.

**[⬆](#Questions)**
---
### Q7
✍What is type of null, undefined, function, NaN.
```javascript
console.log(typeof null);  // "object"
console.log(typeof undefined); // "undefined"
console.log(typeof function demo() {}); // "function"
console.log(typeof NaN); // "number"
```

**[⬆](#Questions)**
---
### Q8
✍null and undefined.
- the type of undefined is "undefined", whereas null is "object".
- When a variable is declared but no value is assigned, then it shows undefined. But we can assign to a variable. So "null" is an assignment value.

**[⬆](#Questions)**
---
### Q9
✍typeOf() 
```javascript
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
### Q10
✍Difference between == and === . 
- "==" converts the variable values to the same type before performing comparison. This is called "type coercion". 
- "===" does not do any type conversion (coercion) and returns true only if both values and types are identical.

**[⬆](#Questions)**
---
### Q11
✍How does this keyword work? Provide some examples.

**[⬆](#Questions)**
---
### Q12
✍Difference between call, apply and bind. Give example.

**[⬆](#Questions)**
---

### Q13
✍What is closure and what are the advantages of using closure.

**[⬆](#Questions)**
---
### Q14
✍Function statement, Function Expression, Anonymous Function, Named Function Expression, First Class Function, Higher-order Function.
- Function Statement or Function Declaration
```javascript
function a() {
   console.log('a is called');
}
a(); // a is called
```
- Function Expression. Here, it is treated as a variable, so it is not hoisted. On the other hand, Function Statement is hoisted.
```javascript
let b = function () {
   console.log('b is called');
}
b();  // b is called
```
- Anonymous Functions are used when functions are used as values, just like Function Expression as an example.

- Named Function Expression
```javascript
let c = function abc() {
   console.log('c is called', abc);
}
c(); 
// c is called, function abc() {
 console.log('c is called', abc);
}
```
We can't call this function like abc() as it is defined as a value .
- First Class Function (or First Class Citizens)
The ability to pass functions as values or pass functions inside a function as arguments is known as First Class Function. We can also return a function from function. 
- Higher-order Function
A “higher-order function” is a function that accepts functions as parameters and/or returns a function.

**[⬆](#Questions)**
---
### Q15
✍Difference between arguments and parameters.
```javascript
function sum(a,b) {
   return a+b;
}
console.log(sum(2, 3));
```
a, b are the parameters. 2, 3 are arguments.
The values which we pass insde a function are called as arguments and the labels or identiers which gets those values are known as parameters.

**[⬆](#Questions)**
---
### Q16
✍Function overiding and overloading.

**[⬆](#Questions)**
---

### Q17
✍OOPs concept in JS (Objects, Classes, Encapsulation(constructor), Inheritance(prototypal with example))

**[⬆](#Questions)**
---
### Q18
✍Implement debouncing.

**[⬆](#Questions)**
---
### Q19
✍Implement throttling.

**[⬆](#Questions)**
---
### Q20
✍IIFE (Immediately Invoked Function Expression)

**[⬆](#Questions)**
---

### Q21
✍Function currying with example.

**[⬆](#Questions)**
---
### Q22
✍Difference between setTimeout vs setInterval.
- setTimeout(function, milliseconds)
Executes a function, after waiting a specified number of milliseconds.
```javascript
function showTime() {
   setTimeout(function() {
       alert('Hello');
   }, 1000);
}
```
- setInterval(function, milliseconds)
Same as setTimeout(), but repeats the execution of the function continuously.
```javascript
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
- clearInterval()
The clearInterval() method stops the execution of the function specified in setInterval().
```javascript
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
### Q23
✍Implement setInterval using setTimeout

**[⬆](#Questions)**
---
### Q24
✍What is the difference between window, screen, and document in Javascript?
The <code>window</code> is the actual global object.
The <code>screen</code> is the screen, it contains properties about the user's display.
The <code>document</code> is where the DOM is.

![My image](https://i.stack.imgur.com/BkAjU.jpg)

**[⬆](#Questions)**
---
### Q25
✍Falsy values in js.

**[⬆](#Questions)**
---
### Q26
✍What is a strict mode in js
- Strict mode makes it easier to write "secure" JavaScript.
- Strict mode changes previously accepted "bad syntax" into real errors.
- As an example, in normal JavaScript, mistyping a variable name creates a new global variable. In "strict" mode, this will throw an error, making it impossible to accidentally create a global variable.
 
Using a variable, without declaring it, is not allowed.

**[⬆](#Questions)**
---
### Q27
✍What is eval()

**[⬆](#Questions)**
---
### Q28
✍What are reference error and syntax error?

**[⬆](#Questions)**✍
---

### Q29
✍JavaScript data types.
- Number
- String
- Boolean
- Undefined
- Null

**[⬆](#Questions)**
---
### Q30
✍Insert content in HTML using JavaScript.
There 

**[⬆](#Questions)**
---
### Q31
✍HTML DOM (Document Object Model)\
HTML Document Object Model (DOM)is a standard Object model and programming interface for HTML. It defines all HTML elements as objects, the properties of HTML elements, the methods to access all HTML elements and the events for all HTML objects.\
In general, the HTML DOM is a standard for how to get, change, add, or delete HTML elements.\
Some examples of DOM\

- document.getElementById()
```javascript
<input type="text" name="fname" value="1" id="text1"><br>
<input type="text" name="fname" value="2" id="text2">

document.getElementById('text1').value = 9999;
document.getElementById('text2').value = 1111;
```

- document.querySelector()
```javascript
document.querySelector('.demo').innerHTML = "Hello";
// you can use id also.
```

- document.getElementsByTagName()
The getElementsByTagName() method returns a collection of all elements in the document with the specified tag name.
```javascript
<h4 id="demo">Check the console for details.</h4>
<ul>
       <li>Ice cream</li>
       <li>Honey</li>
       <li>Vanilla</li>
</ul>
var x = document.getElementsByTagName("li");
document.getElementById("demo").innerHTML = x[1].innerHTML;
```

- document.getElementsByClassName()
```javascript
<h4 id="demo" class="demo">Check the console for details.</h4>

var x = document.getElementsByClassName('demo');
x[0].innerHTML = 'hello';
```

- element.innerHTML =  new html content
```javascript
<h4 id="demo" class="demo">Check the console for details.</h4>
document.getElementById('demo').innerHTML = "inner html changed";
```

- element.attribute =  new value
```javascript
<a href="#" id="link">Link</a>

var a = document.getElementById('link').attributes.length;
console.log(a); //2
```

- element.setAttribute(attribute, value)
```javascript
document.getElementById('link').setAttribute('href', 'https://www.google.co.in/');
document.getElementById('text1').setAttribute('type', 'button');
```

- element.style.property = new style
```javascript
document.getElementById('link').style.color = "red";
document.getElementById('link').style.textTransform = "uppercase";
```

- document.createElement(element), document.removeChild(element),  document.appendChild(element),  document.replaceChild(element),  document.removeChild(element)
```javascript
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
### Q32
✍BOM (Browser Object Model)
The Browser Object Model (BOM) allows JavaScript to "talk to" the browser.
- The Window Object
1. window.innerHeight -the inner height of the browser window (in pixels)
2. window.innerWidth -the inner width of the browser window (in pixels)
```javascript
console.log("Window innerWidth: " + innerWidth);
console.log("Window innerHeight: " + innerHeight);
```
3. window.open() -open a new window
```javascript
<button type="button" id="btn" onclick="a()">Click me</button>

function a() {
   var x = window.open("", "MsgWindow", "width=200,height=100");
   x.document.write("<p>This is 'MsgWindow'. I am 200px wide and 100px tall!</p>")
}
```
4. window.close() -closes the current window
5. window.moveTo() -move the current window
6. window.resizeTo() -resize the current window

- The Window Screen
The window.screen object contains information about the user's screen.
   - screen.width
   - screen.height
   - screen.availWidth
   - screen.availHeight
   - screen.colorDepth
   - screen.pixelDepth

- The Window Location
The window.location object can be used to get the current page address (URL) and to redirect the browser to a new page.
   - window.location.href returns the href (URL) of the current page
   - window.location.hostname returns the domain name of the web host
   - window.location.pathname returns the path and filename of the current page
   - window.location.protocol returns the web protocol used (http: or https:)
   - window.location.assign loads a new document

```javascript
console.log(location); or
window.location
```

- The Window History
   - history.back() -same as clicking back in the browser
   - history.forward() -same as clicking forward in the browser

- The Window Navigator
The window.navigator object contains information about the visitor's browser. The window.navigator object can be written without the window prefix.

```javascript
console.log(navigator); or
window.navigator
```

**[⬆](#Questions)**
---
### Q33
✍alert, confirm and popup
- Alert box: "window.alert()" instructs the browser to display a dialog with an optional message, and to wait until the user dismisses the dialog.
```javascript
alert('Hi There!');
```
- Confirm box: "window.confirm()" instructs the browser to display a dialog with an optional message, and to wait until the user either confirms or cancels the dialog.
```javascript
if (confirm("Press a button!")) {
   console.log('You pressed OK');
} else {
   console.log('You pressed cancelled.');
}
```
- Prompt box: "window.prompt()" instructs the browser to display a dialog with an optional message prompting the user to input some text, and to wait until the user either submits the text or cancels the dialog
```javascript
var person = prompt("Please enter your name", "");

if (person == null || person == "") {
   console.log('You cancelled the prompt');
} else {
   console.log("Hello " + person + "! How are you today?");
}
```

**[⬆](#Questions)**
---
### Q34
✍cookies, sessions and localstorage
| Cookies                   | Sessions           | Localstorage  |
| ------------------------  |:------------------------:| ------------------------:|
| The storage capacity of local storage is 5MB/10MB      | The storage capacity of session storage is 5MB | The storage capacity of Cookies is 4KB |
| As it is not session-based, it must be deleted via javascript or manually | It’s session-based and works per window or tab. This means that data is stored only for the duration of a session, i.e., until the browser (or tab) is closed | Cookies expire based on the setting and working per tab and window |
| The client  can only read local storage | The client can only read local storage | Both clients and servers can read and write the cookies |
| There is no transfer of data to the server | There is no transfer of data to the server | Data transfer to the server is exist |
| There are fewer old browsers that support it | There are fewer old browsers that support it | It is supported by all the browser including older browser |

**[⬆](#Questions)**
---
### Q35
✍Array methods
- concat()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var arr2 = ["india", "usa", "uk","china", "russia", "germany"];
var concat = arr1.concat(arr2);
console.log(concat);

RESULT:
["cricket", "football", "hockey", "baseball", "kabaddi", "india", "usa", "uk", "china", "russia", "germany"]
```
- fill()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var fill = arr1.fill("soccer");
console.log(fill);

RESULT:
["soccer", "soccer", "soccer", "soccer", "soccer"]
```
- indexOf()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var indexOf = arr1.indexOf("hockey");
console.log(indexOf);

RESULT:
2
```

- join()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var join = arr1.join();
console.log(join);

RESULT:
cricket,football,hockey,baseball,kabaddi
```

* map()
```javascript
var arr1 = [4, 9, 16, 25, 36];
var map = arr1.map(Math.sqrt);
console.log(map);

RESULT:
[2, 3, 4, 5, 6]
```

* shift()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var shift = arr1.shift();
console.log(shift);
console.log(arr1);
RESULT:
Cricket
["football", "hockey", "baseball", "kabaddi"]
```

* unshift()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var unshift = arr1.unshift("golf");
console.log(unshift);
console.log(arr1);

RESULT:
6
["golf", "cricket", "football", "hockey", "baseball", "kabaddi"]
```

- pop()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var pop = arr1.pop();
console.log(pop);
console.log(arr1);

RESULT:
Kabaddi
["cricket", "football", "hockey", "baseball"]
```

- push()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var push = arr1.push("golf");
console.log(push);
console.log(arr1);
RESULT:
6
["cricket", "football", "hockey", "baseball", "kabaddi", "golf"]
```

- reverse()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var reverse = arr1.reverse();
console.log(reverse);

RESULT:
["kabaddi", "baseball", "hockey", "football", "cricket"]
```

- slice()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var slice = arr1.slice(1, 3);
console.log(slice);

RESULT:
["football", "hockey"]
```

- sort()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var sort = arr1.sort();
console.log(sort);

RESULT:
["baseball", "cricket", "football", "hockey", "kabaddi"]
```

- splice()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var splice = arr1.splice(1, 2, "golf"); //splice(position, howmany, items,...)
console.log(splice);
console.log(arr1);

RESULT:
["football", "hockey"]
["cricket", "golf", "baseball", "kabaddi"]
```

- toString()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var toString = arr1.toString();
console.log(toString);

RESULT:
cricket,football,hockey,baseball,kabaddi
```

- split()
```javascript
var arr1 = "How are doing today?";
var split = arr1.split(" ");
console.log(split);
console.log(arr1.split(" ").reverse().join());

RESULT:
["How", "are", "doing", "today?"]
today?,doing,are,How
```

**[⬆](#Questions)**
---

### Q36
✍String methods

**[⬆](#Questions)**
---
### Q37
✍Different errors in JS.

**[⬆](#Questions)**
---
### Q38
✍isNaN()
```javascript
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
### QA1
✍Explain features of ES6.

**[⬆](#Questions)**
---
### QA2
✍Difference between the arrow and normal function.

**[⬆](#Questions)**
---
### QA3
✍Explain what the callback function is and provide a simple example.

**[⬆](#Questions)**
---
### QA4
✍Promises

**[⬆](#Questions)**
---
### QA5
✍Async-await

**[⬆](#Questions)**
---
### QA6
✍Spread operator, rest and destructing.

**[⬆](#Questions)**
---
### QA7
✍Iterators

**[⬆](#Questions)**
---
### QA8
✍Import and Export

**[⬆](#Questions)**
---
### QA9
✍Pollyfill for map, reduce, filter and forEach.
- Pollyfill for forEach
```javascript
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

- Pollyfill for map
```javascript
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

- Pollyfill for filter
```javascript
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

- Pollyfill for reduce
```javascript
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
         accumulator = callback.call(undefined, accumulator, this[i], i);
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
### QA10
✍Pollyfill for call, apply,bind.

**[⬆](#Questions)**
---
### QA11
✍Polyfill for flat method
   - Infinite depth flatten and flatten by a certain number
   - Implement both recursive and iterative approaches

**[⬆](#Questions)**
---
### QA12
✍Polyfill for promises and Promise.all

**[⬆](#Questions)**
---
### QA13
✍Event bubbling, event capturing/trickling, and event delegation.

**[⬆](#Questions)**
---
### QA14
✍Difference between stop propagation and prevent default method.

**[⬆](#Questions)**
---
### QB1
✍How to empty an array.

**[⬆](#Questions)**
---
### QB2
✍Remove duplicate values from an array.

**[⬆](#Questions)**
---
### QB3
✍Explain with examples of a deep and shallow copy.

**[⬆](#Questions)**
---
### QB4
✍Remove falsy values from Array.

**[⬆](#Questions)**
---
### QB5✍
✍Shuffle elements in an array.

**[⬆](#Questions)**
---
### QB6
✍splice vs slice method.

**[⬆](#Questions)**
---
### QB7
✍What is array destructuring.

**[⬆](#Questions)**
---
### QB8
✍Different ways of creating an object.

**[⬆](#Questions)**
---
### QB9
✍Object creation patterns.

**[⬆](#Questions)**
---
### QB10
✍Deep copy of an object.

**[⬆](#Questions)**
---
### QB11
✍Check if a given object is empty or not.

**[⬆](#Questions)**
---
### QB12
✍Add/remove properties from Objects.

**[⬆](#Questions)**
---
### QB13
✍Given a string, reverse each word in the sentence.

**[⬆](#Questions)**
---
### QB14
✍Given two strings, return true if they are anagrams of one another.

**[⬆](#Questions)**
---
### QB15
✍Find a maximum consecutive repeating char in a given string.

**[⬆](#Questions)**
---
### QC1
✍What are the advantages of using Axios over Fetch API.

**[⬆](#Questions)**
---
### QC2
✍Explain the CORS mechanism.

**[⬆](#Questions)**
---
### QC3
✍Explain JWT in detail.

**[⬆](#Questions)**
---
### QC4
✍Use AJAX and XMLHttpRequest to get reponse from an URL.

**[⬆](#Questions)**
---
### QD1
✍Critical rendering path (must watch)

**[⬆](#Questions)**
---
### QD2
✍Caching
   - HTTP requests: Headers like Cache-Control, ETag, and Transfer-Encoding

**[⬆](#Questions)**
---
### QD3
✍Network waterfall

**[⬆](#Questions)**
---
### QD4
✍Async, defer script attributes

**[⬆](#Questions)**
---
### QD5
✍preconnect, preload, prefetch

**[⬆](#Questions)**
---
### QD6
✍Image optimization (jpeg v/s png v/s svg)

**[⬆](#Questions)**
---
### QD7
✍Bundle size optimisation ( good to have webpack basics)

**[⬆](#Questions)**
---
### QE1
✍XSS ( understand why we need cookies )

**[⬆](#Questions)**
---
### QE2
✍CSRF

**[⬆](#Questions)**
---
### QE3
✍Content security policy

**[⬆](#Questions)**
---




