---
layout: post
title: "if / else statements in JavaScript"
date: 2021-09-03 17:35:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript if-else
---



### 1. if control structure

To take decision with code, you can use `if`statements.



```js
let userName = `Jason`;
let age = 19;
const isOldEnough = age >= 18;

if (isOldEnough) {
  console.log(`${userName} can start driving license`);
}
```

It works!

> `else` block is **optional**. When there's no `else` block, JavaScript will simply move on when the condition is false.

### 2. if/else control structure

You can add `else` statement to make it multiple.

 

```js
let userName = `Jason`;
let age = 15;
const isOldEnough = age >= 18;

if (isOldEnough) {
  console.log(`${userName} can start driving license`);
} else {
  console.log(
    `${userName} should wait ${18 - age} years to start driving license!`
  );
}
```



If the value of `isOldEnough` is `true`, JavaScript will execute the code inside of `if` block,

else, it'll execute the code inside of `else` block.





