# Pure Functions

A __pure function__ is a function that does not change anything outside of its own [scope](#scope).

## By Value

```js
// Impure function
var x = 5;
function addToX(y) {
  x += y;
  return x;
}
addToX(10) // 15
console.log(x) // 15

// Pure function
var x = 5;
function add(y) {
  return x + y;
}
add(10) // 15
console.log(x) // 5
```

Pure functions are pretty easy to write when we [Pass by Value](#passing-by-value).


## By Reference

```js
// Impure function
var list = [1, 2, 3];
function addToList(arr, value) {
  arr.push(value);
  return arr;
}
console.log(addToList(list, 4)); // [1, 2, 3, 4]
console.log(list); // [1, 2, 3, 4]

// Pure function
var list = [1, 2, 3];
function addToList(arr, value) {
  var copy = arr.slice();
  copy.push(value);
  return copy;
}
console.log(addToList(list, 4)); // [1, 2, 3, 4]
console.log(list); // [1, 2, 3]
```

We need to be more careful when we [Pass by Reference](#passing-by-reference)
