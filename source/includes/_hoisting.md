# Hoisting

```js
function demostrateHoisting() {
  var foo = 'bar';

  // Function declaration
  function myFunc(x) {
    return x + 1;
  }

  // Function assignment
  var myFunctionVariable = function(y) {
    return y - 1;
  }

  if (foo) {
    myFunc(10);
  }
}
```

Before your Javascript code is executed, the interpreter does a few quick passes that rearrange your code. This process is called __hoisting__.

We'll be using the example code on the right to illustrate this process.

## Function Hoisting

```js
/*
  Original
*/
function demostrateHoisting() {
  var foo = 'bar';

  // Function declaration
  function myFunc(x) {
    return x + 1;
  }

  // Function assignment
  var myFunctionVariable = function(y) {
    return y - 1;
  }

  if (foo) {
    myFunc(10);
  }
}

/*
  After First Pass
*/
function demostrateHoisting() {
  // Moved to top
  function myFunc(x) {
    return x + 1;
  }

  var foo = 'bar';

  // Function declaration
  function myFunc(x) {
    return x + 1;
  }

  // Function assignment
  var myFunctionVariable = function(y) {
    return y - 1;
  }

  if (foo) {
    myFunc(10);
  }
}
```

The interpreter's first pass is to check for any __function declarations__.

Function declarations are statements that __start__ with the `function` keyword, as opposed to __function assignments__, which refers to assigning a function to a variable.

When then interpreter identifies any function declarations, it moves the to the top of the file.

## Variable Hoisting


```js
/*
  After First Pass
*/
function demostrateHoisting() {
  function myFunc(x) {
    return x + 1;
  }

  var foo = 'bar';

  // Function assignment
  var myFunctionVariable = function(y) {
    return y - 1;
  }

  if (foo) {
    myFunc(10);
  }
}

/*
  After Second Pass
*/
function demostrateHoisting() {
  function myFunc(x) {
    return x + 1;
  }

  // Variable declarations moved below function declarations
  var foo;
  var myFunctionVariable;

  foo = 'bar';

  // Function assignment
  myFunctionVariable = function(y) {
    return y - 1;
  }

  if (foo) {
    myFunc(10);
  }
}
```

After the first pass is complete, the interpreter looks for all __variable declarations__ using the `var` keyword, and moves them immediately below the function declarations.

__NOTE:__ the variable declarations are hoisted, but their __assignments__ stay in the same place.


