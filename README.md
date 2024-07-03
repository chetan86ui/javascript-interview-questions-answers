# javascript-interview-questions-answers

This JavaScript repository offers interview prep for both interviewers and candidates, with common questions, detailed answers, and code examples to benefit developers of all levels.

## Contents

- **Basic Questions:** Fundamental concepts and syntax.
- **Intermediate Questions:** In-depth questions on functions, objects, and more.
- **Advanced Questions:** Complex scenarios and advanced topics.
- **Coding Challenges:** Practical coding problems and solutions.
- **Best Practices:** Tips and guidelines for writing clean and efficient JavaScript code.

## Basic Questions

#### 1.What is JavaScript?

JavaScript is a high-level, dynamic, untyped, and interpreted programming language. It is one of the core technologies of the World Wide Web, alongside HTML and CSS. It enables interactive web pages and is an essential part of web applications. The majority of websites use it, and all major web browsers have a dedicated JavaScript engine to execute it.

#### How do you declare a variable in JavaScript?

You can declare a variable using the var, let, or const keywords.

var is function-scoped and can be redeclared and updated.
let is block-scoped and can be updated but not redeclared.
const is block-scoped and cannot be updated or redeclared.

```javascript
var x = 5;
let y = 10;
const z = 15;
```

#### What are data types in JavaScript?

Answer: JavaScript has the following data types:

Primitive Data Types: undefined, null, boolean, number, string, symbol, and bigint.
Non Primitive Data Types: Object, Array, Function, etc.

#### What are JavaScript functions?

Answer: Functions in JavaScript are blocks of code designed to perform a particular task. They are executed when they are invoked (called).

```javascript
function add(a, b) {
  return a + b;
}

let sum = add(5, 10); // sum is 15
```

#### What is the difference between == and ===?

Answer: == is the abstract equality operator which performs type coercion if the operands are of different types. === is the strict equality operator which does not perform type coercion, and returns false if the operands are of different types.

```javascript
5 == "5"; // true
5 === "5"; // false
```

#### How do you create an object in JavaScript?

Answer: An object can be created using object literals, the new Object() syntax, or constructor functions/classes.

```javascript
// Object literal
let person = {
  firstName: "John",
  lastName: "Doe",
};

// Using new Object()
let person = new Object();
person.firstName = "John";
person.lastName = "Doe";

// Constructor function
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}
let person = new Person("John", "Doe");

// Using class
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
}
let person = new Person("John", "Doe");
```

#### What are arrays in JavaScript and how do you create them?

Answer: Arrays are list-like objects used to store multiple values in a single variable. You can create arrays using array literals or the new Array() syntax.

```javascript
// Array literal
let fruits = ["Apple", "Banana", "Cherry"];

// Using new Array()
let fruits = new Array("Apple", "Banana", "Cherry");
```

#### What is the this keyword?

Answer: The this keyword refers to the object it belongs to. In a method, this refers to the owner object. Alone, this refers to the global object. In a function, this refers to the global object (in non-strict mode). In an event, this refers to the element that received the event.

#### What are closures in JavaScript?

Answer: A closure is a function that has access to its own scope, the scope of the outer function, and the global scope. This means that a function can "remember" the variables from the place where it was created, even after that function has finished executing.

```javascript
function outerFunction() {
  let outerVariable = "I'm from outer function";

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

const myInnerFunction = outerFunction();
myInnerFunction(); // logs: "I'm from outer function"
```

#### How do you handle asynchronous operations in JavaScript?

Answer: JavaScript handles asynchronous operations using callbacks, Promises, and async/await.

Callbacks: A function passed into another function as an argument to be executed later.

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback("Data fetched");
  }, 1000);
}
fetchData(console.log); // logs: "Data fetched" after 1 second
```

Promises: An object representing the eventual completion or failure of an asynchronous operation.

```javascript
let promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Data fetched"), 1000);
});
promise.then(console.log); // logs: "Data fetched" after 1 second
```

async/await: Syntactic sugar on top of Promises to make asynchronous code look synchronous.

```javascript
async function fetchData() {
  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Data fetched"), 1000);
  });
  let result = await promise;
  console.log(result); // logs: "Data fetched" after 1 second
}
fetchData();
```
### JavaScript Reduce
The reduce() method of Array instances executes a user-supplied "reducer" callback function on each element of the array, in order, passing in the return value from the calculation on the preceding element. The final result of running the reducer across all elements of the array is a single value.
```javascript
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  initialValue,
);

console.log(sumWithInitial);
// Expected output: 10
```

### What is a Higher Order Function? and How its working.
A higher order function is a function that takes one or more functions as arguments, or returns a function as its result.
There are several different types of higher order functions like map and reduce. We will discuss these later in this tutorial. But before that let's first dive deep into what higher order functions are.

```javascript
// Callback function, passed as a parameter in the higher order function
function callbackFunction(){
    console.log('I am  a callback function');
}

// higher order function
function higherOrderFunction(func){
    console.log('I am higher order function')
    func()
}

higherOrderFunction(callbackFunction);
```
In the above code higherOrderFunction() is an HOF because we are passing a callback function as a parameter to it.

The above example is quite simple isn't it? So let's expand it further and see how you can use HOFs to write more concise and modular code.
You can use higher order functions in a variety of ways.

When working with arrays, you can use the map(), reduce(), filter(), and sort() functions to manipulate and transform data in an array.

When working with objects, you can use the Object.entries() function to create a new array from an object.

When working with functions, you can use the compose() function to create complex functions from simpler ones.
### 3 Ways to Promise
There are 3 ways you could want promises to resolve, parallel (all together), sequential (1 after another), or a race (doesn't matter who wins).
```javascript
const promisify = (item, delay) =>
  new Promise(resolve => setTimeout(() => resolve(item), delay));

const a = () => promisify("a", 100);
const b = () => promisify("b", 5000);
const c = () => promisify("c", 3000);

async function parallel() {
  const promises = [a(), b(), c()];
  const [output1, output2, output3] = await Promise.all(promises);
  return `parallel is done: ${output1} ${output2} ${output3}`;
}

async function sequence() {
  const output1 = await a();
  const output2 = await b();
  const output3 = await c();
  return `sequence is done: ${output1} ${output2} ${output3}`;
}

async function race() {
  const promises = [a(), b(), c()];
  const output1 = await Promise.race(promises);
  return `race is done: ${output1}`;
}

sequence().then(console.log);
parallel().then(console.log);
race().then(console.log);

// race is done: a
// parallel is done: a b c
// sequence is done: a b c
```


