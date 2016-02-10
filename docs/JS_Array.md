## How to handle Arrays in JavaScript

### Create an Array
```javascript
var points = [40, 100, 1, 5, 25, 10];
```
or
```javascript
var points = [
  40,
  100,
  1,
  5,
  25,
  10
];
```
or
```javascript
var points = new Array(0, 100, 1, 5, 25, 10);
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
