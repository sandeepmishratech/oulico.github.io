---
layout: post
title: "Notes: DataType in Javascript"
date: 2021-09-01 16:04:50 +0200
categories: Notes-JavaScript
tags: Notes, JavaScript, DataType
---

Data Types in JS!

There are two types of value in JS.

For now, let's focus on primitive data types.

+ Object

  ```js
  let me = {
    name: 'Jonas'
  };
  
  ```

+ Primitive

  ```js
  let firstName = 'Jonas';
  let age = 30; 
  ```





### 7 primitive data types



| Data types | Examples                |                                                 |
| ---------- | ----------------------- | ----------------------------------------------- |
| Number     | `let age = 23;`         |                                                 |
| String     | `let userName = 'Bill'` |                                                 |
| Boolean    | `let isMale = true;`    |                                                 |
| Undefined  | `let currentJob;`       |                                                 |
| Null       |                         |                                                 |
| Symbol     | `let sym1 = Symbol()`   |                                                 |
| big int.   | `BigInt()`              | to represent whole numbers larger than 2^53 - 1 |



#### Numbers

```js
let age = 23;
```



They are all floating point numbers. So, It is used for `decimals` and `integers`

All numbers are simply of the type number. (There's only one data type for integers and for decimals in JavaScript)



#### String

```js
let firstName = 'Jason'
```

Text.

always **in quote**.



#### Boolean

```js
let fullAge = true;
```



`True` or `False`

We use boolean for **taking decisions**



#### Undefined

```js
let fullAge = true;
```



Value taken by a variable that is not yet defined ('empty value')



#### Null

'Empty value'

![null](http://oulico.github.io/assets/img/2021-09-03-data-types-in-js/null.png)



#### Symbol (ES2015)

Value that is unique and cannot be changed [not useful for now]



#### BigInt (ES2020)

Larger integers than the Number type can hold.



> JavaScript has [**dynamic typing**](#dynamic-typing): Data types are detemined a utomatically. You don't need to manually define the data type!

> We can assign later a new value with a different data type to the same variable. It can be useful but also, It can make it difficult to find errors in the code.



#### Commenting



##### Comment just 1 line:
```js
//this line will be ignored
```
This can be useful to divide or code into different sections and explain what differnet pieces of code are actually doing in the code.

Or you can comment out some codes when you debug.

> Tip - Short cut for comment in VSC: `command` + `/`





![comment1](/assets/img/2021-09-03-data-types-in-js/comment1.jpg)

---

##### Comment a paragraph
```js
/* Blablabla
you can leave multi line comments like this.
If you want to leave some official messages, 
I recommend you to use this type */
```



![comment2](assets/img/2021-09-03-data-types-in-js/comment2.jpg)



#### Dynamic Typing

The example:

```js
let jsIsFun = true;
//assigned a value that has Boolean data type.

console.log(typeof jsIsFun);
//data type is boolean.

jsIsFun = 'YES!';
//You just assigned a value which has string data type

console.log(typeof jsIsFun);
  
```

Result in console:

![image-20210903104407359](/Users/jhl/workplace/oulico.github.io/assets/img/2021-09-03-data-types-in-js/image-20210903104407359.png)

As you can see here, you can assign a value which has another type of data very simply.



#### Little fun fact of undefined and null

Undefined:

```js
let theYear;
console.log(theYear);
console.log(typeof theYear);
/* When you declare an empty variable like this,
it will automatically hold the value of undefined. */
theYear = 1992;
console.log(typeof theYear);
//You'll see the type is changed to `number` now.
```



Null:

```js
console.log(typeof null);
//you'll get 'object' as the data type but it's not, though.
```

This is a **bug** of JavaScript.

