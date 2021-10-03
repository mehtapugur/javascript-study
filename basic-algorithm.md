#### Convert Celsius to Fahrenheit

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
<hr>

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
<hr>
  
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
<hr>

#### Finders Keepers

  - Solution 1
```js
function findElement(arr, func) {
  let num = 0;
  for (let i = 0; i < arr.length; i++) {
    num = arr[i];
    if (func(num)) {
      return num;
    }
  }
  return undefined;
}
```

  - Solution 2
```js
function findElement(arr, func) {
  return arr.find(func);
}
```

  - Solution 3
```js
function findElement(arr, func) {
  return arr[arr.map(func).indexOf(true)];
}
```

  - Solution 4
```js
function findElement(arr, func) {
  return arr.length && !func(arr[0]) 
    ? findElement(arr.slice(1), func)
    : arr[0];
}
```
<hr>

#### Boo who

  - Solution 1
```js
function booWho(bool) {
  return (bool === true || bool === false)
}
booWho(null);
```

  - Solution 2
```js
function booWho(bool) {
  return typeof bool === "boolean";
}
```

#### Title Case a Sentence

```js
function titleCase(str) {
  var convertToArray = str.toLowerCase().split(" ");
  var result = convertToArray.map(function(val) {
    return val.replace(val.charAt(0), val.charAt(0).toUpperCase());
  });
  return result.join(" ");
}
```

#### Slice and Splice

```js
function frankenSplice(arr1, arr2, n) {
  let newArray = arr2.slice();
  newArray.splice(n, 0, ...arr1);
  return newArray;
}
frankenSplice([1, 2, 3], [4, 5, 6], 1);
```
<hr>

#### Falsy Bouncer

  - Solution 1
```js
function bouncer(arr) {
  return arr.filter(Boolean);
}
bouncer([7, "ate", "", false, 9]);
```

  - Solution 2
```js
function bouncer(arr) {
  let newArray = [];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i]) newArray.push(arr[i]);
  }
  return newArray;
}
```
<hr>

#### Where do I Belong

  - Solution 1
```js
function getIndexToIns(arr, num) {
  arr.sort((a, b) => a - b);
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] >= num)
      return i;
  }
  return arr.length;
}
```

  - Solution 2
```js
function getIndexToIns(arr, num) {
  return arr.filter(val => num > val).length;
} //num dan küçük olan elemanalrın sayısını aldık
```

  - Solution 3
```js
function getIndexToIns(arr, num) {
  // sort and find right index
  let index = arr
    .sort((curr, next) => curr - next)
    .findIndex(currNum => num <= currNum);
  // Returns index or total length of arr
  return index === -1 ? arr.length : index;
}
getIndexToIns([40, 60], 500);
```

  - Solution 4
```js
function getIndexToIns(arr, num) {
  return arr
    .concat(num)
    .sort((a, b) => a - b)
    .indexOf(num);
}
getIndexToIns([1, 3, 4], 2);
```

#### Mutations

```js
function mutation(arr) {
  return arr[1]
    .toLowerCase()
    .split("")
    .every(function(letter) {
      return arr[0].toLowerCase().indexOf(letter) != -1;
    });
}
```

#### Chunky Monkey

```js
function chunkArrayInGroups(arr, size) {
  let newArr = [];
  while (arr.length > 0) {
    newArr.push(arr.splice(0, size));
  }
  return newArr;
}
```
