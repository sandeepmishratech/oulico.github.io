---
layout: post
title: "Notes_The diffrence between let and const in JavaScript"
date: 2021-09-02 11:35:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript variable
---

The diffrence between `let` and `const`.



```js
let age = 30;
age = 31;
//reassigning (or mutating) a value is possible with `let`
```

```js
const birthYear = 1991;
birthYear = 1990;
/* you'll get an error:"Uncaught TypeError: Assignment to constant variable."
Value is not mutable with `const` */
```

```js
const currentJob;
/* you'll get an error:"Uncaught SyntaxError: Missing initializer in const declaration". 
You have to initiate the value. */
```

```js
let currentJob;
// at least you don't get an error. 
```



> **For clean code**: Use `Const` as default and use `let` when you're sure that the value will be changed. <u>Less variable mutations = Less potential to make bugs.</u>



### **Never use `var`**



