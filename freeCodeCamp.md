## JavaScript Notes

`my notes`

 **my notes**
 
 - My Notes

<br>

----------------
finished

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

`goodStr = 'Jake asks Finn, "Hey, let\'s go on an adventure?"'; 
 badStr = 'Finn responds, "Let's go!"'; // Throws an error`

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

`var arr = [
  [1,2,3],
  [4,5,6],
  [7,8,9],
  [[10,11,12], 13, 14]
];
arr[3]; // equals [[10,11,12], 13, 14]
arr[3][0]; // equals [10,11,12]
arr[3][0][1]; // equals 11`

`.pop()` removes the last element from an array and returns that element

 `.shift()` It removes the first element
 
 `.unshift()` adds the element at the beginning of the array.
 
 It is possible to have both local and global variables with the same name. When you do this, the local variable takes precedence over the global variable.

 In order for JavaScript to compare two different data types (for example, numbers and strings), it must convert one type to another. This is known as "Type Coercion". Once it does, however, it can compare terms as follows:
 `
1   ==  1   // true
1   ==  2   // false
1   == '1'  // true
"3" ==  3   // true `

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


