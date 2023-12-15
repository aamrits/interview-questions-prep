# Questions
## JavaScript
- [Explain event loop. How execution context? Explain JS engine archietecture. How JavaScript is so fast?](#QA1)
- [Explain Datatypes and type coercion in JS with examples. Difference between == and === ](#QA2)
- [Explain typeOf() and isNaN().](#QA3)
- [Functions. What is Function Hoisting and scope chain. Explain type of functions, IIFE, function currying. Explain closures.](#QA4)
- [Explain call, apply and bind with examples. Write a polyfill for all.](#QA5)
- [Explain OOPs concepts in JS, i.e., inheritence, encapsulation, classes, etc.](#QA6)
- [What is HTML DOM.](#QA7)
- [What is BOM.](#QA8)
- [Enlist Array methods.](#QA9)
- [Enlist String methods](#QA10)
- [Difference between setTimeout() and setInterval().](#QA11)
- [Explain Event bubbling, event capturing/trickling, and event delegation.](#QA12)
- [Difference between Cookies, sessions and localStorage.](#QA13)
- [Explain Alert, confirm and prompt.](#QA14)
- [Enlist Errors in JS.](#QA15)
- [Looping through Array and Object.](#QA16)
- [Different ways to create Object.](#QA17)
- [Explain Deep Copy and Shallow copy.](#QA18)
- [Explain Debouncing and Throttling with example.](#QA19)

## Some more(modern) JavaScript...
- [What is Promise. Why is it needed? Explain with example. Also enlighten async/await.](#QB1)
- [Enlist ES6 features. For e.g., Arrow Functions (difference from normal functions), spread and rest operator, var and let, destructing, import, dynamic import, etc.](#QB2)
- [Explain Higher Order Functions. Explain forEach(), map(), filter(), reduce() with examples. Write polyfill for each method.](#QB3)
- [Explain Generators and Iterators. In which scenarios these are used?](#QB4)

## JavaScript Misc
- [What are the advantages of using Axios over Fetch API.](#QC1)
- [Explain the CORS mechanism.](#QC2)
- [Explain JWT in detail.](#QC3)
- [Use AJAX and XMLHttpRequest to get reponse from an URL.](#QC4)

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
#### QA1 
### ✍Explain event loop. How execution context? Explain JS engine archietecture. How JavaScript is so fast?

![Event Loop](https://i.ibb.co/NFWj1Bc/event-loop1.png)

JavaScript is a **single threaded language**, i.e., it can execute one line at a time.
- The JavaScript Engine has a **memory heap** and **call stack** . Even before executing a single line of code, JS stores variables and functions in the heap. *Variables are assigned **undefined** and functions are stored as it*.

- After that **Global Execution Context** is created in the call stack. Each line is executed synchronously and after execution, gets popped out of the call stack.

- All the asynchronous events like `setTimeout` or **DOM APIs** or `XMLHttpRequest` are part of the **WebAPI**. When the timer expires or the response is fetched, it goes to the **callback queue**, where it waits for the call stack to be clear. Event loop checks this functionality.

- Once the call stack is empty, event loop pushes the callback functions, which are waiting in the callback queue, to the call stack, to be executed. 

- Suppose, there is a fetch request (**Promise**) and also a setTimeout. In this case, Promises gets pushed to the **microtask queue** or **priority queue**, after getting response. Microtask queue has more priority than callback queue (or task queue). So once the call stack is cleared, functions in the microtask queue gets pushed. After that callback functions in callback queue gets executed.

![Event Loop 2](https://i.ibb.co/J5RfsFf/event-loop2.png)

As per the code execution,
- Before even code is executed, there is Global Execution Context. In GEC, `window` and `this` is available to us. Here, `this` refers to `window` Object.

- Once code is executed, variable names are assigned value. For a function, a separate Execution Context is created. Here, `arguments` and `this` is available to us. For each function call, seperation Execution Contexts are created.

- Execution Context has 2 phases: **Creation** and **Execution**.
![Execution Context](https://i.ibb.co/hXZKHSr/execution-context.png)

**[⬆](#Questions)**
---
#### QA2
### ✍Explain Datatypes and type coercion in JS with examples. Difference between == and === 
The following are the primitive data types use in JS.
- Number
- String
- Boolean
- Undefined
- Null

`==` converts the variable values to the same type before performing comparison. This is called **type coercion**.

`===` does not do any type conversion (coercion) and returns true only if both values and types are identical.

**[⬆](#Questions)**
---
#### QA3 
### ✍Explain typeOf() and isNaN().
```js
// typeOf()
console.log(typeof undefined); // "undefined"
console.log(typeof null);  // "object"
console.log(typeof "John"); // "string"
console.log(typeof 3.14); // "number"
console.log(typeof x); // "undefined"
console.log(typeof true); // "boolean"
console.log(typeof {'Name': 'Amrit', 'age': 23}); // "object"
console.log(typeof [1, 2, 3]); // "object"
console.log(typeof function demo() {}); // "function"

// isNaN()
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
#### QA4 
### ✍Functions. What is Function Hoisting and scope chain. Explain type of functions, IIFE, function currying. Explain closures.
JavaScript Hoisting refers to the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.

`var` variables are initialized with undefined, `let` and `const` variables are not initialized.

Functions are hoisted as it is. Hence, we can run a function before we declare.

**[⬆](#Questions)**
---
#### QA5 
### ✍Explain call, apply and bind with examples. Write a polyfill for all.
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
#### QA6 
### ✍Explain OOPs concepts in JS, i.e., inheritence, encapsulation, classes, etc.

**[⬆](#Questions)**
---
#### QA7 
### ✍What is HTML DOM.
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
#### QA8
### ✍What is BOM
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
#### QA9 
### ✍Enlist Array methods.
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
#### QA10 
### ✍Enlist String methods.
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
#### QA11 
### ✍Difference between setTimeout() and setInterval().
`setTimeout(expression, timeout);` runs the code/function once after the timeout.

`setInterval(expression, timeout);` runs the code/function repeatedly, with the length of the timeout between each repeat.

```js
var intervalID = setInterval(alert, 1000); // Will alert every second.
// clearInterval(intervalID); // Will clear the timer.

setTimeout(alert, 1000); // Will alert once, after a second.
```

**[⬆](#Questions)**
---
#### QA12
### ✍Explain Event bubbling, event capturing/trickling, and event delegation.
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
#### QA13 
### ✍Difference between Cookies, sessions and localStorage.
| Cookies                   | Sessions           | Localstorage  |
| ------------------------  |:------------------------:| ------------------------:|
| The storage capacity of Cookies is 4KB | The storage capacity of session storage is 5MB |  The storage capacity of local storage is 5MB/10MB |
| Cookies expire based on the setting and working per tab and window | It’s session-based and works per window or tab. This means that data is stored only for the duration of a session, i.e., until the browser (or tab) is closed | As it is not session-based, it must be deleted via javascript or manually |
| Both clients and servers can read and write the cookies | The client can only read local storage | The client  can only read local storage |
| Data transfer to the server is exist | There is no transfer of data to the server | There is no transfer of data to the server |
| It is supported by all the browser including older browser | There are fewer old browsers that support it | There are fewer old browsers that support it |

**[⬆](#Questions)**
---
#### QA14 
### ✍Explain Alert, confirm and prompt.
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
#### QA15
### ✍Enlist Errors in JS.
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
#### QA16 
### ✍Looping through Array and Object.
`for...in`:
- The `for...in` statement iterates a specified variable over all the enumerable properties of an object. 

`for...of`:
- The `for...of` statement creates a loop Iterating over iterable objects (including Array, Map, Set, arguments object and so on).

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
#### QA17 
### ✍Different ways to create Object.
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
#### QA18
### ✍Explain Deep Copy and Shallow copy.
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
#### QA19 
### ✍Explain Debouncing and Throttling with example.
`Debounce`: In the debouncing technique, no matter how many times the user fires the event, the attached function will be executed only after the specified time once the user stops firing the event.

**Function for Debounce**
```js
function debounce(targetFunction, waitingTime = 1000) {
   let timer;
   return (...args) => {
      if (timer) clearTimeout(timer); // clear any previous timer
      timer = setTimeout(() => {
      targetFunction(...args);
      }, waitingTime);
   }
}

const debounceAndCallApi3 = debounce(api3, 3000);

document.getElementById("searchText").addEventListener("keyup", (e) => {
   const textValue = e.target.value;

   callApi1(textValue); // instantly calls Api 1
   waitAndCallApi2(textValue); // waits before Api call

   debounceAndCallApi3(textValue);
});
```

`Throttle`: Throttling is a technique in which, no matter how many times the user fires the event, the attached function will be executed only once in a given time interval.
~
**Function for Throttle**
```js
let  throttleFunction  =  function (func, delay) {
// If setTimeout is already scheduled, no need to do anything
if (timerId) {
   return;
}

// Schedule a setTimeout after delay seconds
timerId  =  setTimeout(function () {
   func();
   // Once setTimeout function execution is finished, timerId = undefined so that in <br>
   // the next scroll event function execution can be scheduled by the setTimeout
   timerId  =  undefined;
}, delay);
}
```

**[⬆](#Questions)**
---
#### QB1
### ✍What is Promise. Why is it needed? Explain with example. Also enlighten async/await.
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

The `.then()` method takes up to two arguments; the first argument is a callback function for the resolved case of the promise, and the second argument is a callback function for the rejected case. Each .then() returns a newly generated promise object.

A Promise is in one of these states:
- **pending**: initial state, neither fulfilled nor rejected.
- **fulfilled**: meaning that the operation was completed successfully.
- **rejected**: meaning that the operation failed.

Promise chain is one of the great things about using promises.

If we were to use 2 or more asynchronous operations, where subsequent operation starts when previous operation succeeds, we can simply use the `.then()` function, as it returns a new promise.

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
rejectionhandled: Sent when a promise is rejected, after that rejection has been handled by the executor's reject function.
unhandledrejection: Sent when a promise is rejected but there is no rejection handler available.

In both cases, the event has a promise property indicating the promise that was rejected, and a reason property that provides the reason given for the promise to be rejected.
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

// NOTE: However, even if one promise fail, Promise.all() will throw error and abort other calls. To avoid this, we can use Promise.allSettled(), which ensures all operations are complete (fulfilled or rejected) before resolving.
```

Promise callbacks are handled as a MicroTask and it has more priority than task queues.
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

Also unlike `Promise.race()`, which returns the first settled value (either fulfillment or rejection), this method returns the first fulfilled value. This method will ignore all rejected promises up until the first promise that fulfills.

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
#### QB2
### ✍Enlist ES6 features. For e.g., Arrow Functions (difference from normal functions), spread and rest operator, var and let, destructing, import, dynamic import, etc.


**[⬆](#Questions)**
---
#### QB3
### ✍Explain Higher Order Functions. Explain forEach(), map(), filter(), reduce() with examples. Write polyfill for each method.
- **forEach():** It takes a callback function and run that callback function on each element of array one by one.
```js
var arr = [10, 20, 30];

arr.forEach(function (elem, index){
   console.log(elem + ' comes at ' + index);
});
// 10 comes at 0
// 20 comes at 1
// 30 comes at 2
```

- **map():** `map()` takes a callback and run it against every element on the array but whats makes it unique is it generate a new array based on your existing array.
```js
var arr = [10, 20, 30];

var mapped = arr.map(function(elem) {
   return elem * 10;
});
console.log(mapped); // [100, 200, 300]
```

- **filter():** The main difference between `forEach()` and `filter()` is that forEach just loop over the array and executes the callback but filter executes the callback and check its return value. If the value is true element remains in the resulting array but if the return value is false the element will be removed for the resulting array. `filter()` will return a new filtered array every time.
```js
var arr = [10, 20, 30]; 

var result = arr.filter(function(elem){
    return elem !== 20;
})
console.log(result); // [10, 30]
```

- **reduce():** `reduce()` method of the array object is used to reduce the array to one single value.
```js
var arr = [10, 20, 30];

var sum = arr.reduce(function(sum, elem) {
    return sum + elem;
});
console.log(sum); // Output: 60
```

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
#### QB4
### ✍Explain Generators and Iterators. In which scenarios these are used?


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

![CORS mechanism](https://i.ibb.co/t2D7h7C/cors-infographic.jpg)

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

![JWT](https://i.ibb.co/rFBV7JG/jwt-infographic.jpg)

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
![Async and Defer](https://i.ibb.co/X8x3Scy/async-defer.png)

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

9.1 create one object which contains the property and method. Method should print the details of the property
Solution:
```js
var person = {
	name: 'Giri',
	age: 25,
	getIntroduction: function(){
		return `This is ${this.name} and person's age is ${this.age}`
	}
}
```
9.2 Bind another method which should print only the name in the object
Solution:
```js
var getName = function(){
	return this.name
}

var getNameHolder = getname.bind(person)
console.log(getNameHolder());
```
10 what is the compressor plugin you are using in the webpack to compress the code.
11 What is the difference between the onkeypress and onchange and which one will call first if it is register to same element.
12 difference between event.stopPropagation and event.preventDefault.

Lowe's

Interview 2
What is the advantage of react
why do you recommend react
Explain about Ajax calls - how it works
Explain how javascript is single threaded
How to handle asynchronous tasks
Fix the bug in React component (coding task)
About redux flow
About middleware used in project
Redux principles



Interview 3
Challenges you faced in your previous project
Object class in js
literal class in js
micro front-end framework
Deploying react application
react router
singleton object
Redux
What are the new APIs you've used in ES6
Explain 5 array helper methods
advantages of saga
http request on typing (each character typing makes http request, how to avoid & invoke request on word type)
react life cycle method componentDidUpdate alternate in functional component
How do you manage multiple http requests
example of uni directional data flow
what is immutability, give an example


Have you worked on configuring react project from scratch
How does React code is executed
Two forms, after form is succesfull -> navigate to another form (Router concept)
How do you approach this in React router
What is let & const used for
can you make array immutable
Redux architecure
Difference between hooks, lifecycle methods
When to use hooks
Is it mandatory to use Redux, why we need to use redux
What is mutable & immutable



Project Introduction
Rate yourself in React
Functional or class based components
virtual DOM
State Vs props
Program to pass props and change the parent component value in child component
Rate yourself in Javascript
What are the Array methods used?
Find out if object is empty or not?
Write a program to take an array as input and loop through the array elements and break from the loop when it finds a repeated number?
If we get an array of 100 objects from api, how to extract 50th object key value?
What is flex ?
Explain positions?
HTML5 what tags have u used explain? Why these tags have to be used instead of div tags?

Interview2:

Example program of closure? Several versions of modifying the program by creating the variable with the same name in the outer scope and asked for output?
Write a function that takes an array as an input arr=[1,2,3,0,8,7,0,0,6,0] to move the digits to left side of the array and zeros to right side of the array without using any sort and using only 1 array. The order of digits in the array should not be changed.
event loop and difference between callback queue and micro task queue? Which takes priority and why?
Write the output for the following?
console.log(1 < 2 < 3) 
console.log(3 > 2 >1) 
console.log(1+ +"2"+"3"); 
setTimeout(()=>{
console.log("hello")
},[0]
) 
const promiseA = new Promise( (resolutionFunc,rejectionFunc) => {
    resolutionFunc(777);
});
promiseA.then( (val) => console.log("asynchronous logging has val:",val) );

Why context api is used ? Why not redux? Use cases of redux exclusively ?
Pure Component
React.Memo vs usememo vs usecallback?
If we wrap the fucntion using usememo hook, if the state changes, the updated value will not be reflected. How to get the updated value?
What is Box model? If margin is added, will it change the height and weight of an element?




1 - Tell me about last project roles and responsibilities
2 - Have you worked on deployment, CI/CD
3 - What is your experience in fixing performance issues
4 - What is the limitations of React JS
5 - What is the difference between useContext and useMemo
6 - Explain REDUX and the react - redux flow
7 - Have you worked on Thunk or Saga





1.	Tell me about yourself?
2.	What is the difference between Redux and Context API? And which you will choose and why?
3.	What is virtual DOM and Explain how it is different from another JS library?
4.	Why JS is Single threaded?
5.	What is Event Loop?
6.	How are we doing Unit testing in react and Integration testing?
7.	How are we creating API using Node JS?
8.	Give a workflow for GET API?
9.	How we configure CI/CD Pipeline?
10.	How we store token in the application?
11.	What is useMemo, useEffect and how to avoid re-rendering to component?
12.	 What are the best practices to design React application?
13.	How can we create npm package so that we can use in multiple project?
14.	Why we use Functional Component over Class Component?
15.	If API (backend) is not ready and it will take a month to complete then what will be your approach in frontend side to progress with your task, whether you will wait for a month or what things you will start from UI side?
16.	How we can show or hide any component in react, tell me your approach?
17.	 How we design folder structure in React?
18.	How we call the API and bind in React and what is best approach?
19.	How we do code refactoring in React?

