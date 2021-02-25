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
const doubler = item => item * 2;

It is possible to pass more than one argument into an arrow function.

// multiplies the first input value by the second and returns it
const multiplier = (item, multi) => item * multi;
multiplier(4, 2); // returns 8

- Set Default Parameters for Your Functions

const greeting = (name = "Anonymous") => "Hello " + name;

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






