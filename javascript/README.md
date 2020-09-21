# JavaScript

- [Introduction](#introduction)
- [Basic Syntax](#basic-syntax)
  - [Comments](#comments)
  - [Code Implementation](#code-implementation)
  - [Variables](#variables)
  - [Operators](#operators)
  - [Control Structures](#control-structures)
  - [Functions](#functions)
  - [Classes](#classes)
  - [Types](#types)
- [Built-in Objects](#built-in-objects)
  - [Arrays](#arrays)
  - [Window Object](#window-object)
  - [Date Object](#date-object)
  - [Math Object](#math-object)
- [APIs](#apis)
  - [DOM](#dom)
  - [Ajax](#ajax)
  - [GeoLocation](#geolocation)
- [Import/Export](#import/export)
- Libraries
  - [jQuery](jquery.md)
  - [REACT](react.md)
- Framework
  - [React Native](react-native.md)
- Server-side JavaScript
  - [Node.js](node-js.md)

## Introduction

- JavaScript is originally a client-side programming language.
- JavaScript is a special TypeScript script.
- It uses an interpreter built into the browser.
- JavaScript helps make a web page dynamic by responding to user events.
- JavaScript is the language for front-end web development.
- Many browsers have a console for the JavaScript interpreter, in Chrome, its in the Developer Tools.
- Javascript has an extension as .js.
- Semi-colons are optional, but recommended.
- Javascript it case-sensitive.
- JavaScript conforms to the ECMAScript(ES) specification
- ES6 is introduced in 2015.
- ES7 is introduced in 2016.
- ES8 is introduced in 2017.
- ...

## Basic Syntax

### Comments

- Single line comment

```js
//This is the single line comment for JS
```

- Multiline comments

```js
/* This is
     multiline comment */
```

### Code Implementation

#### Console

- JavaScript can be entered in the browser's console

#### Script Tag

JavaScript code can be added inside the script tag.

```html
<script>
  console.log("abc");
</script>
```

- The script tag can be placed in the HTML's `<head>` and `<body>` tags. It can be mostly found in the `<head>` tag, or at the bottom of the `<body>` tag.
- `<script>` can have attribute type, <script type="text/javascript"></script>, not required.
- JavaScript code can be placed in a separate js file and link the file using script tag.

```html
<script src="js/example.js"></script>
```

- `<noscript>` tag. If Javascript is not supported by the browser, the content inside `<noscript>` will be read.

### Variables

#### Naming Convention

- starts with letter, underscore, and dollar sign only.
- cannot start with a number.
- cannot contain operators, and special characters.

### Operators

#### Assignment

- `=` is used for variable assignment.
- assignment operators like `+=`, `-=`, `*=` all works in JavaScript.

##### var

`var` keyword is used to declared a global variable, its value can be any data type.

```js
var x = 10;
```

##### let

`let` declares local variables that only available in the current block of code.
let keyword is recommended for variable declaration.

##### const

`const` variables have the same scope as variables declared using let. it declares constants.

##### Undeclared Variables

If no keyword is used when declaration. these variables are global by default.

```js
x = 10; //x is global.
```

##### Destructuring Assignment

An easier way to assign elements of objects and arrays into variables.

- For Arrays:
  ```js
  const [x, y, z] = [1, 2, 3]; //result: x=1, y=2, z=3
  const [x, , z] = [3, 4, 5]; //result: x=3, z=5
  ```
- For Objects:
  ```js
  let objectX = { x: 1, y: 2, z: 3 };
  const { x: a, y: b, z: c } = objectX;
  // result: a=1, b=2, c=3
  const { prop1, prop2, prop3 } = this.props;
  // the three properties of the props will be assigned to prop1, prop2, prop3 respectively.
  ```

#### Arithmetic Operators

- Operators like `+`, `-`, `*`, `/`, `%`, `++`, `--` all work in JavaScript.

#### Comparison Operators

- `==` //equal to
- `===` //identical (equal and of same type)
- `!=` //Not equal
- `!==` //Not identical
- `>`
- `>=`
- `<`
- `<=`

#### Logical Operators

- JavaScript uses `&&`, `||`, `!` as logical operators.
  - `!!` will convert the variable to its corresponding boolean value by return the opposite boolean first then negate it again.
- `bool && string`, if bool true return string, if bool false return false.

#### Conditional(ternary) Operator

```js
variable = condition ? value1 : value2;
```

#### Membership Operator

```js
i in arrayX; //returns true if i is a member of arrayX
i in arrayX === false; //is true if i is not a member of arrayX
pushpin instanceof Microsoft.Maps.Pushpin; //see if an object is of type a class
typeof x !== "undefined"; //see if a variable is of certain type.
```

### Control Structures

#### Conditional Structures

- if-else

```js
if (condition1) {
  // code for condition1
} else if (condition2) {
  // code for condition2
} else {
  // code for all other conditions
}
```

- switch

```js
switch (expression) {
  case n1:
    //statements
    break;
  case n2:
    //statements
    break;
  default:
  //statements
}
```

#### Loops

- for loop

```js
for (i = 0; i < x; i++) {
  //...
}
```

- init part can be declared before for loop

```js
init
for(;con;in)
```

- init part can declare two variable separated by ,

```js
for (i = 1, text = ""; ; ) {}
```

- increment expression can be written in the loop

```js
for (init; con; ) {
  //increment expression
}
```

- if the condition part is missing, it is an infinite loop

```js
for (;;) {} //This is an infinite loop
```

- for...in loop

```js
let obj = { a: 1, b: 2, c: 3 };
for (let v in obj) {
  console.log(v);
}
//or
for (let i in array) {
  array[i].x = 100;
}
```

- it is intended for iterating over the enumerable keys of an object.

- for...of loop

```js
let list = ["x", "y", "z"];
for (let val of list) {
  console.log(val);
}
```

- it creates a loop iterating over iterable objects.

- while loop

```js
while (condition) {
  //...
}
```

- do...while loop

```js
do {
  //...
} while (condition);
```

- break/continue statements
- `break;` or `continue;` statement can be placed at anywhere in the loop.
- `break;` is used to break out the loop.
- `continue;` is used to skip the current iteration.

### Functions

- In JavaScript all functions are object methods.
- If a function is not a method of a JavaScript object, it is a function of the global object

#### Naming Convention

- same as the variables.

#### Define Functions

```js
 function functionName(param1, param2 , …) {
   //...
 }
```

```js
function sum(a, b) {
  var c = a + b;
  return c;
}
document.write(sum(2, 3));
```

- If a function has no return statement, the function will return undefined.

#### Functions with Default Values

```js
function test(a, b = 3, c = 42) {
  return a + b + c;
}
```

- Values are stated on the right side of the parameter list.
- Javascript is not strict about the number of parameter during function call. The missing arguments will be set as undefined, when extra argument was put, it will be ignored.

#### Anonymous Function(function literals)

```js
 let x.onclick = function () {
   document.body.innerHTML = Date();
 }
```

- It can be assigned as a value, to a variable.
- It can also be passed as an argument for a function that take a function as it's parameters.

#### Arrow Functions

```js
const add = (x, y) => {
  let sum = x + y;
  console.log(sum);
  return sum;
  //the value of add will be the sum.
};
//If no parameters uses
const x = () => alert("Hi");
```

#### Nested Functions

```js
function outerFunction(a, b, c = 0) {
  function innerFunction(a, b) {
    console.log("inner function called!");
    return a * b;
  }

  console.log("outer function called!");
  return innerFunction(b, c) + innerFunction(a, c);
}
```

#### Promise

- A Promise is a special object that represents an asynchronous operation that will eventually produce a value.
- Promise takes two function as arguments. They can be resolved and rejected.
- In a promise, the argument of the resolve function will be returned when the promise is resolved. The argument of the reject function will be returned when the promise is rejected.

##### Create a Promise as a variable

```js
let myPromise = new Promise((resolve, reject) => {
  if (condition) {
    resolve(data);
  } else {
    reject();
  }
});
//Pass data to the promise, get result from resolve in then, get result from reject in catch.
//The .then will only be called if the resolve function is called. .catch is for reject().
myPromise
  .then((data) => {
    console.log("Resolved: " + data);
  })
  .catch(() => {
    console.log("Rejected");
  });
```

##### Chained then Functions

`.then()` can be chained the latter then function has access to the data returned by previous then function.

```js
myPromise
  .then((data) => {
    console.log("Received: " + data);
    let moreData = "Another payload";
    return moreData;
  })
  .then((data) => {
    console.log(data);
  })
  .catch(() => {
    console.log("There was an error");
  });
```

##### Create a Promise as a Function

Promise can be created in a function and return as the result of the function, then it can be called use the function name.

```js
function promiseFunction() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(data);
    }, 500);
  });
}
```

- A function returns a promise can be assigned to a variable, the variable will have a value when the promise is resolved or rejected.

```js
const data = await promiseFunction();
```

#### Async Functions

- It runs asynchronously and controls the order of execution of the functions it contains. It use return keyword to return a promise.
- async function uses try catch block to handle errors.

##### Forms of Async Functions

- async function:
  async function functionName() {
  const msg = await scaryClown();
  console.log('Message:', msg);
  }

- async function expressions:
  const functionName = async function() {

}

- async arrow function:
  const functionName = async () => {

}

##### await Keyword

- It allow the functions(any statements or data assignment) inside the async function run in order.
  - Orders will be establist among code lines with `await`
  - Functions inside an async function with await keywords are mostly returning a promise.

```js
async function functionName() {
  const a = await promiseFunctionOne();
  const b = await promiseFunctionTwo();
  const c = await promiseFunctionThree();

  console.log(`${a} ${b} ${c}`);
}

//call the  functionName() async function to run the code inside the function.
functionName();
```

##### Promise.all

- Promise.all takes an array of functions and returns an array with the resolved values once all the passed-in promises have resolved.
- All functions start at the same time.

```js
async function functionName() {
  const [a, b, c] = await Promise.all([
    promiseFunctionOne(),
    promiseFunctionTwo(),
    promiseFunctionThree(),
  ]);

  console.log(`${a} ${b} ${c}`);
}
functionName();
```

### Classes

```js
class Person {
  constructor(name, id, balance = 0) {
    this.name = name;
    this.id = id;
    this.balance = balance;
  }
  addItem(price) {
    this.balance += price;
  }
}

let x = new Person("Jim", 1, 100);
```

- extends and static keywords are also supported.

### Types

- Supported types include Boolean, Number, String, Object, Null, and Undefined etc.

#### Number

- All numbers are stored as double precision flotation point numbers.
- NaN is a number type which stands for not-a-number.
- function `isNaN(x)`, returns true if x is `NaN`.
- `typeof x == 'number'` return true if x is a number.
- Use `x.toString()` to convert integer to string.

#### Boolean

- Boolean has true and false.
- For type conversion: 0, null, undefined, empty string return false, everything else is true.

#### String

- Strings can be enclosed by either single quotes and double quotes. when use single quotes, double quotes can be used without the escape character \\. when use double quotes, single quotes can be used inside.
- Uses `+` sign for concatenation.
- `parseInt("10")`, converts a string into int.
- `parseFloat("2.3")` converts a string into float.
- If conversion between a string and a number failed, returns NaN.
- `s.repeat(3);` returns a repeated string `s`, for three times.
- `s.length` return the length of s.
- `s.split(c)`; turn string into an array, split by character `c`.
- `s1.includes(s2)` return bool value states if s1 includes s2.
- `s1.equals(s2)` return true if two strings are equal
- Template literals are a way to output variables in the string. `'Value: ${variable}'`.
- click to see the docs for string.
- `s.toLowerCase()`
- `s.toUpperCase()`

#### Objects

- JavaScript objects are containers for named values.
- Values of object properties can contain primitive data types, function and other objects.
- When accessing a variable or method that does not exist in an object, undefined will be the result.

##### Creating New Object:

- Create an empty object:

```js
let objectName = {};
```

- Create an object with multiple variables:

```js
var person = {
  name: "John Dow",
  age: 31,
  favColor: "green",
  height: 186,
};
```

- Create an object with methods:

```js
let person = {
  name: "Sam Scott",
  id: 1021,
  balance: 123.99,
  addItem: function (price) {
    this.balance = this.balance + price;
  },
};
```

- Add Object's properties after object declaration:

```js
let circle = {};
circle.radius = 5.3;
circle.getArea = function () {
  return this.radius * this.radius * Math.PI;
};
```

- Property shorthand

```js
let height = 5;
let health = 100;
let athlete = {
  height,
  health,
};
```

- Shorthand object definitions syntax

```js
let time = {
  day: 10,
  month: "Feb",
  nextWeek() {
    this.day += 7;
  },
};
time.nextWeek();
console.log(time.day); // Output: 17
```

##### Accessing Object Properties

Objects are like associative arrays, instance variable and method can all be accessed by the named index. They can also be accessed using the dot format.

```js
node.style["color"] = "blue";
node.style.color = "blue";
```

##### Object Constructor Function.

It is a good idea to capitalize the first letter of the constructor name to distinguish it from others.

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.changeName = function (variableName) {
    this.variableName = variableName;
  };
}

var p = new Person("David", 21);
p.changeName("John");
//Now p.name equals to "John"
```

```js
//Define the function outside the constructor function and associate it with the object.
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.yearOfBirth = bornYear;
}
function bornYear() {
  return 2016 - this.age;
}
//it's not necessary to write the function's parentheses when assigning it to an object.
```

- The this keyword refers to the current object that take control of the current scope(the object in front of the curly brackets).
- Instance variables and methods defined by this keyword will be public, if private is desired, use let keyword.

## Built-in Objects

### Arrays

- JavaScript arrays are dynamic,
- Attempting to access an index outside of the array, returns the value undefined.

#### Creating Arrays

- Array Constructor

```js
var courses = new Array("HTML", "CSS", "JS");
var courses = new Array(3); // New array with three elements
```

- Array literal(Recommended)

```js
var courses = ["HTML", "CSS", "JS"];
var courses = []; // empty array using literal.
```

#### Accessing Array

```js
var courses = new Array();
courses[0] = "HTML";
courses[1] = "CSS";
courses[2] = "JS";
courses[3] = "C++";
```

#### Array Methods

```js
array.length; //return the length
array.concat(a1, a2); //return the concatenated a1 and a2
array.push("newElement"); //add new element to the end of array and return counts.
array.includes("elementX"); //return true if array contains elementX, false if not.
array.forEach(function(i) {
  //forEach iterates each element of the array as an argument of the function.
  //function code
});
array.filter(i => i.id !== 1); //filter an array item that has id not equal to 1.
[1, 2, 3].map(x => 2 * x); //return an array of element base on an array of data.
[1, 2, 3].map((item, index, array) => 2 * x); //it can takes optional parameters, index(second), and the array itself(third)
array.splice(2, 3); // delete 3 items starting at index 2.(have to call it independently and get the result after.)
array.reverse() //reverse all elements
array1.find(element => element > 10); //return the first element found, returns undefined if no match is found
array.reduce(function(total, currentValue, currentIndex, arr), initialValue)
//reduce iterate over each element of the function and return a value that will be used by the next iteration.
let arrAvg = arr => arr.reduce((a,b) => a + b, 0) / arr.length //get avg
Math.max(...array);//find the max value among array elements
array.unshift(a,b,c);//adds one or more items or elements to the beginning of the array and returns the new length of the array.
array.slice(1, 3);//The slice() method selects the elements starting at the given start argument, and ends at, but does not include, the given end argument.
//The only way to modify array element it to use for loop and access with index
for (var i in array) {
  array[i].x = 100;
}
```

#### Associative Array

Technically, associative array is an object. Array methods cannot be used on associative array.

```js
var person = []; //empty array
person["name"] = "John";
person["age"] = 46;
console.log(person["age"]);
//Outputs "46"
```

#### Spread operator

- It turns an array into a list of its element.

```js
...array = (array[0], array[1], array[2], ...)
```

- It can be used to insert elements of an array into another array's elements.

```js
array1 = [4, 5];
array2 = [1, 2, 3, ...array1, 6, 7];
//same as array2 = [1,2,3,4,5,6,7];
```

- `...rest`, can be used to represent the rest elements of an array.

### Window Object

All function and variables with global scope of Javascript that run on browser, belongs to the Window object.

#### Methods

```js
console.log(string);  //It is used for testing, it output text string in the console.
console.log(string, variable); // auto concatenate its argument.
Window.localStorage object.
// Simulate a mouse click:
window.location.href = "http://www.example.com";
// Simulate an HTTP redirect:
window.location.replace("http://www.example.com");
//open a new tab
window.open("https://www.example.com");

window.screen.width //Screen Width is the width of the device

document.write("\<h1\>abc<\\h1>");  //It is used for testing, it output text string in the HTML.
alert("alert message goes here");//return an alert box
eval("a string of expression"); 	//it returns the result of expression as a string, returns undefined if argument is empty.
prompt("promptText", "placeholder string");	//show a pop-up window for user input. it returns the value user entered if the OK button is clicked, or cancel return null.
confirm("confirmation message"); //it returns true if OK button is clicked, false if user cancels it.
setInterval(functionName, intervalNms);//setInterval function calls a function repeatedly in a certain time interval
clearInterval(intervalFunctionName); //stops the setInterval function right away
setTimeout(functionName, milliseconds);//Executes a function, after waiting a specified number of milliseconds.
```

#### Local Storage

- `window.localStorage` - stores data with no expiration date
- `window.sessionStorage` - stores data for one session (data is lost when the browser tab is closed)
- `localStorage.setItem("lastname", "Smith");` or `localStorage.lastname` - store local storage data
- `localStorage.getItem("lastname");` or `localStorage.lastname` - get local storage data
- `localStorage.removeItem("lastname");` - remove local storage data
- `localStorage.clear()` - clear all local storage
- `sessionStorage.setItem("lastname", "Smith");` or `sessionStorage.lastname` - store session storage data
- `sessionStorage.getItem("lastname");` or `sessionStorage.lastname` - get session storage data
- `sessionStorage.removeItem("lastname");` - remove session storage data
- `localStorage.clear()` - clear all session storage

### Date Object

#### Create New Date Object

```js
var d = new Date(); //d stores the current date and time
new Date(milliseconds);
new Date(dateString);
new Date(year, month, day, hours, minutes, seconds, milliseconds);
```

#### Methods

```js
Date.now(); // static method returns the number of milliseconds elapsed since January 1
date.getFullYear(); //gets the year
date.getMonth();
date.getDate();
date.getDay();
date.getHours();
date.getMinutes();
date.getSeconds();
date.getMilliseconds();
date.getTime(); //returns the number of milliseconds since January 1, 1970:
date.toDateString();
date.toTimeString();
```

- JavaScript counts months from 0 to 11.

### Math Object

#### Constants

```js
Math.PI;
Math.E;
Math.LN2; //natural log of 2
Math.LN10; //natural log of 10
Math.LOG2E; //The base 2 of e
Math.LOG10E; //The base 10 log of e
```

#### Methods

```js
Math.sqrt(4);
Math.abs
Math.acos
Math.asin
Math.ceil
Math.atan2(y,x)
Math.exp
Math.floor
Math.max(x,y,z,....)
Math.min(x,y,z,....)
Math.pow(x,y)
Math.round(x)      //rounds a number to the nearest integer.
Math.random() 		//random number between [0,1).
Math.floor((Math.random() * 10) + 1); //random integer from 0 - 10
Math.sin
Math.cos
Math.tan
```

- click here to see a complete list of its constants and methods.

## APIs

### DOM

- Document Object Model
- The browser builds the Document Object Model for HTML actively at runtime. document objects is organized in a hierarchical tree of elements(nodes).
- The root node is document, it can be used to select elements with the following methods.

#### Document Object

- `document` is the root object of the entire HTML file.
- has body as its property, `document.body`.
- work with following methods, to get a node object or nodelist.
  - finds element by id, `document.getElementById("id")`.
  - finds elements by class name, `document.getElementsByClassName("className");`.
  - finds elements by tag name, `document.getElementsByTagName("tagName");`.
  - select element using CSS selector rules, returns an array of elements.
    `document.querySelectorAll("cssSelector");`
- has an array of `forms` as its property
  - returns all forms in an array, `document.forms`.
  - return specific input element in a form, `document.forms.formID.inputName`.
  - returns the first input element of the first form in a document, `object.document.forms[0][0]`.

#### Node Object

- Any node object works with the following methods to find related node(s).
  - `node.childNodes` returns an array of an element's child nodes.
  - `node.firstChild` returns the first child node of an element.
  - `node.lastChild` returns the last child node of an element.
  - `node.hasChildNodes` returns true if an element has any child nodes, otherwise false.
  - `node.nextSibling` returns the next node at the same tree level.
  - `node.previousSibling` returns the previous node at the same tree level.
  - `node.parentNode` returns the parent node of an element.

#### NodeList Object

- If more than one node is found. Elements will be put in an nodeList
- NodeList is not an Array, it is possible to iterate over it with forEach().
  ```js
  nodeListName.forEach(function (nodeName) {
    //do something for each node inside nodeList
  });
  ```
- It can also be converted to a real Array using Array.from().
- nodeList can be accessed using index(starting at 0). `document.getElementsByTagName("p")[0];` If none is found, returns null.

#### Node Methods

After the node is found, following method can be used.

- `node.innerHTML`, access all string inside node's tag.
  - elements' content can be modified, `node.innerHTML = "Hello World!";`.
  - set innerHTML to "" can hide the tag.
- if the node is an input tag.
  - `inputNode.value;`, returns the value of the field, can be assigned with new value.
  - `inputNode.checked;`, return true if it is checked.
- change attribute
  - To access attributes of the style object, The dot format can be used, the associative array format can be used.
  - dashes (-) in the property names: these are replaced with camelCase versions. For example, `background-color` property should be referred to as `backgroundColor`.
  - `node.src = "apple.png";`
  - `node.href = "http://www.google.com";`
  - `node.style.color = "6600FF";`
  - `node.style.width = "100px";`
  - `node.style = "visibility:visible";`
  - `node.style["background-color"] = "lightBlue";`
  - `node.style.backgroundColor = "lightBlue";`
  - `node.className`, change its class name, it can be used to change a group of styles. with predefined CSS for a new classname.
  - `node.attributes.length`, find the number of attributes the node's tag has.
  - `node.attributes[0].name`, find the name of the tag's first attribute.
  - `node.id`, set tag id.
  - `checkboxNode.checked`, set get the bool value for checked status.

#### Create New Nodes

- Create nodes
  - `element.cloneNode()` clones an element and returns the resulting node.
  - `document.createElement("tagName")` creates a new element node.
  - `document.createTextNode("text")` creates texts that can be added to the element node.
- Add the new node into the document
  - `element.appendChild(newNode)` adds a new child node to an element as the last child node.
  - `element.insertBefore(node1, node2)` inserts node1 as a child before node2.
- remove a node
  - `parent.removeChild(node);`
  - `child.parentNode.removeChild(node);`
- replace elements
- `element.replaceChild(newNode, oldNode)`
- `element.replaceWith(newNode)`

#### Event handling

##### Event handlers

- Event handlers can be added as an attribute.
- Adding event handlers, `<p onclick="someFunc()">some text</p>`
- The form tag has an onsubmit attribute that can be assigned to validation checking function. If the function return false the form will not be submitted. In HTML for example: `<form onsubmit="returnvalidate()" method="get"></form>`
- Event handlers can be assigned to elements.
  ```js
  var x = document.getElementById("demo");
  x.onclick = function () {
    document.body.innerHTML = Date();
  };
  ```
- `window.onload` event can be used to run code after the whole page is loaded.
  ```js
  window.onload = function () {
    //some code
  };
  ```
- List of events
  - onclick
  - onload
  - onunload
  - onchange //any change for inside a form
  - onmouseover
  - onmouseout //mouse move out
  - onmousedown //click mouse
  - onmouseup //release mouse
  - onblur
  - onfocus

#### EventListener

- EventListener can be added for event handling, it is the recommended way.
- The `addEventListener()` method attaches multiple handlers to an element without overwriting existing event handlers
- `element.addEventListener(event, function, useCapture);`
  - The last parameter is optional:
  - There are two ways of event propagation in the HTML DOM: bubbling and capturing.
  - In bubbling, the innermost element's event is handled first and then the outer element's event is handled.
  - In capturing, the outermost element's event is handled first and then the inner.
  - In addEvent method the third parameter is optional it the useCapture default false mean using bubble
- `element.addEventListener("click", myFunction);`
- `use the document.attachEvent()` method in Internet Explorer before IE8.
- To remove an event listener use, `element.removeEventListener("mouseover", myFunction);`
- List of Events:
  - click
  - ouseover
  - mouseout
  - dbclick //double click
  - mousemove
  - mouseup
  - mousedown
  - mouse
  - submit
  - input //monitor any user input.
  - keyup
  - change //monitor input value change.
  - focus //monitor if an input element gain focus.
  - blur //monitor if an input element lose focus.
  - load
    - load event can be used for window.load function with act like the main method for the entire script. `window.addEventListener("load", function () {});`
- Event Object
  - event listeners always take an event object as its argument. It is always available inside the scope of the function that the event listener calls.
  - in `function(event){}`
    - `event.target` element that triggered event
    - `event.target.value` the trigger element's value
    - `event.which` mouse button number
    - `event.clientX` X location
    - `event.clientY` Y location
    - `event.preventDefault()` can be used to stop URL redirects after user click submit.
    - `event.pageX`, or pageY the mouse position (X & Y coordinates) at the time the event occurred, relative to the top left of the page.
    - `event.type` the type of the event (e.g. "click").
    - `event.which` the button or key that was pressed.
    - `event.data` any data that was passed in when the event was bound.
    - `event.stopPropagation()` Stop the event from bubbling up to other elements.

### Ajax

- It is used to send HTTP Requests and receive the HTTP Responses programmatically at runtime, without a page load.
- Ajax stands for Asynchronous JavaScript and XML, it is handled asynchronously, all other code runs normally, while Ajax is waiting or processing HTTP Responses.
- In Chrome, the Network tab of the Developer Tools shows the HTTP Request and Response details.
- XMLHttpRequest and fetch APIs are used to initiate HTTP Requests. Fetch is recommended.
  - [Click here](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) for detailed docs.
- An external library polypill can be added to provide fetch APIs supports.(unnecessary in the future)
- To send and process HTTP request, `fetch(URL, {credentials:'include'}).then(response=>response.text()).then(success);`

#### GET request

- URL could be an txt file url relative to current path.
- URL could be an URL with encoded parameter.
- `url="text.php?nameParam="+name;` usually this PHP echo simple text according the input.

#### POST request

```js
let param = "min=" + min + "&max=" + max;
fetch("target.php", {
  method: "POST",
  credentials: "include",
  headers: { Content_Type: "application/x-www-form-urlencoded" },
  body: param,
})
  .then((response) => response.text())
  .then(success);
```

- Content_Type specifies the format that used to pass the parameters.
- urlencoded style encodes parameter in url like GET url.
- Second parameter is an object contains request infomation. It can also be like:

```js
let options = {};
options.credentials = "include";
fetch(URL, options)
  .then((response) => response.text())
  .then(success);
```

- credentials:'include' means authorization headers and cookies are included in the request.
- success is the function that process the response.
- can chain more function in then after then. asynchronously.

```js
function success(text) {
  let span = document.getElementById("target");
  span.innerHTML = text;
}
```

#### Receive JSON data

- HTTP can only transmit strings. Data transfer formats are used to translate data structures like an array or an object into strings.
- Ajax uses two data transfer format: XML(eXtensible Markup Language) and JSON(JavaScript Object Notation). JSON is the most used one.
- In code change response.text() to response.json() to receive JSON data.
- JavaScript Object to JSON String, `JSON.stringify(data)`
- Decode from JSON, `JSON.parse(string)`
  - Using `eval()` can also convert json to javaScript objects, but It does not validate incoming data and it evaluate all string data

```js
//Eval converts the STRING into a JavaScript Array Map
var jsObj = eval("(" + JSONString + ")");
```

### GeoLocation

- The HTML Geolocation API is used to locate a user's position.
- Modern browsers support a global navigator object and the navigator object contains a navigator.geolocation property.
- To calculate the distance between two coordinates use `haversine()` function.
  - run `npm i haversine`.
  -

#### getCurrentPosition Method

```javascript
navigator.geolocation.getCurrentPosition(function (position) {
  //callback returns position object
  if (navigator.geolocation) {
    //check if there is a geolocation object
    latitude = position.coords.latitude;
    longitude = position.coords.longitude;
    accuracy = position.coords.accuracy;
  }
});
```

- The return object of callback function on success contains the following properties.
  - latitude - The latitude as a decimal number
  - longitude - The longitude as a decimal number
  - accuracy - The accuracy of position
  - altitude - The altitude in meters above the mean sea level
  - accuracy - The altitude accuracy of position
  - heading - The heading as degrees clockwise from North
  - speed - The speed in meters per second
  - timestamp - The date/time of the response
- It can have a second callback function to handle error.
- It can have an option object as its third argument for some setting.
  - timeout: how long are we willing to wait for an answer (in millisecs). Default is infinite
  - maximumAge: how old a cached location may be, in order to be acceptable as the ”current” location. Default is 0.
  - enableHighAccuracy: If more than one ”device” for obtaining a position is available, will we want the most accurate one. Default is false.
  - Example, `options = { maximumAge: 0, timeout:10 * 1000 , enableHighAccuracy: false}`

#### watchPosition Method

- `navigator.watchPosition(success, [error], [options]);`
- Returns the current position of the user and continues to return updated position as the user moves.
- Options:
  - `timeout (ms)` - Is a positive value representing the maximum length of time (in milliseconds) the device is allowed to take in order to return a position. Defaults to INFINITY.
  - `maximumAge (ms)` - Is a positive value indicating the maximum age in milliseconds of a possible cached position that is acceptable to return. If set to 0, it means that the device cannot use a cached position and must attempt to retrieve the real current position. If set to Infinity the device will always return a cached position regardless of its age. Defaults to INFINITY.
  - `enableHighAccuracy (bool)` - Is a boolean representing if to use GPS or not. If set to true, a GPS position will be requested. If set to false, a WIFI location will be requested.
  - `distanceFilter (m)` - The minimum distance from the previous location to exceed before returning a new location. Set to 0 to not filter locations. Defaults to 100m.
  - `useSignificantChanges (bool)` - Uses the battery-efficient native significant changes APIs to return locations. Locations will only be returned when the device detects a significant distance has been breached. Defaults to FALSE.

#### clearWatch Method

Stops the watchPosition() method

### Bing Maps

- Provide map to the webpage.
- [Click](https://www.microsoft.com/en-us/maps/documentation) to see full documents
- [Click](https://www.bing.com/api/maps/sdk/mapcontrol/isdk/Overview#HTML) to see sample codes.
- all of the map object has `getVisible()`, `getLocation()` methods.
- infobox properties can contain html tags in description property with close button. `<br>` or `description: "<a href='#' onclick='return directions(" + variableName + ");" + "'>directions</a>"`.

#### Set up

API key is required to use the map.

- Go to [Bing Maps Portal](https://www.bingmapsportal.com/)
- Sign in
- go to My Account -> My Keys to create an API key
- Place `<script type='text/javascript' src='https://www.bing.com/api/maps/mapcontrol?key=PLACEKEYHERE&callback=loadMapScenario' async defer></script>` before the closing body tag in HTML file.

## Import/Export

### Export

- In a separate javascript file for certain modules, any variable, function, class can be started with an export keyword so other js file can import it and use it.
- Anything without the export keyword will not be available for other js files.

```js
//export an array
export const myArray = [1, 2, 3, 4];
//export a function
const strings = ["AA", "BB", "CC"]; // Not available directly outside the module
export function myFunction() {
  console.log(strings);
}
//export a class
export class ClassName {
  constructor() {
    // ...
  }
}
```

- `export` keyword can be placed at the end and use curly brackets to enclosed everything needed to export.
- When exporting arrow function, declare the function variable proper using `const`.
- `as` keyword is used for alias.
  - `export { myArray, myFunction as NewName, ClassName };`
- `export` will export the access to imported modules for the export module since the object exported will trace back to the module file.

### Import

- `import` keyword, members to be imported in curly brackets and then the location of the module relative to the current file, `import { myFunction, ClassName } from 'file.js';`
- use `as` for alias without curly brackets. `import myFunction as newName from 'file.js';`
- You can import everything that's exported by a module like this: `import * as Utils from 'app.js';`
  - This allows you access to members with the dot notation: `Utils.myLogger();`
- append `default` keyword for default export. Default export will allow is to be imported by default.
  - import with a random name will assign and import default export item as this random name. Then followed by any other non-default items in the curly brackets.
  - If myArray is the default export, When import `import newDefaultArrayName, { ClassName, myFunction } from 'file.js';`
- Note: Imported function and variables is global, they can be accessed anywhere directly.
