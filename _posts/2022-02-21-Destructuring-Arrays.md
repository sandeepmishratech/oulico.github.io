---
layout: post
title: "Destructuring Arrays" 
date: 2022-02-21 16:36:50 +0300
categories: Notes-JavaScript
tags: Notes JavaScript Destructuring Arrays
---



What is `destructuring`?

`Destructing array` is an ESX feature and it's basically a way of unpacking values from an array or an object into separate variables.

So in other words, `destructuring` is to break a complex data structure down into a smaller data structure like a variable.





## Destructuring an array:

```js
const arr = [2, 3, 4];
const a = arr[0];
const b = arr[1];
const c = arr[2];

const [x, y, z] = arr;
console.log(x, y, z);
console.log(arr);
```



## to reassign elements of an array

#### 1.

```js
const temp = main;
main = secondary;
secondary = temp; // change the arrays
console.log(main, secondary);
```

#### 2.

```js
[main, secondary] = [secondary, main];
```



## Destructuring inside of a destructuring

```js
const nested = [2, 4, [5, 6]];

const [i, , [j, k]] = nested;
console.log(i, j, k);
```





## Default values

```js
const [p = 1, q = 1, r = 1] = [8, 9]; //default is set to 1.
console.log(p, q, r);
```

