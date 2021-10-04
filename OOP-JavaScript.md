### Use a Constructor to Create Objects

```js
function Bird() {
  this.name = "Albert";
  this.color  = "blue";
  this.numLegs = 2;
}
let blueBird = new Bird();
```

### Verify an Object's Constructor with instanceof

***instanceof*** ile bir nesnenin o constructor'dan üretilip üretilmediğini kontrol ederiz. True veya false döner.

```js
function House(numBedrooms) {
  this.numBedrooms = numBedrooms;
}
let myHouse = new House(7);
myHouse instanceof House;
```

### Understand Own Properties

In the following example, the Bird constructor defines two properties: name and numLegs:
```js
function Bird(name) {
  this.name  = name;
  this.numLegs = 2;
}
let duck = new Bird("Donald");
```

The following code adds all of the own properties of duck to the array ownProps:
```js
let ownProps = [];
for (let property in duck) {
  if(duck.hasOwnProperty(property)) {
    ownProps.push(property);
  }
}
console.log(ownProps);
```

### Use Prototype Properties to Reduce Duplicate Code

Bütün kuşlar 2 ayağa sahip olacağı için constructor yerine prototype ile numLegs özelliğini ekledik. 
```js
Bird.prototype.numLegs = 2;
```

### Iterate Over All Properties

```js
function Bird(name) {
  this.name = name;  //own property
}
Bird.prototype.numLegs = 2; // prototype property
```

### Understand the Constructor Property

```js
let duck = new Bird();
let beagle = new Dog();
console.log(duck.constructor === Bird); 
console.log(beagle.constructor === Dog);
```
Both of these console.log calls would display true in the console.

### Change the Prototype to a New Object

```js
Bird.prototype = {
  numLegs: 2, 
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```

### Inherit Behaviors from a Supertype

```js
function Animal() { }
Animal.prototype = {
  constructor: Animal,
  eat: function() {
    console.log("nom nom nom");
  }
};
let duck = Object.create(Animal.prototype); // Change this line
let beagle = Object.create(Animal.prototype); 
```

### Override Inherited Methods

```js
function Animal() { }
Animal.prototype.eat = function() {
  return "nom nom nom";
};
function Bird() { }
Bird.prototype = Object.create(Animal.prototype);
Bird.prototype.eat = function() {
  return "peck peck peck";
};
```

### Use a Mixin to Add Common Behavior Between Unrelated Objects

For unrelated objects, it's better to use mixins. A mixin allows other objects to use a collection of functions.
```js
let flyMixin = function(obj) {
  obj.fly = function() {
    console.log("Flying, wooosh!");
  }
};
```
The flyMixin takes any object and gives it the fly method.
```js
let bird = {
  name: "Donald",
  numLegs: 2
};
let plane = {
  model: "777",
  numPassengers: 524
};

flyMixin(bird);
flyMixin(plane);
```

### Understand the Immediately Invoked Function Expression (IIFE)

A common pattern in JavaScript is to execute a function as soon as it is declared:
```js
(function () {
  console.log("Chirp, chirp!");
})();
```
This is an anonymous function expression that executes right away, and outputs Chirp, chirp! immediately.



