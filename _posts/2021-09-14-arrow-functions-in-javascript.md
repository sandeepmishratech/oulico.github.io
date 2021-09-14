---
layout: post
title: "Arrow Functions in JavaScript"
date: 2021-09-14 21:14:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript function
---





There is a new type of function that was added to JavaScript in ES6, **Arrow Function**.







## Arrow Function

An arrow function is a special form of `function expression` which is shorter (and faster).

Let's take a look with an example.







### Example

```js
// Arrow function
const calcAge3 = birthYear => 2037 - birthYear;
const age3 = calcAge3(1991);
console.log(age3);
```

`birthYear => 2037 - birthYear;` // First, we write the name of the function and an `arrow(=>)`. And then we write what we want to return. (i.e `2037 - birthYear`)

`const calcAge3 = birthYear => 2037 - birthYear;`// Since this is a function expressions, `birthYear => 2037 - birthYear;` this is a value. So we stored it in a variable, `calcAge3`.







## Why Arrow Functions

+ We don't need the curly braces, any parentheses, etc.
+ The return actually happens implicitly 







## More Complex Arrow Functions

#### 1) single parameter, multiple lines of code

```js
const yearsUntilRetirement = birthYear => {
  const age = 2037 - birthYear;
  const retirement = 65 - age;
  return retirement;
}

console.log(yearsUntilRetirement(1992)); 
```



`const yearsUntilRetirement = birthYear => {` //  We need to add the curly braces to define the code block when we have multiple lines of code.

and then we need to **do the return explicitly**. (Because it is not a one-liner function)



#### 2) multiple parameter, mutiple lines of code

```js
const yearsUntilRetirement = (birthYear, firstName) => {
  const age = 2037 - birthYear;
  const retirement = 65 - age;
  return `${firstName} retires in ${retirement} years`;
}

console.log(yearsUntilRetirement(1992, 'Oulico'));
```



`const yearsUntilRetirement = (birthYear, firstName) =>` // You need `parentheses` to wrap the parameters.



