#### Convert Celsius to FahrenheitPassed

```js
function convertToF(celsius) {
  let fahrenheit = celsius*(9/5) + 32;
  return fahrenheit;
}
convertToF(30);
```

#### Reverse a String

```js
function reverseString(str) {
  return str.split("").reverse().join("");
}
reverseString("hello");
```

#### Factorialize a Number

```js
function factorialize(num) {
  if(num === 0)
    return 1;
  return num *factorialize(num-1);
}
factorialize(5);
```

#### Find the Longest Word in a String

  - Solution 1
```js
function findLongestWordLength(str) {
  return Math.max(...str.split(" ").map(word => word.length));
}
findLongestWordLength("The quick brown fox jumped over the lazy dog");
```

  - Solution 2
```js
function findLongestWordLength(str) {
  let words = str.split(' ');
  let maxLength = 0;

  for (let i = 0; i < words.length; i++) {
    if (words[i].length > maxLength) {
      maxLength = words[i].length;
    }
  }
  return maxLength;
}
```

  - Solution 3
```js
function findLongestWordLength(s) {
  return s.split(' ')
    .reduce(function(longest, word) {
      return Math.max(longest, word.length)
    }, 0);
}
```

  - Solution 4
```js
function findLongestWordLength(str) {
  // split the string into individual words
  const words = str.split(" ");

  // words only has 1 element left that is the longest element
  if (words.length == 1) {
    return words[0].length;
  }

  // if words has multiple elements, remove the first element
  // and recursively call the function
  return Math.max(
    words[0].length,
    findLongestWordLength(words.slice(1).join(" "))
  );
}
```

#### Return Largest Numbers in Arrays

```js
function largestOfFour(arr) {
  return arr.map(function(group) {
    return group.reduce(function(prev, current) {
      return current > prev ? current : prev;
    });
  });
}
```

#### Confirm the Ending

  - Solution 1
```js
function confirmEnding(str, target) {
  return str.slice(-target.length) === target;
}
confirmEnding("Bastian", "n");
```

  - Solution 2
```js
function confirmEnding(str, target) {
  return str.slice(str.length - target.length) === target;
}
confirmEnding("He has to give me a new name", "name");
```

  - Solution 3
```js
function confirmEnding(str, target) {
  let re = new RegExp(target + "$", "i");
  return re.test(str);
}
```

#### Repeat a String Repeat a String

```js
function repeatStringNumTimes(str, num) {
  return num > 0 ? str + repeatStringNumTimes(str, num - 1) : '';
}
```

#### Truncate a String

```js
function truncateString(str, num) {
  return str.length > num ? str.slice(0, num) + "..." : str;
}
```

#### 
