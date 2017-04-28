# Truthiness

```js
var name = 'Amir';
!name;  // false
!!name; // true
```

In Javascript, every data type can be interpreted as either __true__ or __false__.
Some of them may seem a bit strange, but honestly it's something you just need to memorize.

To test whether a value is `true` or `false`, simply prepend it with `!!`.
This first __negates__ the value, then __negates__ the __negated__ value, resulting in either `true` or `false.

## Strings

```js
var empty = '';
!!name; // false

var name = 'Amir';
!!name; // true
```

A string is `true` if it has more than one character, and `false` otherwise.

## Numbers

```js
var count = 0;
!!count; // false

var decimal = 0.00;
!!decimal; //false

var age = 31;
!!age; // true

var percent = 3.12;
!!percent; // true
```

## Undefined & Null

Both `underfined` and `null` are falsey.

## Arrays and Objects

```js
var emptyArr = [];
!!emptyArr; // true
!!emptyArr.length; // false

var arr = [1, 2, 3];
!!arr; // true
!!arr.length; // true

var obj = {};
!!obj; // true
```

Arrays and Objects are truthy, even when they're empty.
You wil need to check their contents to derive a useful truthy value.
