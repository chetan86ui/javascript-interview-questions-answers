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
