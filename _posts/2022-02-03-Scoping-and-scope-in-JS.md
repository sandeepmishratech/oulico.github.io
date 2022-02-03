---
layout: post
title: "Scoping and scope in JavaScript"
date: 2022-02-03 15:19:50 +0300
categories: Notes-JavaScript
tags: Notes JavaScript Scope Scoping Scope-chain
---

What is scope?





## Concepts





**Scoping**: How our program's variables are **organized** and **accessed** "Where do variables live?" or "Where can we access a certain variable, and where not?"

**Lexical scoping**: Scoping is controlled by **placement** of functions and blocks in the code;

**Scope**: Space or environment in which a certain variable is **declared** (variable environment in case of functions). There is `global scope`, `function scope`, and `block scope`;

**Scope of a variable**: Region of our code where a certain variable can be **accessed**.







## 3 types of scopes

#### Global scope: 

- Outside of any function or block
- Variables declared in global scope are accessible **everywhere**

##### Example:

```js
//GLOBAL SCOPE
const me = `Oulico`;
const job = `Singer`;
const year = `1964`;
```



---

#### Function scope:

- Variables are accessible only inside function, NOT outside
- Also called `local scope`

##### Example:

```js
//FUNCTION SCOPE
function calcAge(birthYear) {
  const now = 2037;
  const age = now - birthYear;
  return age;
}

console.log(now); // ReferenceError
```



---

#### Block Scope (ES6)

- Variables are accessible only inside block (block scoped)

  ⚠︎ **However**, this only applies to **Let** and **const** variables. (if you use `var` instead, the `var` variable will be accessible outside of the block. That is, it would be scoped to the current function or to the global scope. So `var` is function scoped. That is why ES5 variables declared with var only care about functions, but not about blocks.)

- Functions are also block scoped(only in strict mode)

```js
//BLOCK SCOPE (ES6)
if (year >= 1981 && year <= 1996) {
  const millenial = true;
  const food = `Avocado toast`;
}// <-- exaple: if block, for loop block, etc.
console.log(millenial); // ReferenceError
```

---





## Scope Chain





```js
'use strict';

const myName = 'oulico';

function first() {
  const age = 30;

  if (age >= 30) {
    const decade = 3;
    var millenial = true;
  }

  function second() {
    const job = 'singer';

    console.log(`${myName} is a ${age} old ${job}`);
  }
  second();
}

first();
```



As you can see, the variables are in..

Global scope : 

```js
myName = "oulico"
```

`first()` scope:

```js
age = 30
```

`second()` scope:

```js
job = "teacher"
```



How with the JavaScript engine know the values of these variables?

Because, every scope always has access to **all the variables from all its outer scopes**.

So it will be like this:



Global scope:

```js
myName = "oulico"
```

↓

`first()` scope:

```js
age = 30
myName = "oulico"
```

↓

`second()` scope:

```js
job = "teacher"
age = 30 //from first() scope
myName = "oulico" //from Global scope
```



This is how the `scope chain` works. 

(all this also applies to function arguments.)



⚠︎It's important to note that **these variables are not copied form one scope to another**.



⚠︎And what's also important to note is that this **does not work the other way around**.

A certain scope will never have access to the variables of an **inner scope**. 



### difference between var and let/const variables

Now let's look at the examples of `block-scoped`  variable and `function-scoped` variable.

```js
'use strict';

const myName = 'oulico';

function first() {
  const age = 30;

  if (age >= 30) {
    const decade = 3; //<-- let, const = block-scoped
    var millenial = true;  //<-- var is function-scoped
  }

  function second() {
    const job = 'singer';

    console.log(`${myName} is a ${age} old ${job}`);
  }
  second();
}

first();
```



The function-scoped `millenial` variable is actually same as `first()` scope and which means it can be accessed by `second()` scope also.

The `decade` variable is in the `if block` scope and which means it has an access to `first()`scope and `global` scope, but it doesn't have an access to `second()` scope.

 And `second()` scope either doesn't have access to `if block` scope.



![image-20220203174252188](/assets/img/2022-02-03-Scoping-and-scope-in-JS/image-20220203174252188.png)





Why is that? it's because of lexical scoping



## Lexical scoping



The way that we can access variables depends on whrer the scope is placed, so where it is written in the code.

In this case, none of these two scopes is written inside of one another.



They're both **child scopes** of the first function.



We could even say that they are sibling scopes.

And so **by the rules of lexical scoping,** they cannot have access to each others varibles,

simply because **one is not written inside the other one**.



We can also say that the scope chain only works upwards, not sideways.



## The difference between the scope chain and call stack

![image-20220203195410874](/assets/img/2022-02-03-Scoping-and-scope-in-JS/image-20220203195410874.png)





## Summary

- scoping asks the question "where do variables live?" or "**Where can we access a certain variable, and where not**?"
- There are 3 types of scope in JavaScript: the **global scope**, **scopes defined by functions**, and **scopes defined by blocks**;
- Only `let` and `const` variables are **block-scoped**. Variables declared with `var` end up in the closest function scope;
- In JavaScript, we have **lexical scoping**, so the rules of where we can access variables are based on exactly **where in the code functions and blocks are written**;
- Every scope always has access to all the variables from all its **outer scopes**. This is **the scope chain.**
- When a variable is not in the current scope, the engine **looks up** in the scope chain until it finds the variable it's looking for. This is called **variable lookup**;

- The scope chain is a **one-way street**: a scope will never, ever have access to the variables of an inner scope;
- The scope chain in a certain scope is equal to adding together all the variable environments of the all parent scopes;(but not siblings)
- The **scope chain has nothing to do with the order in which functions were called**. It does not affect the scope chain at all

