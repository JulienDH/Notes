## Some useful links
* [The Difference Between Javascript Primitive Data Types and Objects](http://vicfriedman.github.io/blog/2013/09/15/the-difference-between-javascript-primitive-data-types-and-objects/)

## Basic variable declarations
### Const
The **const** declaration creates a read-only reference to a value. A const variable identifier cannot be reassigned.
### Let
The function **let** allows you to declare variables that are limited in scope to the block, statement, or expression on which it is used.
This is unlike the **var** keyword, which defines a variable globally or locally to an entire function regardless of block scope.

## Using of: =
```javascript
var number = 4, text = '4', result;

result = number == text;
alert(result); // Affiche  « true » alors que « number » est un nombre et « text » une chaîne de caractères

result = number === text;
alert(result); // Affiche « false » car cet opérateur compare aussi les types des variables en plus de leurs valeurs
```

## How to handle Arrays in JavaScript

### Create an Array
```javascript
var points = [40, 100, 1, 5, 25, 10];
```

### Sort an Array
```javascript
points.sort(function(a, b){return b-a});    
// Sort the numbers in the array in descending order
// The first item in the array (points[0]) is now the highest value

points.sort(function(a, b){return a-b});    
// Sort the numbers in the array in acending order
// The first item in the array (points[0]) is now the lowest value
```

### Reverse a string
```javascript
var new_string = my_string.split(``).reverse().join(``)
```
