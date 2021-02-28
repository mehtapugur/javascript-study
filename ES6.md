ECMAScript, or ES, is a standardized version of JavaScript. Because all major browsers follow this specification, the terms ECMAScript and JavaScript are interchangeable.

with the var keyword is that you can overwrite variable declarations without an error.
var camper = 'James';
var camper = 'David';
console.log(camper);
// logs 'David'

If you were to replace var with let in the variable declarations of the code above, the result would be an error.
let camper = 'James';
let camper = 'David'; // throws an error
So unlike var, when using let, a variable with the same name can only be declared once.

Note the "use strict". This enables Strict Mode, which catches common coding mistakes and "unsafe" actions. For instance:
"use strict";
x = 3.14; // throws an error because x is not declared

- Compare Scopes of the var and let Keywords

    When you declare a variable with the var keyword, it is declared globally, or locally if declared inside a function.

    The let keyword behaves similarly, but with some extra features. When you declare a variable with the let keyword inside a block, statement, or expression, its scope is           limited to that block, statement, or expression.

    For example:
    
    var numArray = [];
    var numArray = [];
    for (var i = 0; i < 3; i++) {
      numArray.push(i);
    }
    console.log(numArray);
    // returns [0, 1, 2]
    console.log(i);
    // returns 3
    
    With the var keyword, i is declared globally. So when i++ is executed, it updates the global variable. This code is similar to the following:
With the var keyword, i is declared globally. So when i++ is executed, it updates the global variable. This code is similar to the following:

    var numArray = [];
    var i;
    for (i = 0; i < 3; i++) {
      numArray.push(i);
    }
    console.log(numArray);
    // returns [0, 1, 2]
    console.log(i);
    // returns 3
    This behavior will cause problems if you were to create a function and store it for later use inside a for loop that uses the i variable. This is because the stored function     will always refer to the value of the updated global i variable.
    
    
    var printNumTwo;
    for (var i = 0; i < 3; i++) {
      if (i === 2) {
        printNumTwo = function() {
          return i;
        };
      }
    }
    console.log(printNumTwo());
    // returns 3
    As you can see, printNumTwo() prints 3 and not 2. This is because the value assigned to i was updated and the printNumTwo() returns the global i and not the value i had when     the function was created in the for loop. The let keyword does not follow this behavior:
    
    let printNumTwo;
    for (let i = 0; i < 3; i++) {
      if (i === 2) {
        printNumTwo = function() {
          return i;
        };
      }
    }
    console.log(printNumTwo());
    // returns 2
    console.log(i);
    // returns "i is not defined"


- Declare a Read-Only Variable with the const Keyword

const has all the awesome features that let has, with the added bonus that variables declared using const are read-only. They are a constant value, which means that once a variable is assigned with const, it cannot be reassigned.

const FAV_PET = "Cats";
FAV_PET = "Dogs"; // returns error

You should always name variables you don't want to reassign using the const keyword.
A common practice when naming constants is to use all uppercase letters, with words separated by an underscore.

- Mutate an Array Declared with const

const s = [5, 6, 7];
s = [1, 2, 3]; // throws error, trying to assign a const
s[2] = 45; // works just as it would with an array declared with var or let
console.log(s); // returns [5, 6, 45]

As you can see, you can mutate the object [5, 6, 7] itself and the variable s will still point to the altered array [5, 6, 45]. Like all arrays, the array elements in s are mutable, but because const was used, you cannot use the variable identifier s to point to a different array using the assignment operator.

- Prevent Object Mutation

To ensure your data doesn't change, JavaScript provides a function Object.freeze to prevent data mutation.
Once the object is frozen, you can no longer add, update, or delete properties from it. Any attempt at changing the object will be rejected without an error.

let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad"; // will be ignored. Mutation not allowed
obj.newProp = "Test"; // will be ignored. Mutation not allowed
console.log(obj); 
// { name: "FreeCodeCamp", review:"Awesome"}

- Use Arrow Functions to Write Concise Anonymous Functions

const myFunc = function() {
  const myVar = "value";
  return myVar;
}

ES6 provides us with the syntactic sugar to not have to write anonymous functions this way. Instead, you can use arrow function syntax:

const myFunc = () => {
  const myVar = "value";
  return myVar;
}

When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword return as well as the brackets surrounding the code. This helps simplify smaller functions into one-line statements:
const myFunc = () => "value";

- Write Arrow Functions with Parameters

Just like a regular function, you can pass arguments into an arrow function.

// doubles input value and returns it
const doubler = (item) => item * 2;
doubler(4); // returns 8

If an arrow function has a single parameter, the parentheses enclosing the parameter may be omitted.

// the same function, without the parameter parentheses
`const doubler = item => item * 2;`

It is possible to pass more than one argument into an arrow function.

// multiplies the first input value by the second and returns it
`const multiplier = (item, multi) => item * multi;
multiplier(4, 2); // returns 8`

- Set Default Parameters for Your Functions

`const greeting = (name = "Anonymous") => "Hello " + name;`

console.log(greeting("John")); // Hello John
console.log(greeting()); // Hello Anonymous

The default parameter kicks in when the argument is not specified (it is undefined). 

- Use the Rest Parameter with Function Parameters

With the rest parameter, you can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from inside the function.

function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2)); // You have passed 3 arguments.
console.log(howMany("string", null, [1, 2, 3], { })); // You have passed 4 arguments.

The rest parameter eliminates the need to check the args array and allows us to apply map(), filter() and reduce() on the parameters array.

Example:
Modify the function sum using the rest parameter in such a way that the function sum is able to take any number of arguments and return their sum.

const sum = (x, y, z) => {
  const args = [x, y, z];
  return args.reduce((a, b) => a + b, 0);
}

=
const sum = (...args) => {
  return args.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3)); // 6

- Use the Spread Operator to Evaluate Arrays In-Place

const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr); // returns 89

...arr returns an unpacked array. In other words, it spreads the array. However, the spread operator only works in-place, like in an argument to a function or in an array literal. 

Example:
const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
let arr2;
arr2 = [];  // Change this line

Copy all contents of arr1 into another array arr2 using the spread operator:
const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
let arr2;
arr2 = [...arr1];

- Use Destructuring Assignment to Extract Values from Objects

Destructuring assignment is special syntax introduced in ES6, for neatly assigning values taken directly from an object.

const user = { name: 'John Doe', age: 34 };

Here's an equivalent assignment statement using the ES6 destructuring syntax:

const { name, age } = user;
// name = 'John Doe', age = 34

You can extract as many or few values from the object as you want.

- Use Destructuring Assignment to Assign Variables from Objects

const user = { name: 'John Doe', age: 34 };

Here's how you can give new variable names in the assignment:

const { name: userName, age: userAge } = user;
// userName = 'John Doe', userAge = 34

You may read it as "get the value of user.name and assign it to a new variable named userName" and so on.

Example2: 

const HIGH_TEMPERATURES = {
  yesterday: 75,
  today: 77,
  tomorrow: 80
};

const {today: highToday, tomorrow: highTomorrow} = HIGH_TEMPERATURES; 

- Use Destructuring Assignment to Assign Variables from Nested Objects

const user = {
  johnDoe: { 
    age: 34,
    email: 'johnDoe@freeCodeCamp.com'
  }
};

Here's how to extract the values of object properties and assign them to variables with the same name:

const { johnDoe: { age, email }} = user;
And here's how you can assign an object properties' values to variables with different names:

const { johnDoe: { age: userAge, email: userEmail }} = user;

Example 2:

const LOCAL_FORECAST = {
  yesterday: { low: 61, high: 75 },
  today: { low: 64, high: 77 },
  tomorrow: { low: 68, high: 80 }
};

const {today: {low: lowToday, high: highToday}} = LOCAL_FORECAST;

- Use Destructuring Assignment to Assign Variables from Arrays

const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b); // 1, 2

The variable a is assigned the first value of the array, and b is assigned the second value of the array. We can also access the value at any index in an array with destructuring by using commas to reach the desired index:

const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c); // 1, 2, 5

Example:

let a = 8, b = 6;

Use destructuring assignment to swap the values of a and b so that a receives the value stored in b, and b receives the value stored in a:

[a, b] = [b, a];

- Use Destructuring Assignment with the Rest Parameter to Reassign Array Elements

const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b); // 1, 2
console.log(arr); // [3, 4, 5, 7]

Variables a and b take the first and second values from the array. After that, because of the rest parameter's presence, arr gets the rest of the values in the form of an array.

- Use Destructuring Assignment to Pass an Object as a Function's Parameters

In some cases, you can destructure the object in a function argument itself.

const profileUpdate = (profileData) => {
  const { name, age, nationality, location } = profileData;
  // do something with these variables
}
This effectively destructures the object sent into the function. This can also be done in-place:

const profileUpdate = ({ name, age, nationality, location }) => {
  /* do something with these fields */
}
When profileData is passed to the above function, the values are destructured from the function parameter for use within the function.

Example:
const stats = {
  max: 56.78,
  standard_deviation: 4.34,
  median: 34.54,
  mode: 23.87,
  min: -0.75,
  average: 35.85
};
const half = (stats) => (stats.max + stats.min) / 2.0; 

Use destructuring assignment within the argument to the function half to send only max and min inside the function:
const half = ({ max, min }) => (max + min) / 2.0;

- Create Strings using Template Literals
 
A new feature of ES6 is the template literal. This is a special type of string that makes creating complex strings easier.

Template literals allow you to create multi-line strings and to use string interpolation features to create strings.

Consider the code below:

const person = {
  name: "Zodiac Hasbro",
  age: 56
};

// Template literal with multi-line and string interpolation
const greeting = `Hello, my name is ${person.name}!
I am ${person.age} years old.`;

console.log(greeting); // prints
// Hello, my name is Zodiac Hasbro!
// I am 56 years old.

- Write Concise Object Literal Declarations Using Object Property Shorthand

const getMousePosition = (x, y) => ({
  x: x,
  y: y
});

Here is the same function from above rewritten to use this new syntax:

const getMousePosition = (x, y) => ({ x, y });

- Write Concise Declarative Functions with ES6

When defining functions within objects in ES5, we have to use the keyword function as follows:

const person = {
  name: "Taylor",
  sayHello: function() {
    return `Hello! My name is ${this.name}.`;
  }
};

With ES6, You can remove the function keyword and colon altogether when defining functions in objects. Here's an example of this syntax:

const person = {
  name: "Taylor",
  sayHello() {
    return `Hello! My name is ${this.name}.`;
  }
};

- Use class Syntax to Define a Constructor Function

class Vegetable {
  constructor(name) {
    this.name = name;
  }
}

const carrot = new Vegetable('carrot');
console.log(carrot.name); // Should display 'carrot'

- getter setter

class Thermostat {
  constructor(fahrenheit) {
    this.fahrenheit = fahrenheit;
  }
  
  get temperature() {
    return (5 / 9) * (this.fahrenheit - 32);
  }
  
  set temperature(celsius) {
    this.fahrenheit = (celsius * 9.0) / 5 + 32;
  }
}

- Use export to Share a Code Block

export const add = (x, y) => {
  return x + y;
}
The above is a common way to export a single function, but you can achieve the same thing like this:

const add = (x, y) => {
  return x + y;
}

export { add };

When you export a variable or function, you can import it in another file and use it without having to rewrite the code. You can export multiple things by repeating the first example for each thing you want to export, or by placing them all in the export statement of the second example, like this:

export { add, subtract };

- Reuse JavaScript Code Using import

import allows you to choose which parts of a file or module to load. In the previous lesson, the examples exported add from the math_functions.js file. Here's how you can import it to use in another file:

import { add } from './math_functions.js';

Here, import will find add in math_functions.js, import just that function for you to use, and ignore the rest. The ./ tells the import to look for the math_functions.js file in the same folder as the current file. The relative file path (./) and file extension (.js) are required when using import in this way.

You can import more than one item from the file by adding them in the import statement like this:

import { add, subtract } from './math_functions.js';

Example:

import {uppercaseString, lowercaseString} from './string_functions.js';

- Use * to Import Everything from a File
- 
Suppose you have a file and you wish to import all of its contents into the current file. This can be done with the import * as syntax. Here's an example where the contents of a file named math_functions.js are imported into a file in the same directory:

import * as myMathModule from "./math_functions.js";
The above import statement will create an object called myMathModule. This is just a variable name, you can name it anything.

- Create an Export Fallback with export default

// named function
export default function add(x, y) {
  return x + y;
}

// anonymous function
export default function(x, y) {
  return x + y;
}

- Import a Default Export

import add from "./math_functions.js";

- Complete a Promise with resolve and reject

const myPromise = new Promise((resolve, reject) => {
  if(condition here) {
    resolve("Promise was fulfilled");
  } else {
    reject("Promise was rejected");
  }
});

- Handle a Fulfilled Promise with then

const makeServerRequest = new Promise((resolve, reject) => {
  // responseFromServer is set to true to represent a successful response from a server
  let responseFromServer = true;
    
  if(responseFromServer) {
    resolve("We got the data");
  } else {  
    reject("Data not received");
  }
});

makeServerRequest.then(result => {
  console.log(result);
});

- Handle a Rejected Promise with catch

catch is the method used when your promise has been rejected. It is executed immediately after a promise's reject method is called. Here’s the syntax:

``myPromise.catch(error => {
  // do something with the error.
});``











