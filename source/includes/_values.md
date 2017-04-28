# Value vs. Reference

When you pass data from function to function, or when you assign the value of a variable to another variable, we say that you are __passing__ that data from one place to another.

In Javascript (and most languages) there are two ways of __passing__: by __value__ and by __reference__.

## Passing by Value

```js
// Step 1
var number = 5;

// Step 2
var anotherNumber = number;

// Step 3
anotherNumber += 10;

// Step 4
console.log(number); // 5
console.log(anotherNumber); // 15
```

When you pass a primitive value to a function or reassign it to another variable,
Javascript creates a __copy__ of it in memory. The steps look like this:

__Step 1__

Javascript allocates memory to the number `5` and provides the variable `number` with a reference to that memory.

__Step 2__

Javascript allocates __new__ memory to create a copy of the number five and provides the variable `anotherNumber` with a reference to that new memory.

__Step 3__

Javascript calculates `5 + 10 = 15` and allocates __new__ memory to store `15`. It then provides `anotherNumber` with a reference to that new memory. Once the number `5` (previously referenced by `anotherNumber`) is __de-referenced__, it is destroyed by the [Javascript Garbage Collector](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management).

__Step 4__

When we log the values assigned to `number` and `anotherNumber`, we get `5` and `15`.

## Passing by Reference

```js
// Step 1
var list = [1, 2, 3];

// Step 2
var anotherList = list;

// Step 3
anotherList.push(4);

// Step 4
console.log(list); // [1, 2, 3, 4]
console.log(anotherList); // [1, 2, 3, 4]

// Step 5
var listCopy = list.slice();

// Step 6
listCopy.push(5);

// Step 7
console.log(list); // [1, 2, 3, 4]
console.log(listCopy); // [1, 2, 3, 4, 5]
```

When you pass a compex structures like Arrays and Objects, Javascript simply passes them __by reference__. This means that it simply points the new variable to the same memory as the old variable.

Why? Consider working with large data sets, say an array of size 1,000,000. If we needed to rebuild that array completely every time we passed it to a function, our application would be very slow! We would also be using a considerable amount of memory to maintain all of these seperate copies.

__Step 1__

Javascript allocates memory for an array. Javascript then allocates memory for the numbers `1`, `2`, and `3` and gives the provides the array with references to the memory associated with those three numbers. Javascript then provides a reference to the memory it allocated for the array to the variable `list`.

__Step 2__

Javascript takes the reference to the array currently stored in `list`, copies it, and assigns it to `anotherList`. Both variables now point at the same section of memory.

__Step 3__

Javascript allocates memory for the number `4` and adds it to the array referenced by `anotherList`, which is __the same array__ referenced by `list`.

__Step 4__

When we log the values assigned to `list` and `anotherList`, we can see that they are the same!

__Step 5__

We use the Array.slice() method to create a copy of the `list` array (same process as Step 1), which is then assigned to the variable `listCopy`.

__Step 6__

We then add the number `5` to the `listCopy` array.

__Step 7__

When we log `list` and `listCopy`, we see that their values are now different. This is because we __created a copy__ of list. The copy had its own memory, so the two arrays could act independantly.
