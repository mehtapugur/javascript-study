## JavaScript Notes


JavaScript provides eight different data types which are
 1. undefined
 2. null
 3. boolean
 4. string
 5. symbol
 6. bigint
 7. number
 8. object

Variable names can be made up of numbers, letters, and $ or _, but may not contain spaces or start with a number.

When JavaScript variables are declared, they have an initial value of undefined. If you do a mathematical operation on an undefined variable your result will be NaN which means "Not a Number".

In JavaScript all variables and function names are case sensitive.

Not all real numbers can accurately be represented in floating point. This can lead to rounding errors.

The remainder operator `%` gives the remainder of the division of two numbers.

`var myName = "your name";`
`"your name"` is called a string literal. It is a string because it is a series of zero or more characters enclosed in single or double quotes.

In JavaScript, you can escape a quote from considering it as an end of string quote by placing a backslash (\) in front of the quote.

`var sampleStr = "Alan said, \"Peter is learning JavaScript\".";`

```goodStr = 'Jake asks Finn, "Hey, let\'s go on an adventure?"'; 
 badStr = 'Finn responds, "Let's go!"'; // Throws an error```

In the goodStr above, you can use both quotes safely by using the backslash \ as an escape character.

- Code	- Output

   \'   	single quote
  \"	    double quote
  \\	    backslash
  \n	    newline
  \r    	carriage return
  \t	    tab
  \b	    word boundary
  \f	    form feed
  
In JavaScript, String values are immutable, which means that they cannot be altered once created.
Note that this does not mean that myStr cannot be changed, just that the individual characters of a string literal cannot be changed. The only way to change myStr would be to assign it with a new string, like this:

```var arr = [
  [1,2,3],
  [4,5,6],
  [7,8,9],
  [[10,11,12], 13, 14]
];
arr[3]; // equals [[10,11,12], 13, 14]
arr[3][0]; // equals [10,11,12]
arr[3][0][1]; // equals 11```

`.pop()` removes the last element from an array and returns that element

 `.shift()` It removes the first element
 
 `.unshift()` adds the element at the beginning of the array.
 
 It is possible to have both local and global variables with the same name. When you do this, the local variable takes precedence over the global variable.

 In order for JavaScript to compare two different data types (for example, numbers and strings), it must convert one type to another. This is known as "Type Coercion". Once it does, however, it can compare terms as follows:
 ```
1   ==  1   // true
1   ==  2   // false
1   == '1'  // true
"3" ==  3   // true ```

- Comparison with the Strict Equality Operator
`
3 ===  3   // true
3 === '3'  // false`

3 == '3'  // returns true because JavaScript performs type conversion from string to number
3 === '3' // returns false because the types are different and type conversion is not performed

- Note
In JavaScript, you can determine the type of a variable or a value with the typeof operator, as follows:
typeof 3   // returns 'number'
typeof '3' // returns 'string'

- Inequality Operator

    `3 !==  3   // false
    3 !== '3'  // true
    4 !==  3   // true `

- Using Objects for Lookups
   Objects can be thought of as a key/value storage, like a dictionary. If you have tabular data, you can use an object to "lookup" values rather than a switch statement or an      if/else chain. This is most useful when you know that your input data is limited to a certain range.
   
     ```var alpha = {
        1:"Z",
        2:"Y",
        3:"X",
        4:"W",
        ...
        24:"C",
        25:"B",
        26:"A"
    };
    alpha[2]; // "Y"
    alpha[24]; // "C"```
    

```var myStorage = {
  "car": {
    "inside": {
      "glove box": "maps",
      "passenger seat": "crumbs"
     },
    "outside": {
      "trunk": "jack"
    }
  }
};```
 
Access the myStorage object and assign the contents of the glove box property to the gloveBoxContents variable:

`var gloveBoxContents = myStorage.car.inside["glove box"];`

The `hasOwnProperty()` method returns a boolean indicating whether the object has the specified property as its own property (as opposed to inheriting it).


Create a function called randomRange that takes a range myMin and myMax and returns a random whole number that's greater than or equal to myMin, and is less than or equal to myMax, inclusive:

`function randomRange(myMin, myMax) {
  return Math.floor(Math.random() * (myMax - myMin + 1) + myMin);
}`

The parseInt() function parses a string and returns an integer. Here's an example:

`var a = parseInt("007");`

The above function converts the string "007" to an integer 7. If the first character in the string can't be converted into a number, then it returns NaN.

- Use the parseInt Function with a Radix

The parseInt() function parses a string and returns an integer. It takes a second argument for the radix, which specifies the base of the number in the string. The radix can be an integer between 2 and 36.

The function call looks like:

`parseInt(string, radix);`

And here's an example:

`var a = parseInt("11", 2);`

The radix variable says that "11" is in the binary system, or base 2. This example converts the string "11" to an integer 3.


- Use the Conditional (Ternary) Operator

The conditional operator, also called the ternary operator, can be used as a one line if-else expression.

The syntax is:

condition ? expression-if-true : expression-if-false;

The following function uses an if-else statement to check a condition:
`
function findGreater(a, b) {
  if(a > b) {
    return "a is greater";
  }
  else {
    return "b is greater";
  }
} `
This can be re-written using the conditional operator:
`
function findGreater(a, b) {
  return a > b ? "a is greater" : "b is greater";
}
`

- Use Multiple Conditional (Ternary) Operators

`function findGreaterOrEqual(a, b) {
  return (a === b) ? "a and b are equal" 
    : (a > b) ? "a is greater" 
    : "b is greater";
}`


`function countdown(n){
  if (n < 1) {
    return [];
  } else {
    const arr = countdown(n - 1);
    arr.unshift(n); //add the beginning
    return arr;
  }
}`
= [5,4,3,2,1];

We have defined a function named rangeOfNumbers with two parameters. The function should return an array of integers which begins with a number represented by the startNum parameter and ends with a number represented by the endNum parameter. The starting number will always be less than or equal to the ending number. Your function must use recursion by calling itself and not use loops of any kind. It should also work for cases where both startNum and endNum are the same:

`function rangeOfNumbers(startNum, endNum) {
   if (endNum - startNum === 0) {
    return [startNum];
  } else {
    var numbers = rangeOfNumbers(startNum, endNum - 1);
    numbers.push(endNum);
    return numbers;
  }
};`






