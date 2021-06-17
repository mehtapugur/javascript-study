### Solutions

#### 1 

```
function FirstFactorial(num) { 
    return (num === 1 ? 1 : num * FirstFactorial(num - 1));
}
   
FirstFactorial(readline());
```

#### 2

```
function FirstFactorial(number) {
  var factorial = 1;
  for (var i = 1; i <= number; i++) {
    factorial *= i;
  }
  return factorial;
}
   
FirstFactorial(readline());
```

#### 3

```
function FirstFactorial(num) {
  var total = 1;
  while (num >= 1) {
    total *= num;
    num--;
  }
  return total; 
}

FirstFactorial(readline());
```
