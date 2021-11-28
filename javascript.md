# Questions
- [How does JavaScript works. Explain event loop.](#Q1)
- JS engine archietecture.
- Explain execution context.
- What is hoisting? Explain with example.
- Scope chain.
- var, let, const, Temporal Dead Zone.
- What is type of null, undefined, function, NaN.
- null and undefined.
- typeOf().
- Difference between == and ===.
- How does this keyword work? Provide some examples.
- Difference between call, apply and bind. Give example.fcons
- What is closure and what are the advantages of using closure.
- Function declaration and Function Expression.
- Higher Order Functions.
- Function overiding and overloading.
- OOPs concept in JS
   - Objects
   - classes
   - Encapsulation (constructor functions)
   - Inheritance (prototypal inheritance) with example
- Implement debouncing.
- Implement throttling.
- IIFE (Immediately Invoked Function Expression)
- Function currying with example.
- Difference between setTimeout vs setInterval.
- Implement setInterval using setTimeout
- What is type coercion?
- Falsy values in js.
- What is a strict mode in js?
- What is eval()?
- What are reference error and syntax error?
- JavaScript data types.
- Insert content in HTML using JavaScript. 
- HTML DOM (Document Object Model)
- BOM (Browser Object Model)
- window, screen, and document in Javascript
- alert, confirm and popup
- cookies, sessions and localstorage
- Array methods
- String methods
- Different errors in JS.

- Explain features of ES6.
- Difference between the arrow and normal function.
- Explain what the callback function is and provide a simple example.
- Promises
- Async-await
- Spread operator, rest and destructing.
- Iterators.
- Import and export.
- Pollyfill for map, reduce, filter and forEach. 
- Pollyfill for call, apply,bind.
- Polyfill for flat method
   - Infinite depth flatten and flatten by a certain number
   - Implement both recursive and iterative approaches
- Polyfill for promises and Promise.all
- Event bubbling, event capturing/trickling, and event delegation.
- Difference between stop propagation and prevent default method.

- How to empty an array.
- Remove duplicate values from an array.
- Explain with examples of a deep and shallow copy.
- Remove falsy values from Array.
- Shuffle elements in an array.
- splice vs slice method.
- What is array destructuring.
- Different ways of creating an object.
- Object creation patterns.
- Deep copy of an object.
- Check if a given object is empty or not.
- Add/remove properties from Objects.
- Given a string, reverse each word in the sentence.
- Given two strings, return true if they are anagrams of one another.
- Find a maximum consecutive repeating char in a given string.

- What are the advantages of using Axios over Fetch API.
- Explain the CORS mechanism.
- Explain JWT in detail.
- Use AJAX and XMLHttpRequest to get reponse from an URL. 

## Web Performance
- Critical rendering path (must watch)
- Caching
   - HTTP requests: Headers like Cache-Control, ETag, and Transfer-Encoding
- Network waterfall
- Bundle size optimisation ( good to have webpack basics)
- Async, defer script attributes
- preconnect, preload, prefetch
- Image optimization (jpeg v/s png v/s svg)

## Web security
- XSS ( understand why we need cookies )
- CSRF
- Content security policy

## Old Questions
* [JavaScript can display data in following ways](#javascript-can-display-data-in-following-ways)
* [JavaScript Data Types](#javascript-data-types)
* [JavaScript Objects](#some-of-the-javascript-objects-are)
* [null and undefined](#null-and-undefined)
* [typeof](#typeof)
* [Creating an object](#creating-an-object)
* [isNAN()](#isnan)
* [void(0)](#void0)
* [Tainted property in javascript](#tainted-property-in-javascript)
* [getElementbyName()](#getelementbyname)
* [HTML DOM](#html-dom)
* [Browser Object Model (BOM)](#browser-object-model-bom)
* [window, screen, and document in Javascript](#what-is-the-difference-between-window-screen-and-document-in-javascript)
* [Popup Alert](#popup-alert)
* [Timing Events](#timing-events)
* [Why “use strict” is used?](#why-use-strict-is-used)
* [Cookies and sessions](#what-is-difference-between-cookies-and-sessions)
* [JavaScript Methods](#javascript-methods)

# Answers
## Q1
### JavaScript can display data in following ways.

1. Writing into a HTML element, using <code>innerHTML</code>.
2. Writing into the HTML output, using <code>document.write()</code>. (NOTE: It deletes all the existing HTML)
3. Writing into an alert box, using <code>window.alert()</code>.
4. Writing into browser console, using <code>console.log()</code>.

**[⬆](####Questions)**
---
## JavaScript ignores multiple spaces.

JavaScript uses the Unicode character set. Unicode covers (almost) all the characters, punctuations, and symbols in the world.
 
## JavaScript Data Types
 
* Number
* String
* Boolean
* Undefined
* Null
 
## Some of the JavaScript Objects are
 
* Array
* Functions
* Objects
* Dates

## null and undefined

```javascript
var a;
console.log(a); //display undefined
var b = null;
console.log(b); //display null
```

## typeof

```javascript
console.log(typeof undefined); //undefined
console.log(typeof null);  //object
console.log(typeof "John"); //string
console.log(typeof 3.14); //number
console.log(typeof x); //undefined
console.log(typeof true); //boolean
console.log(typeof {'Name': 'Amrit', 'age': 23}); //object
console.log(typeof [1, 2, 3]); //object
console.log(typeof function demo() {}); //function
```

## Creating an object

```javascript
var car = {
   type: 'Fiat',
   color: 'red',
   model: '500'
}
console.log(car.type); //Fiat
console.log(car["color"]); //red
```

## Special characters

Add a backlash for showing special characters.
```javascript
var a = "My name is \"Amrit\" Anand."
console.log(a);
var b = "It's a name."
console.log(b);
```

## isNAN()

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

## void(0)

The void(0) evaluates the expression and returns undefined. Normally, we use in hrefs if we want to stop the default behaviour of href. It stays on the same page.
```javascript
<a href="javascript:void(0)">Read More</a>
```

## Tainted property in javascript

**window.defaultStatus** or **defaultStatus**

The FileUpLoad is a client-side as well as a server-side JavaScript object.

## getElementbyName()

It gets the element from the input field by name
```javascript
<input type="text" name="fname" value="1">
<input type="text" name="fname" value="2">

<script>
var x = document.getElementsByName("fname").length;
console.log(x); //2 as input fields are there with name=”fname”
</script>
```

## HTML DOM

HTML Document Object Model (DOM)is a standard Object model and programming interface for HTML. It defines all HTML elements as objects, the properties of HTML elements, the methods to access all HTML elements and the events for all HTML objects.
In general, the HTML DOM is a standard for how to get, change, add, or delete HTML elements.
Some examples of DOM

* document.getElementById()
```javascript
<input type="text" name="fname" value="1" id="text1"><br>
<input type="text" name="fname" value="2" id="text2">

document.getElementById('text1').value = 9999;
document.getElementById('text2').value = 1111;
```

* document.querySelector()
```javascript
document.querySelector('.demo').innerHTML = "Hello";
// you can use id also.
```

* document.getElementsByTagName()
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

* document.getElementsByClassName()
```javascript
<h4 id="demo" class="demo">Check the console for details.</h4>

var x = document.getElementsByClassName('demo');
x[0].innerHTML = 'hello';
```

* element.innerHTML =  new html content
```javascript
<h4 id="demo" class="demo">Check the console for details.</h4>
document.getElementById('demo').innerHTML = "inner html changed";
```

* element.attribute =  new value
```javascript
<a href="#" id="link">Link</a>

var a = document.getElementById('link').attributes.length;
console.log(a); //2
```

* element.setAttribute(attribute, value)
```javascript
document.getElementById('link').setAttribute('href', 'https://www.google.co.in/');
document.getElementById('text1').setAttribute('type', 'button');
```

* element.style.property = new style
```javascript
document.getElementById('link').style.color = "red";
document.getElementById('link').style.textTransform = "uppercase";
```

* document.createElement(element), document.removeChild(element),  document.appendChild(element),  document.replaceChild(element),  document.removeChild(element)
```javascript
var btn = document.createElement("button");
var t = document.createTextNode("Click Me");
var nw = document.createTextNode("New");
btn.appendChild(t);
btn.replaceChild(nw, t);
document.getElementById('link').appendChild(btn);
document.getElementById('link').removeChild(btn);
```

## Browser Object Model (BOM)

The Browser Object Model (BOM) allows JavaScript to "talk to" the browser.

### The Window Object

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

### The Window Screen

The window.screen object contains information about the user's screen.

* screen.width
* screen.height
* screen.availWidth
* screen.availHeight
* screen.colorDepth
* screen.pixelDepth


### The Window Location

The window.location object can be used to get the current page address (URL) and to redirect the browser to a new page.

1. window.location.href returns the href (URL) of the current page
2. window.location.hostname returns the domain name of the web host
3. window.location.pathname returns the path and filename of the current page
4. window.location.protocol returns the web protocol used (http: or https:)
5. window.location.assign loads a new document

```javascript
console.log(location); or
window.location

Location {replace: ƒ, assign: ƒ, href: "https://www.google.co.in/?gws_rd=ssl", ancestorOrigins: DOMStringList, origin: "https://www.google.co.in", ...}
ancestorOrigins:DOMStringList {length: 0}
assign:ƒ ()
hash:""
host:"www.google.co.in"
hostname:"www.google.co.in"
href:"https://www.google.co.in/?gws_rd=ssl"
origin:"https://www.google.co.in"
pathname:"/"
port:""
protocol:"https:"
reload:ƒ reload()
replace:ƒ ()
search:"?gws_rd=ssl"
toString:ƒ toString()
valueOf:ƒ valueOf()
Symbol(Symbol.toPrimitive):undefined
__proto__:Location
```

### The Window History

* history.back() -same as clicking back in the browser
* history.forward() -same as clicking forward in the browser

### The Window Navigator

The window.navigator object contains information about the visitor's browser. The window.navigator object can be written without the window prefix.

```javascript
console.log(navigator); or
window.navigator

Navigator {vendorSub: "", productSub: "20030107", vendor: "Google Inc.", maxTouchPoints: 0, hardwareConcurrency: 4, ...}
appCodeName:"Mozilla"
appName:"Netscape"
appVersion:"5.0 (Macintosh; Intel Mac OS X 10_12_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.167 Safari/537.36"
bluetooth:Bluetooth {}
budget:BudgetService {}
connection:NetworkInformation {downlink: 2.85, effectiveType: "4g", onchange: null, rtt: 100}
cookieEnabled:true
credentials:CredentialsContainer {}
deviceMemory:8
doNotTrack:null
geolocation:Geolocation {}
hardwareConcurrency:4
language:"en-GB"
languages:(3) ["en-US", "en", "la"]
maxTouchPoints:0
mediaDevices:MediaDevices {ondevicechange: null}
mimeTypes:MimeTypeArray {0: MimeType, 1: MimeType, 2: MimeType, 3: MimeType, 4: MimeType, application/pdf: MimeType, application/x-google-chrome-pdf: MimeType, application/x-nacl: MimeType, application/x-pnacl: MimeType, application/x-ppapi-widevine-cdm: MimeType, ...}
onLine:true
permissions:Permissions {}
platform:"MacIntel"
plugins:PluginArray {0: Plugin, 1: Plugin, 2: Plugin, 3: Plugin, Chrome PDF Plugin: Plugin, Chrome PDF Viewer: Plugin, Native Client: Plugin, Widevine Content Decryption Module: Plugin, length: 4}
presentation:Presentation {defaultRequest: null, receiver: null}
product:"Gecko"
productSub:"20030107"
serviceWorker:ServiceWorkerContainer {controller: null, ready: Promise, oncontrollerchange: null, onmessage: null}
storage:StorageManager {}
usb:USB {onconnect: null, ondisconnect: null}
userAgent:"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.167 Safari/537.36"
vendor:"Google Inc."
vendorSub:""
webkitPersistentStorage:DeprecatedStorageQuota {}
webkitTemporaryStorage:DeprecatedStorageQuota {}
__proto__:Navigator
```

## What is the difference between window, screen, and document in Javascript?

The <code>window</code> is the actual global object.
The <code>screen</code> is the screen, it contains properties about the user's display.
The <code>document</code> is where the DOM is.

![My image](https://i.stack.imgur.com/BkAjU.jpg)

## Popup Alert

1. Alert box

```javascript
alert('Hi There!');
```

2. Confirm box

```javascript
if (confirm("Press a button!")) {
   console.log('You pressed OK');
} else {
   console.log('You pressed cancelled.');
}
```

3. Prompt box

```javascript
var person = prompt("Please enter your name", "");

if (person == null || person == "") {
   console.log('You cancelled the prompt');
} else {
   console.log("Hello " + person + "! How are you today?");
}
```

NOTE: Line breaks

```javascript
alert("Hello\nHow are you?");
```

## Timing Events

1. setTimeout(function, milliseconds)
Executes a function, after waiting a specified number of milliseconds.
```javascript
function showTime() {
   setTimeout(function() {
       alert('Hello');
   }, 1000);
}
```
2. setInterval(function, milliseconds)
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
3. clearInterval()
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

## Why “use strict” is used?

Strict mode makes it easier to write "secure" JavaScript.
 
Strict mode changes previously accepted "bad syntax" into real errors.
 
As an example, in normal JavaScript, mistyping a variable name creates a new global variable. In strict mode, this will throw an error, making it impossible to accidentally create a global variable.
 
Using a variable, without declaring it, is not allowed.

## What is difference between cookies and sessions?

A cookie is a bit of data stored by the browser and sent to the server with every request.
A session is a collection of data stored on the server and associated with a given user (usually via a cookie containing an id code). Cookies are used to identify a session.

## JavaScript Methods

* concat()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var arr2 = ["india", "usa", "uk","china", "russia", "germany"];
var concat = arr1.concat(arr2);
console.log(concat);

RESULT:
["cricket", "football", "hockey", "baseball", "kabaddi", "india", "usa", "uk", "china", "russia", "germany"]
```
* fill()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var fill = arr1.fill("soccer");
console.log(fill);

RESULT:
["soccer", "soccer", "soccer", "soccer", "soccer"]
```
* indexOf()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var indexOf = arr1.indexOf("hockey");
console.log(indexOf);

RESULT:
2
```

* join()
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

* pop()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var pop = arr1.pop();
console.log(pop);
console.log(arr1);

RESULT:
Kabaddi
["cricket", "football", "hockey", "baseball"]
```

* push()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var push = arr1.push("golf");
console.log(push);
console.log(arr1);
RESULT:
6
["cricket", "football", "hockey", "baseball", "kabaddi", "golf"]
```

* reverse()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var reverse = arr1.reverse();
console.log(reverse);

RESULT:
["kabaddi", "baseball", "hockey", "football", "cricket"]
```

* slice()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var slice = arr1.slice(1, 3);
console.log(slice);

RESULT:
["football", "hockey"]
```

* sort()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var sort = arr1.sort();
console.log(sort);

RESULT:
["baseball", "cricket", "football", "hockey", "kabaddi"]
```

* splice()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var splice = arr1.splice(1, 2, "golf"); //splice(position, howmany, items,...)
console.log(splice);
console.log(arr1);

RESULT:
["football", "hockey"]
["cricket", "golf", "baseball", "kabaddi"]
```

* toString()
```javascript
var arr1 = ["cricket", "football", "hockey", "baseball", "kabaddi"];
var toString = arr1.toString();
console.log(toString);

RESULT:
cricket,football,hockey,baseball,kabaddi
```

* split()
```javascript
var arr1 = "How are doing today?";
var split = arr1.split(" ");
console.log(split);
console.log(arr1.split(" ").reverse().join());

RESULT:
["How", "are", "doing", "today?"]
today?,doing,are,How
```


