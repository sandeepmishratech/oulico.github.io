---
layout: post
title: "Function declarations and function expressions"
date: 2021-09-14 13:18:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript function
---



Let's learn about the difference between function declarations and function expressions.



## Function declarations

when you use the **function keyword** to declare a function a bit like we declare a variable.

### Example:

```js
function calcAge1(birthYear) {
  return 2037 - birthYear;
}

const age1 = calcAge1(1991);
console.log(age1);
```



## Function expressions

```js
const calcAge2 function (birthYear){
  return 2037 - birthYear;
}

const age2 = calcAge2(1991);
console.log(age2);
```



`function (birthYear)` // you define a function without keyword. This function without a name (aka anonymous function) is basically an `expression`. Then, it creates a value. So you store that value inside of a variable. like this ↓

`const calcAge2 = function (birthYear)` // 



## Why is it important?

The big difference is that we can call `function declarations` **before they are defined in the code**.



Let's take a look with some examples.



### Examples:

#### 1)

```js
const age1 = calcAge1(1991);

function calcAge1(birthYear) {
  return 2037 - birthYear;
}

console.log(age2);
```

`const age1 = calcAge1(1991);` // As you can see, we called the function here.

`function calcAge1(birthYear)` // And we defined the code.

### Result:

![image-20210914125730446](/assets/img/2021-09-14-function-declarations-vs-expressions/image-20210914125730446.png)



#### 2)

But If you try this with function expressions

```js
const age1 = calcAge2(1991);

const calcAge2 = function (birthYear) {
  return 2037 - birthYear;
};

console.log(age2);

```

`const age1 = calcAge2(1991);` // if you call the function before you define the function,

You'll get an error

### Result:

![image-20210914130016854](/assets/img/2021-09-14-function-declarations-vs-expressions/image-20210914130016854.png)





This happens because of a process called `hoisting`





### Which one should I use?

It depends on your preference.

but for clean code, `function expressions` are better.

Because it forces you to define all the functions at the top of the code and then you can call them later. 

It makes the code more **structured**.



