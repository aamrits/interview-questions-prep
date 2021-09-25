## Questions
* [Object Creation Patterns](#object-creation-patterns)
* [Function overriding and overloading](#function-overriding-and-overloading)
* [Event capturing and Event bubbling](#event-capturing-and-event-bubbling)
* [Closures](#closures)
* [Callback Functions](#callback-functions)
* [Immediately Invoked Function Expressions (IIFE)](#immediately-invoked-function-expressions-iife)
* [JavaScript Higher Order Functions](#javascript-higher-order-functions-foreach-filter-map-sort-reduce)
* [Call, Apply and Bind()](#call-appy-and-bind)
* [Method Chaining](#method-chaining)
* [Currying Functions](#currying-functions)
* [Programs](#programs)
* [ES6 Features](#es6-features)
* [Const](#const)
* [var and let](#var-and-let)
* [Default parameters in ES6](#default-parameters-in-ES6)
* [Import and export](#import-and-export)
* [Arrow Functions](#arrow-functions)
* [Spread Operators](#spread-operators)
* [Iterators](#iterators)
* [Promises](#promises)


## Object Creation Patterns

1. Factory Function <br> 
In factory function, we create an object first, attach properties and methods to it and the return the object.
```javascript
//Factory Function
var factoryFunction = function(name, age, state) {
   var person = {}

   person.name = name;
   person.age = age;
   person.state = state;

   person.fullName = function() {
       console.log('Name: '+ this.name + '\n' + 'Age: ' + this.age + '\n' + 'State: ' + this.state);
   }

   return person;
}

var person1 = factoryFunction('John', 28, 'Baker Street, London');
person1.fullName();
```

2. Constructor Pattern <br>
In constructor pattern, create an instance of the method by using “new” keyword. Then we call the method.
```javascript
//Constructor Pattern
var constructorFunction = function(name, age, state) {
     this.name = name;
     this.age = age;
     this.state = state;

     this.fullName = function() {
         console.log('Name: ' + this.name + '\n' + 'Age: ' + this.age + '\n' + 'State: ' + this.state);
     }
 }

 var person1 = new constructorFunction('John', 28, 'Baker Street, London');
 person1.fullName();
```

3. Prototype Pattern<br>
In constructor method, we have to create an instance of the function everytime we instantiate it. So, it becomes redundant.
So, instead of creating an instance (by keyword “new”), we can use a prototype object and attach our properties and methods to it. In this way, we don’t have to create an instance of the entire function everytime we call it. 
```javascript
//Prototype Pattern
var personProto = function() {

}
personProto.prototype.name = 'John';
personProto.prototype.age = 28;
personProto.prototype.state = 'Baker Street, London';

personProto.prototype.fullName = function() {
   console.log('Name: ' + this.name + '\n' + 'Age: ' + this.age + '\n' + 'State: ' + this.state);
}

var person1 = new personProto();
person1.fullName();
```

## Function overriding and overloading

**JavaScript does not support overloading.**

JavaScript supports overriding, so if you define two functions with the same name, the last one defined will override the previously defined version and every time a call will be made to the function, the last defined one will get executed.
```
function addNumbers(n1, n2, n3) {
   return n1 + n2 + n3;
}
function addNumbers(n1, n2) {
   return n1 + n2;
}
var sum = addNumbers(1, 2, 3, 4);
console.log(sum); //3 as the first two number will be added.
```

## Event capturing and Event bubbling

A bubbling event goes from the target element straight up. 
In other words, <code>event.stopPropagation()</code> stops the move upwards, but on the current element all other handlers will run.
To stop the bubbling and prevent handlers on the current element from running, there’s a method <code>event.stopImmediatePropagation()</code>. After it no other handlers execute.

## Closures

A closure is an inner function that has access to the outer (enclosing) function’s variables—scope chain. The closure has three scope chains: own scope (variables defined between its curly brackets), it has access to the outer function’s variables, and it has access to the global variables.

```javascript
var fullName = function(firstName) {
  var name = function(lastName) {
      console.log('My name is ' + firstName + ' ' + lastName);
  }
  return name;
}
var person1 = fullName('John');
person1('Doe');
```

## Callback Functions

A higher order function is a function that may receive a function as parameter or even return a function. 
A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

```
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
To know more about callback, click below
https://codingandlearning.in/callback-function-in-javascript

## Immediately Invoked Function Expressions (IIFE)

An Immediately-Invoked Function Expression, or IIFE for short executes immediately after it’s created. The primary reason to use an IIFE is to obtain data privacy. Because JavaScript's var scopes variables to their containing function, any variables declared within the IIFE cannot be accessed by the outside world.

```javascript
var budgetController = (function() {
    var x = 23;

    function add(a) {
        return x + a;
    }

    return {
        publicTest: function (b) {
            console.log(add(b)); 
        } // has access to x and add() as its a closure. even if IIFE is returned immediately, closure still has access to x and add(.
    }
})();

// this is a IIFE which helps in data privacy. x and add() are private and so can't be accessed from outside. We use return object in order to get the value when we access from outside.

// budgetController.x
// undefined

// budgetController.add(5)
// Uncaught TypeError: budgetController.add is not a function\

// budgetController.publicTest(5)
// 28
```

## JavaScript Higher Order Functions: forEach(), filter(), map(), sort(), reduce()

https://codingandlearning.in/javascript-higher-order-array-methods-foreach-filter-map-sort-reduce

## Call, Appy and Bind()

https://codingandlearning.in/call-apply-and-bind-in-javascript

## Method Chaining

```javascript
var operation = function() {
    var i = 0;

    var add = function(j) {
        i = i + j;
        return this;
    }
    var multiply = function(j) {
        i = i * j;
        return this;
    }
    var show = function() {
        console.log(i);
    }

    return {
        add: add,
        mul: multiply,
        show: show
    };
}

var result = new operation();
result.add(3).mul(5).show();
```

## Currying Functions

```javascript
//example 1
var animals = function(a) {
    return function(b) {
        console.log('I love ' + a + ' and ' + b);
    }
}

var tiger = animals('tiger');
tiger('elephant');

//example 2
let avg = function(...n) {
    var total = 0;
    for (let i = 0;i < n.length;i++) {
        total = total + n[i];
    }
    return total/n.length;
}

let resArr = function(callback, ...n) {
    return function(...m) {
        return callback.apply(this, n.concat(m));
    }
};

let result1 = resArr(avg, 1, 2, 3); //2
console.log(result1(4, 5, 6)); // (1+2+3+4+5+6)/6 = 3.5
```

## Programs

### Write a function to remove duplicates in an array, sort it in the descending order.

```
const arr = [5, 2, 7, 5, 8, 4, 7, 2];
let output = [];
for (i = 0; i < arr.length; i++) {
   if(output.indexOf(arr[i]) == -1) {
       output.push(arr[i]);
   }
}
console.log(output.sort((a, b) => { return b-a }));
```

### Factorial Program (Recursion)

```javascript
let factorial = function(n) {
    if(n <= 0) {
        return 1;
    } else {
        return n * factorial(n-1);
    }
}
var result = factorial(6);
console.log(result);
```

## ES6 Features

### const

<code>const</code> is more powerful than <code>var</code>. Once used, the variable can’t be reassigned. In other words, it’s an **immutable variable except when it used with objects**.
```
const a = 6;
a = 7;
console.log(a); //Uncaught TypeError: Assignment to constant variable.
```
But if we use an array or an object, we can modify it.
```
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

### var and let

1. <code>let</code> is block scoped. <code>var</code> is function scoped.

### Default parameters in ES6

In ES6, if we use the default parameter, it won’t return undefined, and it will use its value when we forget to assign a parameter!
```
const person = function (name, age = 22) {
   return `Name is ${name} and age is ${age}`
} 
console.log(person('amrit')); //Name is amrit and age is 22
```

### Import and export

<code>export</code> allows you to export a module to be used in another JavaScript component. We use <code>import</code> to import that module to use it in our component. **In Angular, we use these a lot.**

### Arrow Functions

The arrow function makes your code more readable, more structured, and look like modern code.

```javascript
//function expression
let getA = function(a) {
    return a * a;
}

//arrow function
let getB = (a) => { return a * a }; //  method 1

var a = 4; //   assign the variable
let getC = () => { return a * a }; //  method 2
let getD = _ => { return a * a }; //  method 3

let mult = (c, d) => { return c * d }; //   passing two parameters

//show the result in console
console.log(getA(9)); // 81
console.log(getB(6)); // 36
console.log(getC()); // 16
console.log(getD()); // 16
console.log(mult(5, 6)); // 30

//Another example
var x = function() {
this.val = 1;
setTimeout(function() {
    this.val++;
    console.log(this.val);
}, 1);
}

var xx = new x(); //returns NAN as inside setTimeout there is no "this". It doesn't recognize parent "this".

//solution 1
var x1 = function() {
var that = this; // declare a varibale "that" and assign it "this". (clumpsy)
this.val = 1;
setTimeout(function() {
    that.val++;
    console.log(that.val);
}, 1);
}

var xx1 = new x1(); // 2

//solution 2: using fat arrow as it has not its own "this". It will take its parent "this".
var x2 = function() {          
this.val = 1;
setTimeout(() => {
    this.val++;
    console.log(this.val);
}, 1);
}

var xx2 = new x2(); // 2
```

### Spread Operators

```javascript
//example 1
var a = [1, 2, 3];
var b = [4, 5, 6];

a.push(...b); //using spread operator
// Array.prototype.push.apply(a, b);
console.log(a);

//example 2
var dowhatever = ['talk', 'run', 'watch tv'];
var life = ['born', 'walk', 'eat', ...dowhatever, 'die'];
console.log(life);
```

### Iterators

```javascript
var i = [1, 3, 5];

var iterator = i[Symbol.iterator]();

console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
```

### Promises

Promises are a new feature of ES6. It’s a method to write asynchronous code. It can be used when, for example, we want to fetch data from an API, or when we have a function that takes time to be executed.

The Promise object represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.

```javascript
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
