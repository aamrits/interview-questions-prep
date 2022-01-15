## Questions
* [Object Creation Patterns](#object-creation-patterns)
* [Method Chaining](#method-chaining)
* [Programs](#programs)

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




