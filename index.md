---
layout: default
title: Home
nav_order: 1
description: "A hand crafted markdown document contains all major Javascript topics covered, taken from different sources"
permalink: /
---

## Welcome to Javascript Handbook  
JavaScript, often abbreviated as JS, is a high-level, dynamic, weakly typed, object-based, multi-paradigm, and interpreted programming language.

## Comments
---
Single line comments start with `//`. For multi-line commands, you use `/* ... */` 

```js
// This is a single line comment

/*
 And this is
 a multi-line
 comment
 */
 ```

 > JavaScript is case-sensitive. This means that `Hello()` is not the same as `HELLO()` or `hello()`

## Variables
---
You can create variables using `var`, `let`, `const` (the last two ones are available only in ES6). Variable names can't start with a number or contain spaces. They can contain letters, numbers, underscores, or $. Variable names are case sensitive.   

```js
// This is how you define a variable
// `x` will be `undefined`
var x;

// Declare a constant (the convention is to use CAPS for constants)
const FOO = 42;

// Declare another two variables, using `var` and `let`
var hello = 'world';
let bar = 'baz';
```  
Variables don't have a type. As long as they are not constants, you can change their data:   

```js
let foo = 42;
foo = 'bar';
foo
// => 'bar'
```

> In JavaScript the use of semicolons is optional, as a new line indicates the end of the statement.

### `let` vs `var`
They are pretty similar, but unlike `var`, `let` declares a block scope local variable, optionally initializing it to a value. `let` allows you to declare variables that are limited in scope to the block, statement, or expression on which it is used. The `var` keyword which defines a variable to an entire function regardless of block scope.

```js
var a = 42;
if (true) {
  var b = 7;
  let c = 123;
}

// Obviously, we can access the `a` variable
console.log(a);
// => 42

// We can access `b` as well, even it was assigned in the
// if block (see below what happens if the expressions is
// false).
console.log(b);
// => 7

// We cannot access `c` here because it was declared using
// `let`, inside of the `if` block, therefore it's only
// accessible in the `if` block.
console.log(c);
// => Error: c is not defined
```

> JavaScript is a loosely typed language. This means that you can use the same variable for different types of information

Notice how in the first example below, we get the final value of `i` (because we print it after one second). In the other examples `let` does that for us, the `i` value inside of the `setTimeout` (after one second) is the current value of i when the `setTimeout` was called.

```js
for (var i = 0; i < 7; ++i) {
  setTimeout(function () {
    console.log(i);
    // => 7
    // => 7
    // => 7
    // => 7
    // => 7
    // => 7
    // => 7
    // => 7
  }, 1000);
}

for (let i = 0; i < 7; ++i) {
  setTimeout(function () {
    console.log(i);
    // => 0
    // => 1
    // => 2
    // => 3
    // => 4
    // => 5
    // => 6
  }, 1000);
}
```

> A literal is a hard coded value.

### `const`
One time initialisation. You can use it for variables which values remain the same.

```js
const PI = 3.14;

PI = 3;
// => TypeError: Assignment to constant variable.
```

Note, this won't freeze the objects:

```js
// Create an object
const myObj = { foo: 'bar' };

// Update the `foo` field
myObj.foo = 42;

// Add a new field
myObj.hello = 'world';

myObj
// => { foo: 42, hello: 'world' }

// Though, if you try to reset the whole thing, you can't
myObj = {};
// => TypeError: Assignment to constant variable.
```

## `if` statemenets
---
```js
let foo = 42;

if (foo > 40) {
    // do something
} else {
    // do something else
}
```

## Switches
---
```js
let planet = 'Earth';

switch (planet) {
  case "Mercury":
  case "Venus":
    console.log("Too hot here.");
    break;

  case 'Earth' :
    console.log("Welcome home!");
    break;

  case 'Mars' :
    console.log("Welcome to the other home!");
    break;

  case "Jupiter":
  case "Saturn":
  case "Uranus":
  case "Neptune":
  case "Pluto":
    console.log("You may get gold here.");
    break;

  default:
    console.log("Seems you found another planet.");
    break;
}
```

## Loops
---
This will print all the integers from 1 to 42.

### `for`

```js
for (var i = 1; i <= 42; ++i) {
  console.log(i);
}
```

Using `for ... in ...` can be used to iterate object keys:
```js
var name = {
  first: "Johnny",
  last: "B."
};

for (var key in name) {
  if (name.hasOwnProperty(key)) {
    console.log(key, name[key]);
    // "first", "Johnny"
    // "last", "B."
  }
}
```

In ES6 there is a `for ... of` ... as well. It's pretty neat since it iterates any iterable objects (arrays, strings etc).
```js
let numbers = [-1, 7, 42, 64];
for (let num of numbers) {
  console.log(num);
}
// -1
// 7
// 42
// 64

var country = "Bangladesh";

for(let letter of country) {
  console.log(letter);
}

// B
// a
// n
// g
// l
// a
// d
// e
// s
// h
```

### `while`
```js
var i = 1;
while (i <= 42) {
    console.log(i);
    ++i;
}
```

### `do - while`
```js
var i = 0;
do {
    ++i;
    console.log(i);
} while (i < 42);
```

## Data Types
---
Primitive types are types provided by the system, in this case by JavaScript. Primitive type for JavaScript are Booleans, numbers and text. In addition to the primitive types, users may define their own classes. The following ones, are primitives:

### Primitive   
* Booleans: `false`, `true`   
* Numbers: `42`, `3.14`, `0b11010`, `0x16`, `NaN`   
* Strings: `'Earth'`, `"Mars"`   
* Special Values: `undefined`, `null`   
* Symbol (new in ECMAScript 6). A unique and immutable primitive value and may be used as the key of an Object property   
	
### Object    
Object refers to a data structure containing data and instructions for working with the data.

## Strings
---
To make a new string, you can make a variable and give it a value of `new String()`. 
```js
var foo = new String();
```
But, most developers skip that part and use a string literal:
```js
var foo = "my string";
```
### Properties and methods of the String() object  

**concat(text)**  
The concat() function joins two strings.
```js
var foo = "Hello";
var bar = foo.concat(" World!")
alert(bar);	// Hello World!
```
**length**  
Returns the length as an integer.
```js
var foo = "Hello!";
alert(foo.length);
```
**indexOf**  
Returns the first occurrence of a string inside of itself, starting with 0. If the search string cannot be found, -1 is returned. The indexOf() method is case sensitive.
```js
var foo = "Hello, World! How do you do?";
alert(foo.indexOf(' '));	// 6


var hello = "Hello world, welcome to the universe.";
alert(hello.indexOf("welcome"));      // 13
```
**lastIndexOf**  
Returns the last occurrence of a string inside of itself, starting with index 0.. If the search string cannot be found, -1 is returned.
```js
var foo = "Hello, World! How do you do?";
alert(foo.lastIndexOf(' '));	// 24
```
**replace(text, newtext)**  
The replace() function returns a string with content replaced. Only the first occurrence is replaced.
```js
var foo = "foo bar foo bar foo";
var newString = foo.replace("bar", "NEW!")
alert(foo);		// foo bar foo bar foo
alert(newString);	// foo NEW! foo bar foo
```
**slice(start[, end])**  
Slice extracts characters from the start position.
```js
"hello".slice(1);	// "ello"
// When the end is provided, they are extracted up to, but not including the end position.

"hello".slice(1, 3);	// "el"
// Slice allows you to extract text referenced from the end of the string by using negative indexing.

"hello".slice(-4, -2);	// "el"
// Unlike substring, the slice method never swaps the start and end positions. If the start is after the end, slice will attempt to extract the content as presented, but will most likely provide unexpected results.

"hello".slice(3, 1);	// ""
```

**substr(start[, number of characters]**  
substr extracts characters from the start position, essentially the same as slice.
```js
"hello".substr(1);	// "ello"
// When the number of characters is provided, they are extracted by count.

"hello".substr(1, 3);	// "ell"
```

**substring(start[, end])**  
substring extracts characters from the start position.
```js
"hello".substring(1);	// "ello"
// When the end is provided, they are extracted up to, but not including the end position.

"hello".substring(1, 3);	// "el"
// substring always works from left to right. If the start position is larger than the end position, substring will swap the values; although sometimes useful, this is not always what you want; different behavior is provided by slice.

"hello".substring(3, 1);	// "el"
```

**toLowerCase()**   
This function returns the current string in lower case.
```js
var foo = "Hello!";
alert(foo.toLowerCase());	// hello!
```
**toUpperCase()**   
This function returns the current string in upper case.
```js
var foo = "Hello!";
alert(foo.toUpperCase());	// HELLO!
```

**trim()**   
This function removes leading and trailing white spaces from the current string.
```js
var foo = "     This line has unnecessary spaces.      ";
alert(foo.trim()); 			// This line has unnecessary spaces.
```

**charAt(index)**   
This function returns the character at a given index of the current string.
```js
var foo = "Bangladesh";
alert(foo.charAt(3)); 		// g
```

**parseInt(string[, radix])**   
This function parses a numercial string to integer. 
If the radix is specified it parses in the specified numeral system.
Radix can be any integer between 2 and 36.
```js
var foo = "23";
alert(parseInt(foo)); 		// 23
var foo = "1001";
alert(parseInt(foo,2));		// 9
```

**parseFloat(string)**   
This function parses a numercial string to float. 
```js
var foo = "10.589";
alert(parseFloat(foo)); 	// 10.589
var foo = "10";
alert(parseFloat(foo)); 	// 10
```
**Some ES6 workaround**  

```js
// Template Literals or interpolation
let firstName = "Nuhil";
let lastName = "Mehdy";

console.log(`${firstName} ${lastName}`);
```

```js
let country = "Bangladesh";

console.log(country.repeat(3));
console.log(country.startsWith("Bangla"));
console.log(country.endsWith("desh"));
console.log(country.includes("de"));
/*
BangladeshBangladeshBangladesh
true
true
true
*/
```

```js
// Multiline string
let country = `We 
Love
Bangladesh`;

console.log(country);
/*
We 
Love
Bangladesh
*/
```

## Objects
---
A complex type is an object, be it either standard or custom made. Its home is the heap and goes everywhere by reference (e.g. Array, Object). The common way to declare objects is by using the curly braces:
```js
let myObj = { world: "Earth" };
// Or by
// let myObj = new Object({ world: "Earth" });
```

> Objects are compared by reference. That being said, we have this:

```js
let firstObj = {};
let secondObj = {};

// Check if they are equal
firstObj === secondObj
// => false

// Comparing an object with itself...
firstObj === firstObj
// => true

// Let's point the secondObj to firstObj
secondObj = firstObj

// Now they are equal
firstObj === secondObj
// => true
```

Attention: you have no guarantee that adding the object keys in a specific order will get them in the same order.

```js
var site = new Object(); // Required to not cause error in Internet Explorer
site = {};
site.test = function(string) {
	alert("Hello World! " + string);
	site.string = string;
}
site.test("Boo!");
alert(site.string);
```

### Iterating through Objects   
`for` `in` is perfect for iterating through an object.
```js
const gimli = {
    name: "Gimli",
    race: "dwarf",
    weapon: "battle axe",
};

// Iterate through properties of gimli
for (let key in gimli) {
  console.log(gimli[key]);
}

/*
Gimli
dwarf
battle axe
*/
```

```js
// Initialize method on gimli object to return property keys
Object.keys(gimli);

// => ["name", "race", "weapon"]
```

### ES6 Way of creating Objects   
A more cleaner way to add methods in object.
```js
var addStuff = {
  name: "Adder",
  sum(num1, num2) {
    return num1 + num2;
  }
}

console.log(addStuff.name);
// => Adder
console.log(addStuff.sum(5, 10));
// => 15
```

```js
function createAnimal(name, owner){
  return {
    // Properties
    name,
    owner,
    // Create a method
    getInfo(){
      return `${this.name} is owned by ${this.owner}`
    },
    // Objects can contain other objects
  address: {
    street: '123 Main St',
    city: 'Pittsburgh'
  }
  };
}
 
var spot = createAnimal("Spot", "Doug");
 
// Execute method
console.log(`${spot.getInfo()}`);
 
// Access object in the object
console.log(`${spot.name} is at ${spot.address.street}`);
 
// Get properties and methods of object
console.log(`${Object.getOwnPropertyNames(spot).join(" ")}`);

/*
Spot is owned by Doug
Spot is at 123 Main St
name owner getInfo address
*/
```

### Object Destructuring   
```js
function createAnimal(name, owner){
  return {
    // Properties
    name,
    owner,
    // Create a method
    getInfo(){
      return `${this.name} is owned by ${this.owner}`
    },
    // Objects can contain other objects
  address: {
    street: '123 Main St',
    city: 'Pittsburgh'
  }
  };
}
 
var spot = createAnimal("Spot", "Doug");

// You can store values from Objects with destructoring
let { name, owner } = spot;
console.log(`Name : ${name}`);
 
// Get the inner class value
let { address } = spot
console.log(`Address : ${address.street}`);
 
// You can destructor arrays as well
let favNums = [2.718, .5772, 4.6692];
let [,,chaos] = favNums;
console.log(`Chaos : ${chaos}`);
 
// You can use rest items to grab part of an array
let [, ...last2] = favNums;
console.log(`2nd Num : ${last2[0]}`);
 
// This can be used to switch values
let val1 = 1, val2 = 2;
[val1,val2] = [val2,val1];
console.log(`Val2 : ${val2}`);

/*
Name : Spot
Address : 123 Main St
Chaos : 4.6692
2nd Num : 0.5772
Val2 : 1
*/
```

## Arrays
---
All Arrays are untyped, so you can put everything you want in an Array. In addition to objects, the array data is ordered by indexes. Arrays are actually objects, having the indexes (numbers from `0` to `legnth - 1`) as keys.

```js
let fruits = ["apples", "pears", "oranges"];
// Or by 
// var fruits = new Array("apples", "pears", "oranges");

fruits[1]
// => "pears"
```

### Arrays in ES6 way   
```js
// Array.of() is used to create arrays instead of the array
// constructor
let array1 = Array.of(1,2,3);
 
// Create an object into an array
let array2 = Array.from("word");
 
// You can use Array.from to manipulate values
let array3 = Array.from(array1, (value) => value * 2);
 
// Iterate over values
for (let val of array1) {
  console.log(`Array1 Val : ${val}`);
}

for (let val of array2) {
  console.log(`Array2 Val : ${val}`);
}

for (let val of array3) {
  console.log(`Array3 Val : ${val}`);
}

/*
Array1 Val : 1
Array1 Val : 2
Array1 Val : 3
Array2 Val : w
Array2 Val : o
Array2 Val : r
Array2 Val : d
Array3 Val : 2
Array3 Val : 4
Array3 Val : 6
*/
```

### Some Array Operations
```js
> let fruits = ["Apple"]

// Add to the end of the array
> fruits.push("Pear")
2 // < The new length of the array

 [ 'Apple', 'Pear' ]
 //         ^ This was just added

// Add to the start of the array
> fruits.unshift("Orange")
3 // < The new length of the array

 [ 'Orange', 'Apple', 'Pear' ]
 // ^ This was just added

// Access the element at index 1 (the second element)
> fruits[1]
'Apple'

// How many items do we have?
> fruits.length
3

// Turn the Apple into Lemon
> fruits[1] = "Lemon"
'Lemon'

 [ 'Orange', 'Lemon', 'Pear' ]
 //          ^ This was before an Apple

// Insert at index 1 a new element
> fruits.splice(1, 0, "Grapes")
[] // < Splice is supposed to delete things (see below)
   //   In this case we're deleting 0 elements and
   //   inserting one.

 [ 'Orange', 'Grapes', 'Lemon', 'Pear' ]
 //          ^ This was added.

// Get the Lemon's index
> fruits.indexOf("Lemon")
2

// Delete the Lemon
> fruits.splice(2, 1)
[ 'Lemon' ]

 [ 'Orange', 'Grapes', 'Pear' ]
 //                   ^ Lemon is gone

// Remove the last element
> fruits.pop()
'Pear'

 [ 'Orange', 'Grapes' ]
 //                  ^ Pear is gone

// Remove the first element
> fruits.shift()
'Orange'

   [ 'Grapes' ]
 // ^ Orange is gone
 ```
 
**concat()**  
The `concat()` method returns the combination of two or more arrays. To use it, first you need two or more arrays to combine.
```js
var arr1 = ["a","b","c"];
var arr2 = ["d","e","f"];
```
Then, make a third array and set its value to `arr1.concat(arr2)`.
```js
var arr3 = arr1.concat(arr2) //arr3 now is: ["a","b","c","d","e","f"]
```

**join() and split()**  
The `join()` method combines all the elements of an array into a single string, separated by a specified delimiter. If the delimiter is not specified, it is set to a comma. The `split()` is the opposite and splits up the contents of a string as elements of an array, based on a specified delimiter.

To use `join()`, first make an array.
```js
var abc = ["a","b","c"];
```
Then, make a new variable and set it to `abc.join()`.

```js
var a = abc.join(); //"a,b,c"
```
You can also set a delimiter.
```js
var b = abc.join("; "); //"a; b; c"
```
To convert it back into an array with the String object's `split()` method.
```js
var a2 = a.split(","); //["a","b","c"]
var b2 = b.split("; "); //["a","b","c"]
```

### Iterating over Arrays
 There are few ways to loop trough an array.
 
 ```js
 // Using for-loop
var arr = [42, 7, -1]
for (var index = 0; index < arr.length; ++index) {
    var current = arr[index];
    /* Do something with `current` */
}

// Others prefer defining an additional `length` variable:
for (var index = 0, length = arr.length; index < length; ++index) {
    var current = arr[index];
    /* ... */
}
```

**forEach**  
```js
// Another way i using `forEach`:
arr.forEach((current, index, inputArray) => {
    /* Do something with `current` */
});
```

**for of**  
```js
// Or using the for ... of:
for (let current of arr) {
    /* current will be the current element */
}
```

## Symbols
---
A Symbol is like an enumerated type that can be used as identifiers and they can't be changed (immutable).
```js
// Create a symbol that is used like a label in an array
// You can provide a description in quotes
let capital = Symbol("State Capital");
 
let pennsylvania = {};
pennsylvania[capital] = "Harrisburg";
console.log(`Capital of PA : ${pennsylvania[capital]}`);

// => Capital of PA : Harrisburg
```

## Sets
---
List of values with no duplicates.
```js
var randSet = new Set();
randSet.add(10);
randSet.add("Word");
 
// Check to see if set contains a value
console.log(`Has 10 : ${randSet.has(10)}`);
 
// Get size of Set
console.log(`Set Size : ${randSet.size}`);
 
// Delete item from list
randSet.delete(10);
 
// Iterate a Set
for (let val of randSet) 
  console.log(`Set Val : ${val}`);
  
/*
Has 10 : true
Set Size : 2
Set Val : Word
*/
```  

## Maps
---
A collection of key/value pairs
```js
var randMap = new Map();
randMap.set("key1", "Random String");
randMap.set("key2", 10);
 
// Get values
console.log(`key1 : ${randMap.get("key1")}`);
console.log(`key2 : ${randMap.get("key2")}`);
 
// Get size
document.write(`Map Size : ${randMap.size}`);
 
// Iterate Map
randMap.forEach(function(value, key){
  console.log(`${key} : ${value}`);

/*
key1 : Random String
key2 : 10
Map Size : 2
key1 : Random String
key2 : 10
*/
```

## Scope in Javascript
---
In JavaScript, the scope is the current context of the code. It refers to the accessability of functions and variables, and their context.

**Global scope**  
An entity like a function or a variable has global scope, if it is accessible from everywhere in the code.
```js
var a = 99;

function hello() {
  alert("Hello, " + a + "!");
}
hello();    // prints the string "Hello, 99!"
alert(a);   // prints the number 99
console.log("a = " + a); // prints "a = 99" to the console of the browser
```

**Local Scope**  
A local scope exists when an entity is defined in a certain code part, like a function.
```js
var a = 99;

function hello() {
  var x = 5;
  alert("Hello, " + (a + x) + "!");
}
hello();    // prints the string "Hello, 104!"
alert(a);   // prints the number 99
alert(x);   // throws an exception
```

## Functions
---
There are a couple of ways to define functions in JavaScript. The common uses are:
```js
function sum (a, b) {
    return a + b;
}

var sum = function (a, b) {
    return a + b;
}
```
> In JavaScript, functions are first-class objects, because they can have properties and methods just like any other object. Also,can be dynamically created, destroyed, passed to a function, returned as a value, and have all the rights as other variables.

### Functions in ES6

**Arrow Function**   
```js
// Using the  arrow functions
let sum = (a, b) => a + b;
```
Then you can call the function like:
```
let result = sum(40, 2);
// => 42
```
Arrow function is amazing because they would make your `this` behave properly, i.e., `this` will have the same value as in the context of the function—it won’t mutate.
```js
$('.btn').click((event) =>{
  this.sendData()
})

// Or for example
var logUpperCase = function() {
  this.string = this.string.toUpperCase()
  return () => console.log(this.string)
}

logUpperCase.call({ string: 'es6 rocks' })()
```

**Default Value of Parameter**
```js
// Default values are defined next to parameters
function getSum(num1 = 1, num2 = 1){
  console.log(`${num1} + ${num2} = ${num1+num2}`);
 
  // arguments[] only receives the value passed
  console.log(`${arguments[0]} + ${arguments[1]}`)
}
 
getSum(3);

/*
3 + 1 = 4
3 + undefined
*/
```

**Rest Parameters**
```js
// Rest parameters, which are preceeded by ...
// become an array
// You can only have 1 rest parameter and it must
// be defined last
 
function getSumMore(...vals){
  let sum = 0;
  for(let i = 0, len = vals.length; i < len; i++){
    sum += vals[i];
  }
  console.log(`The sum is ${sum}`);
}
 
getSumMore(1,2,3,4);
 
// You can also pass arrays
let vals = [1,2,3,4,5];
getSumMore(...vals);

/*
The sum is 10
The sum is 15
*/
```

## Anonymous functions

A function that was declared without any named identifier to refer to it. As such, an anonymous function is usually not accessible after its initial creation. 

> One common use for anonymous functions is as arguments to other functions. Another common use is as a closure.

**As an argument to other functions**  
```js
setTimeout(function() {
  alert('hello');
}, 1000);
```

**As a closure**  
```js
(function() {
  alert('foo');
})();
```
The surrounding parentheses are a wrapper for the anonymous function. The trailing parentheses initiate a call to the function and can contain arguments. Another way to write the previous example and get the same result:
```js
(function(message) {
  alert(message);
}('foo'));
```

## JavaScript Closures
---
A closure is a function having access to the parent scope, even after the parent function has closed. Or a data structure storing a function together with an environment.

```js
var add = (function () {
    var counter = 0;
    return function () {return counter += 1;}
})();

add();
add();
add();

// the counter is now 3
```
In above example, the self-invoking function only runs once. It sets the counter to zero (0), and returns a function expression. This way add becomes a function. The "wonderful" part is that it can access the counter in the parent scope. This is called a JavaScript closure. It makes it possible for a function to have "private" variables.

## Functional Javascript
---

### Reduce  
Simply means to get some elements and then reduce them to produce a single element.
```js
var myNumbers = [1, 2, 3, 4, 5];
var sumOfAll = myNumbers.reduce(function (a, b) { 
  return a + b
});

console.log(sumOfAll);
```

```js
// A ES6 Version with the usage of Arrow function
let myNumbers = [1, 2, 3, 4, 5];
let sumOfAll = myNumbers.reduce((a, b) => a + b);

console.log(sumOfAll);

// => 15
```

### Filter   
Pulls out filtered elements that pass out a condition.
```js
var myNumbers = [1, 2, 3, 4, 5];
var evenNumbers = myNumbers.filter(value => value % 2 == 0);

console.log(evenNumbers);

// => [ 2, 4 ]
```

### Map  
Performs a given action to every single elements that are passed to it.
```js
var myNumbers = [1, 2, 3, 4, 5];
var doubleNumbers = myNumbers.map(value => value * 2);

console.log(doubleNumbers);

// => [ 2, 4, 6, 8, 10 ]
```

## Constructors and Classes
---
**Constructor**   
The constructor is a function matching the name of the object, and, when called by the new operator, has the keyword this assigned to the newly created instance of the object. The new operator creates a new object based on a constructor and a prototype.
```js
function CoinObject() {
  this.value = 0;
}
var slug = new CoinObject();  // Creates a "slug" - a valueless coin (slug.value = 0).
```

There are a couple of ways you can obtain a class-like functionality in JavaScript (earlier than ES6).

### Using Factory functions   
---
Creating an object and returning it.

```js
function Person (name) {
   // Could be optional
   var self = {};

   // Public field
   self.name = name;

   // Public method
   self.getName = function () {
     // `this` is the `self`
     return this.name;
   };

   return self;
}

var p = Person("Alice");
console.log(p.getName());
// => "Alice"
```

**Getters & Setters**   
```js
var profile = {
  name: "Nuhil",
  age: 30,
  
  set setMyName(name) {
    this.name = name;
  },

  get getMyName() {
    return this.name;    
  }
};

profile.setMyName = "Nuhil Mehdy";
console.log(profile.getMyName);
// => Nuhil Mehdy
```


### Using `prototype`s  
---
A prototype for an object is the set of auto-created fields and methods. It cannot operate by itself, and relies on an existing constructor. When the object is created, the fields initialized in the prototype are copied to the newly created object.
```js
function CoinObject() {
  this.value = 0;
}

CoinObject.prototype.diameter = 1;
slug = new CoinObject();  // A valueless coin (slug.value = 0), with diameter of 1 (slug.diameter = 1)
```

By adding a method in the prototype object of a function, you're adding that method as a public method to all the instances of that class.

```js
function Person (name) {
  this.name = name;
}

Person.prototype.getName = function () {
  // `this` is the `self`
  return this.name;
};

var p = new Person("Bob");
console.log(p.getName());
// => "Bob"
```

**Extending objects**  
To demonstrate, an Animal constructor is used to create an object, a dog called Spot. After that creation, the constructor has a gender property added to it. That gender property is also accessible from the object for Spot.
```js
function Animal (type, name) {
  this.type = type || 'No type';
  this.name = name || 'No name';
}
var dog = new Animal('dog', 'Spot');

// Add gender to the Animal object
Animal.prototype.gender = 'unspecified';
// dog.gender is 'unspecified'

dog.gender = 'male';
// dog.gender is 'male';

delete(dog.gender);
// dog.gender is once again, 'unspecified'
```

**Inheritance by prototypes**   
The prototype of an object can be used to create fields and methods for an object. This prototype can be used for inheritance by assigning a new instance of the superclass to the prototype.

```js
function CoinObject() {
  this.value = 0; 
  this.diameter = 1;
}

function Penny() {
  this.value = 1;
}
Penny.prototype = new CoinObject();

function Nickel() {
  this.value = 5;
}
Nickel.prototype = new CoinObject();
```

**Access Control**  
JavaScript does not provide a direct means to control access to internal variables, however, it is possible to restrict access to some variables. To declare and use a variable as private, there are two steps required:  
* Declare a new variable within the constructor using the var statement.
* Create an anonymous function within the constructor, and assign it as a method for an object.   

```js
function MyObject() {
  this.publicNumber = 10;  // Public field.
  var privateNumber = 20;  // Private variable.

  this.getPrivateNumber = function() {
    return privateNumber;
  }
}

testObject = new MyObject();
```

**Access Super Class Method**  
```js
// Parent class as known as Factory function
function Vehicle(name) {
  this.name = "Vehicle";
}

// Adding methods to its prototype
Vehicle.prototype = {
  drive: function() {
    return this.name + " drives forward";
  },
  stop: function() {
    return this.name + " stops!";
  }
}

// Child class
function Truck(name) {
  this.name = name;
}

// Inheritance from Parent class
Truck.prototype = new Vehicle();
Truck.prototype.constructor = Truck;

// Method overriding and ...
Truck.prototype.drive = function() {
  // Calling Parent class's method
  var driveMsg = Vehicle.prototype.drive.apply(this);
  return driveMsg += " through a field!";
}

// Instance of Child class
var jeep = new Truck("Jeep");
console.log(jeep.drive());
// => Jeep drives forward through a field!
console.log(jeep.stop());
// => Jeep stops!
```

## Classes in ES6
---
```js
class Person {
  constructor (name) {
    this.name = name;
  }
  getName () {
    return this.name;
  }
}

var p = new Person("Carol");
console.log(p.getName());
// => "Bob"
```

**Inherit classes in ES6**  
```js
class Musician extends Person {
   constructor (name, instrument) {
     // Call the base class
     super(name);

     this.instrument = instrument;
   }

   play () {
     console.log(`${this.getName()} is playing ${this.instrument}`);
   }
}

var me = new Musician("Johnny B.", "piano");

// Get the name of the musician, who is also a person
console.log(me.getName());
// => "Johnny B."

me.play();
// => "Johnny B. is playing piano."
```

**Getters & Setters Example**  
```js
class Mammal{
  constructor(name){
    this._name = name;
  }
 
  // Getter
  get name() {
    return this._name;
  }
 
  // Setter
  set name(name){
    this._name = name;
  }
 
  // Static Mammal creator
  static makeMammal(name){
    return new Mammal(name);
  }
 
  getInfo(){
    return `${this.name} is a mammal`;
  }
 
}

// Create an object
let monkey = new Mammal("Fred");
 
// Change name
monkey.name = "Mark";
 
// Call getter
console.log(`Mammal : ${monkey.name}`);
 
// Create Mammal using static function
let chipmunk = Mammal.makeMammal("Chipper");
console.log(`Mammal 2 : ${chipmunk.name}`);

/*
Mammal : Mark
Mammal 2 : Chipper
*/
```

A more detail example:
```js
class Animal {
  constructor(name){
    this.name = name;
  }
 
  toString(){
    return "Animal is named " + this.name;
  }
 
  // We can create static functions as well
  static getAnimal(){
    return new Animal("No Name");
  }
 
}
 
class Dog extends Animal{
  constructor(name, owner){
 
    // We can call the super class now
    super(name);
    this.owner = owner;
  }
 
  toString(){
 
    // You can call super class methods as well
    return super.toString() + " \nDog is named " + this.name;
  }
}
 
var rover = new Dog("Rover", "Paul");
 
console.log(rover.name + " is owned by " + rover.owner);
 
console.log(rover.toString());
 
// Call the static function
var bowser = Animal.getAnimal();
console.log("Bowser info : " + bowser.toString());
/*
Rover is owned by Paul
Animal is named Rover 
Dog is named Rover
Bowser info : Animal is named No Name
*/
```

## Async vs Sync
---
Sometimes you have to wait a little bit for things to be done: such as when making a cake, you have to work on it and you have to wait a while for it to be ready. Most familiar things in our lives are asynchronous.

### Sync   
Usually, synchronous operations send the response directly, using the `return` keyword:
```js
// Synchronous sum
function sum (a, b) {
  return a + b;
}
var result = sum(40, 2);
// => 42
```

### Async  
To have an async function, you need a source of async stuff. In this example, we will use the `setTimeout` function. It accepts a function as first argument (which is called callback function) and a number as second argument—representing the time delay after the function is called:

```js
function asyncSum(a, b, adder) {
  console.log("I am working in other stuffs...");
  
  setTimeout(function() {
    let sum = a + b;
    adder(sum);
  }, 5000);
}

asyncSum(10, 10, function(result) {
  console.log(result);
});
```

## Callbacks
---
Callbacks are functions which are sent as an argument to another function and are invoked when something happens.
```js
// An usual factory function
function Cake(type) {
  self.type = type;
  
  self.getName = function() {
    return this.type;  
  }
  
  return self;
}

var busy = false;

// The async function
function makeCake (type, callback) {
  
  if (busy) {
    return callback(new Error("Busy with a cake."), new Cake(type));
  }  
  
  busy = true;
  
  // fake the processing time by using setTimeout
  setTimeout(function() {
    callback(null, new Cake(type));
    busy = false;
  }, 2000);
}

// make use of that async function
makeCake("Apple", function(err, cake) {
  if (err) { console.error(err); }
  console.log("Made an " + cake.getName() + " cake!");
});

// make another use of that async function
makeCake("Peach", function(err, cake) {
  if (err) { console.error(err); }
  console.log("Made a " + cake.getName() + " cake!");
});
```

## Promises
---

A Promise object represents an operation which has *produced or will **eventually** produce a value*. Promises provide a robust way to wrap the (possibly pending) result of asynchronous work, mitigating the problem of deeply nested callbacks (known as "callback hell").

**States and control flow**   
A promise can be in one of three states:
* pending — The underlying operation has not yet completed, and the promise is pending fulfillment.
* fulfilled — The operation has finished, and the promise is fulfilled with a value. This is analogous to returning a value from a synchronous function.
* rejected — An error has occurred during the operation, and the promise is rejected with a reason. This is analogous to throwing an error in a synchronous function.   

```js
// A Promise that is handled immediately
var p1 = Promise.resolve('Resolve Me');
 
// then takes 2 optional arguments being first a callback
// for a success and another for failure
p1.then((res) => console.log(`${res}`));

// => Resolve Me
```

A promise is said to be settled (or resolved) when it is either fulfilled or rejected. Once a promise is settled, it becomes immutable, and its state cannot change. The then and catch methods of a promise can be used to attach callbacks that execute when it is settled. These callbacks are invoked with the fulfillment value and rejection reason, respectively.

The `then` and `catch` methods can be used to attach fulfillment and rejection callbacks:
```js
promise.then(function(value) {
    // Work has completed successfully,
    // promise has been fulfilled with "value"
}).catch(function (reason) {
    // Something went wrong,
    // promise has been rejected with "reason"
});
```

```js
let randVal = 18;
 
var p3 = new Promise(function(resolve, reject){
  if (randVal == 6){
    resolve("Good Value");
  } else {
    reject("Bad Value");
  }
});
 
p3.then((val) => console.log(`${val}`),
        (err) => console.log(`${err}`));

// => Bad Value
```	

```js
function sum (a, b) {
   return Promise(function (resolve, reject) {
     // Let's wait a second and only then send the response
     setTimeout(function () {
       if (typeof a !== "number" || typeof b !== "number") {
         return reject(new TypeError("Please provide two numbers to sum."));
       }
       resolve(a + b);
     }, 1000);
   });
}

var myPromise = sum(40, 2);

myPromsise.then(function (result) {
  // After one second we have the response here
  console.log("> Summed 40 + 2: ", result);

  // Let's pass some invalid data and return another promise
  return sum(null, "foo");
}).then(function () {
  // This won't be called because we have an error
}).catch(function (err) {
  // Instead, this `catch` handler is called: (after another second)
  console.error(err);
  // => Please provide two numbers to sum.
});
```

## Modules
In ES5 for example in Nodejs which makes use of CommonJS, let’s say we have `port` variable and `getAccounts` method in `module.js`:
```js
module.exports = {
  port: 3000,
  getAccounts: function() {
    ...
  }
}
```
In ES5 `main.js`, we would require that dependency:

```js
var service = require('module.js')
console.log(service.port) // 3000
```

### Modules in ES6
---
In ES6, we would use export and import. For example, this is our library in the ES6 `module.js` file:
```js
export var port = 3000
export function getAccounts(url) {
  ...
}
```
In the importer ES6 file `main.js`, we use `import {name} from 'my-module'` syntax. For example,
```js
import {port, getAccounts} from 'module'
console.log(port) // 3000
```
Or we can import everything as a variable service in `main.js`:
```js
import * as service from 'module'
console.log(service.port) // 3000
```

## Create and throw errors
---
To create an error, you have to use the `Error` constructor:
```js
let myError = new Error("Something went really wrong.");

// You can even append custom data here
myError.code = "MY_FANCY_ERROR_CODE";
```

To throw an error, you have to use the `throw` statement:
```js
throw new Error("Something bad happened.");
```   

There are few types of errors. For example, if you validate the arguments passed to a function, use `TypeError`:
```js
function sayHello(message) {
  if (typeof message !== "string") {
    throw new TypeError("The message should be a string.");
  }
  console.log(message);
}
```

## Error handling
---
In general, it is a good practice to validate the data you're passing to function (especially when they are coming from the user input). This way you can avoid `TypeError`s to be thrown.

If there's a function which throws an error by design, you can catch it using `try - catch`:
```js
function assert (truly) {
  if (!truly) {
    throw new Error("Not true.");
  }
}

try {
  // This will *not* throw an error
  assert(42 === 42);

  // This will throw an error, so that will go in the catch
  assert(42 === -1);

  // Everything put after the place where the error was thrown
  // is not executed
} catch (e) {
  console.error(e);
  // => Not true.
}
```

Note if you have an async function (either callback-based or which returns a promise), you'll do something like this:
```js
// Callback
fetchDataFromServer(function (err, data) {
  if (err) {
    /* do something if you have an error */
  } else {
    /* Do something with `data` */
  }
});
```

```js
// Promise
fetchDataFromServer().then(function (data) {
    /* Do something with `data` */
}).catch(function (err) {
    /* do something if you have an error */
});
```
	
## Strict Mode
---
The strict mode, when turned on, shows potential errors made by the developer:
```js
a = 42;
// 42

"use strict";
b = 42;
// Error: `b` is not defined
```
It can also be enabled for a single function only:
```js
function myfun(){
  "use strict";
  var myvar = 6;
}
```
Strict mode ensures the following:

* New variables need to be declared with "var"; "var" is no longer optional.
* Attempts to write to non-writable variables throw an error rather than silently doing nothing.
* Attempts to delete undeletable properties throw an error rather than silently doing nothing.
* Octal numerals are disallowed.

## Regular expressions
---
Regular expressions can be used to match things in strings, such as numbers:
```js
// Get all the numbers from this input (note you'll get an array of strings)
> "Alice was born in 1974, so she's 42 years old in 2016.".match(/[0-9]+/g)
[ '1974', '42', '2016' ]

// Want to get numbers? Map them using the `Number` function
> "Alice was born in 1974, so she's 42 years old in 2016.".match(/[0-9]+/g).map(Number)
[ 1974, 42, 2016 ]

// BE CAREFUL that if there's no match `match` will return `null`
> "Bob is seven years old.".match(/[0-9]+/g)
null
```

Also, they can be used to replace parts of the strings:
```js
// Mask all the digits of a credit card number, but the last 4
> "1234234534564567".replace(/\d(?=\d{4})/g, "*");
'************4567'
```

## Math functions and constants
---
```js
// Get the PI number
> Math.PI
3.141592653589793

// Get the E number
> Math.E
2.718281828459045

// Maximum between two numbers
> Math.max(7, 42)
42

// Minimum between numbers (arguments)
> Math.min(7, 42, 255, 264)
7

// Power
> Math.pow(2, 4)
16

// Random number between 0 (inclusive) and 1 (exclusive)
> Math.random()
0.2114640628617317

// Round
> Math.round(41.8)
42
```

## Dates
---
A Date is an object that contains a given time to millisecond precision. Unlike strings and numbers, the date must be explicitly created with the new operator.
```js
var now = new Date();
now.getFullYear();
// => 2016
```
By default, the Date object contains the current date and time found on the computer, but can be set to any date or time desired.

```js
var time_before_2000 = new Date(1999, 12, 31, 23, 59, 59, 999);
```

## Handling JSON
---
Handling JSON may require adding a supporting library, which creates the global JSON object. This object is present natively only in new browsers (e.g. FF 3.5, IE8).

```js
//Parsing JSON:
var myObject = JSON.parse(myJSONtext)

//Creating JSON:
var myJSONText = JSON.stringify(myObject);
```

## Imperative VS Object Oriented VS Functional Approach
---
A simple use case where users are prompted to input some words after clicking on a button and they get back all words capitalized their first letter; could be solved by all different paradigms.
### Imperative
```js
var result;
function getText() {
  var someText = prompt("Give me something to capitalize");
  capWords(someText);
  alert(result.join(" "));
};
function capWords(input) {
  var counter;
  var inputArray = input.split(" ");
  var transformed = "";
  result = [];
  for (counter = 0; counter < inputArray.length; counter++) {
    transformed = [
      inputArray[counter].charAt(0).toUpperCase(), 
      inputArray[counter].substring(1)
    ].join("");
    result.push(transformed);
  }
};
document.getElementById("main_button").onclick = getText;
```
In the above approach: Variables are being defined on the global scope. Values are being passed around and modified by functions. DOM methods are being mixed with native JavaScript. The function names are not very descriptive, and that’s due in part to the fact that the whole thing relies on a context that may or may not exist.

### Object Oriented
```js
(function() {
  "use strict";
  var SomeText = function(text) {
    this.text = text;
  };
  SomeText.prototype.capify = function(str) {
    var firstLetter = str.charAt(0);
    var remainder = str.substring(1);
    return [firstLetter.toUpperCase(), remainder].join("");
  };
  SomeText.prototype.capifyWords = function() {
    var result = [];
    var textArray = this.text.split(" ");
    for (var counter = 0; counter < textArray.length; counter++) {
      result.push(this.capify(textArray[counter]));
    }
    return result.join(" ");
  };

  document.getElementById("main_button").addEventListener("click", function(e) {
    var something = prompt("Give me something to capitalize");
    var newText = new SomeText(something);
    alert(newText.capifyWords());
  });
}());
```
In the above approach: Methods live on the new object’s prototype to keep memory use low. And all of the code is isolated in an anonymous immediately-invoked function expression so it doesn’t litter the global scope. There’s even a "use strict" directive to take advantage of the latest JavaScript engine, and the old-fashioned onclick method has been replaced with a shiny new `addEventListener`.   
There are still many artifacts of the same imperative style that led us here. The methods in the constructor function rely on variables that are scoped to the parent object. There’s a looping construct for iterating across all the members of the array of strings. There’s a `counter` variable that serves no purpose other than to increment the progress through the `for` loop.

### Functional
```js
(function() {
  "use strict";
  var capify = function(str) {
    return [str.charAt(0).toUpperCase(), str.substring(1)].join("");
  };
  var processWords = function(fn, str) {
    return str.split(" ").map(fn).join(" ");
  };
  document.getElementById("main_button").addEventListener("click", function(e) {
    var something = prompt("Give me something to capitalize");
    alert(processWords(capify, something));
  });
}());
```
In the above approach: There are two functions, `capify` and `processWords`. Each of these functions is pure, meaning that they don’t rely on the state of the code they’re called from. The functions don’t create side effects that alter variables outside of themselves.

## Design Patterns
---
### Singleton 
Singletons are used when you only ever want 1 object to be created. Let's say you want to create a game character with fixed stats
```js
function Hero(name){
 
  // Check if the object exists
  if(typeof Hero.instance === 'object'){
 
    // If it does return it
    return Hero.instance;
  }
 
  // if it doesn't then create the hero
  this.name = name;
  Hero.instance = this;
 
  return this;
}
 
var derekHero = new Hero("Superman");
console.log("Are hero is " + derekHero.name);
 
// This won't change the name to Paul
var paulHero = new Hero("Batman");
console.log("Are hero is " + paulHero.name);
```

### Factory  
The factory pattern can be used to generate different objects on request
```js 
function Sword(desc){
  this.weaponType = "Sword";
  this.metal = desc.metal || "Steel";
  this.style = desc.style || "Longsword";
  this.hasMagic = desc.hasMagic || false;
}
 
function Bow(desc){
  this.weaponType = "Bow";
  this.material = desc.material || "Wood";
  this.style = desc.style || "Longbow";
  this.hasMagic = desc.hasMagic || false;
}
 
function WeaponFactory(){};
 
WeaponFactory.prototype.makeWeapon = function(desc){
  var weaponClass = null;
 
  if(desc.weaponType === "Sword"){
    weaponClass = Sword;
  } else if (desc.weaponType === "Bow"){
    weaponClass = Bow;
  } else {
    return false;
  }
 
  return new weaponClass(desc);
 
}
 
var myWeaponFact = new WeaponFactory();
 
var bladeFist = myWeaponFact.makeWeapon({
  weaponType: "Sword",
  metal: "Dark Iron",
  style: "Scythe",
  hasMagic: true
});
 
console.log(bladeFist.weaponType + " of type " + bladeFist.style + " crafted from " + bladeFist.metal);
```
### Decorator  
The decorator pattern allows you alter an object at run time
```js
function Pizza(price){
  this.price = price || 10;
}
 
Pizza.prototype.getPrice = function(){
  return this.price;
}
 
function ExtraCheese(pizza){
  var prevPrice = pizza.price;
 
  pizza.price = prevPrice + 1;
}
 
var myPizza = new Pizza(10);
 
ExtraCheese(myPizza);
 
console.log("Cost of Pizza : $" + myPizza.price);
```

### Observer  
A single object notifies many objects (observers) when a state change occurs.
```js
var Observable = function() {
    this.subscribers = [];
}
 
Observable.prototype = {
    subscribe: function(subscriber) {
        // Add the subscriber object to the list
        this.subscribers.push(subscriber);
    },
    unsubscribe: function(unsubscriber) {
 
        // Cycle through the subscriber array and delete
        // the unsubscriber
        for (i = 0; i < this.subscribers.length; i++) {
            if (this.subscribers[i] === unsubscriber) {
                this.subscribers.splice(i, 1);
 
                // We assume it only subscribed once so we
                // leave after it is found
                return unsubscriber.name;
            }
        }
    },
    publish: function(data) {
 
        // Cycle through all subscribers and send them the update
        for (i = 0; i < this.subscribers.length; i++) {
            this.subscribers[i].receiveData(data);
        }
    }
};
 
var OrganFanny = {
  name: "Organ Fanny",
  receiveData: function(data){
    console.log(this.name + " received your info : " + data);
  }
}
 
var BoldmanYaks = {
  name: "Boldman Yaks",
    receiveData: function(data){
      console.log(this.name + " received your info : " + data);
    }
}
 
// Add subscribers and alert them
observable = new Observable();
observable.subscribe(OrganFanny);
observable.subscribe(BoldmanYaks);
observable.publish('IBM at $145.30');
 
console.log(observable.unsubscribe(OrganFanny) + " Unsubscribed");
 
observable.publish('IBM at $145.33');
```

## Some Optimization Workarounds
---
* High Level Optimization
	* Algorithmic Optimization (Mathematical Analysis)
	* Simplification
* Low Level Optimization
	* Loop Unrolling
	* Strength Reduction
	* Duff's Device
	* Clean Loops
* External Tools & Libraries for speeding/optimizing/compressing JavaScript code
