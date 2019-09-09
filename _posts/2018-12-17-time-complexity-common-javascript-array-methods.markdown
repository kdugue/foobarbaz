---
layout: post
title: "Time Complexity Analysis of Common JavaScript Array & Object Methods"
date: 2018-12-17 19:13:46 -0400
categories: jekyll update
---

The plethora of built-in methods available on JavaScript objects and arrays prototypes promises
developers less bugs and more readable code in their applications. These methods provide a variety
of operations on arrays and objects, including: addition, retrieval, removal and many others.

However, it is wise to know and understand not only what is happening “under the hood” when
such methods are implemented, but to also be aware of their time complexity. This post will help
lift the veil on the methods to show what their implementation looks like.

# Objects

Objects are data types that consist of unordered key:value pairs. Keys must be strings, while
values may consist of any type (strings, numbers, booleans, objects, etc)

Object.keys( someObject )

- This method takes in an object and returns an array contain the object’s keys

```
const carInfo = {
  year: 2011,
  make: "Honda",
  model: "Civic LX"
};

Object.keys(carInfo) // ["year", "make", "model"]
```

Time complexity: O(n). Under the hood, JS is iterating through the whole object, and adding
each key of the object to array

Object.values( someObject )

- This method takes in an object and returns an array contain the object’s values

```
const carInfo = {
  year: 2011,
  make: "Honda",
  model: "Civic LX"
};

Object.values(carInfo) // [2011, "Honda", "Civic LX"]
```

Time complexity: O(n). Like the Object.keys() method, JS is iterating through the whole object,
and outputting all values from the object in an array.

Object.hasOwnProperty( key )

- This method takes in a key from the object and returns true if the key exists in the object, false
  if it doesn’t (additionally, returns false in the key has been inherited from another object)

```
const carInfo = {
  year: 2011,
  make: "Honda",
  model: "Civic LX"
};

carInfo.hasOwnProperty("year") // true
carInfo.hasOwnProperty("name") // false
```

Time complexity: O(1). Under the hood, this method is doing a search operation in the carInfo
object. All search operations in an object are O(1).

# Arrays

Arrays in JavaScript are data structures that consist of ordered value or values. Values in JS arrays can
contain any data type (numbers, strings, booleans, etc)

Array.prototype.push( someValue )

- This methods takes in a value and add the value to the end of the array, incrementing the array’s
  length by one.

```
const carMakes = ["Honda", "Mercedes", "Porsche", "Jeep", "Tesla"];

carMakes.push("Toyota");

// carMakes is now
// ["Honda", "Mercedes", "Porsche", "Jeep", "Tesla", "Toyota"]

```

Time complexity: O(1). Since all this method is only adding to the end of the array, there is no
iteration going on.

Array.prototype.pop()

- This method removes the last element from the array, decrementing the length by 1

```
const carMakes = ["Honda", "Mercedes", "Porsche", "Jeep", "Tesla"];

carMakes.pop();

// carMakes is now
// ["Honda", "Mercedes", "Porsche", "Jeep"]
```

Time complexity: O(1). Similar to push, since this method operates on the last element of the
array, it does not require iteration

Array.prototype.shift()

```
const carMakes = ["Honda", "Mercedes", "Porsche", "Jeep", "Tesla"];

carMakes.shift();

// carMakes is now
// ["Mercedes", "Porsche", "Jeep", "Tesla"];
```

Time complexity: O(n). Since arrays are ordered, when an element is removed from the
array (with the exception of the last element in the array), the array needs to update the indexes
for each element in the array, which will be dependent on the number of elements in the array

Array.prototype.unshift( valueToAdd )

- This method add an element to the beginning of the array (value becomes index position 0)

```
const carMakes = ["Honda", "Mercedes", "Porsche", "Jeep", "Tesla"];

carMakes.unshift("Hyundai");

//carMakes is now
// ["Hyundai", "Honda", "Mercedes", "Porsche", "Jeep", "Tesla"];
```

Time complexity: O(n). Since arrays are ordered, when an element is added to the array,
the array needs to update the indexes for each element in the array, which will be dependent
on the number of elements in the array

Array.prototype.concat( arrayToCombine )

- This method takes in an array, and combines it with another array, returning a new array.
  The array passed in add to the end of the array that the method is operating on

```
const carMakes = ["Honda", "Mercedes", "Porsche"];
const otherCarMakes = ["Jeep", "Tesla"];

const allCarMakes = carMakes.concat(otherCarMakes);

// allCarMakes is now ["Honda", "Mercedes", "Porsche", "Jeep", "Tesla"]
```

Time complexity: O(n). Since the result of this method returns a new array, each element from
both arrays are added to the new array, which is done so iteratively.
