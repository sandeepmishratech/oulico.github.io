---
layout: post
title: "Data structures: Arrays in JavaScript"
date: 2021-09-15 14:22:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript array data-structure 
---



Array is like a big container into which we can store variables and then later reference them.



## How to create an array

### 1)

```js
const friends = ['Michael', 'Steven', 'Peter'];
console.log(friends);
```

You can create an array with `brackets[]`



### 2)

```js
const years = new Array(1991,1984,2008,2020);
```

Or, you can create an array by writing `new Array()`.



## How to get an element out of an array

```js
const friends = ['Michael', 'Steven', 'Peter'];

console.log(friends[0]);//1st element. We count from 0.
```

Remember we count from `0`! Arrays are **zero-based**.



Or, since you can put an `expression` inside of `brackets`, you can do like this:

```js
const friends = ['Michael', 'Steven', 'Peter'];
console.log(friends.length);//numbers of elements, so it is 3.
console.log(friends[friends.length - 1]); //friends.length - 1 is 2, so it is 'Peter'

```



## What can I do with array?





Array is not primitive value, so you can **mutate the elements.** Even though they were declared with const.

```js
friends[2] = 'Jay'; // you can mutate an element
```



An array can **hold value with different types** at the same time. Because you can put `expressions` inside of brackets 

```js
const oulico = ['Oulico', 'Male', 2021 - 1992];
```



You can also **put variables** in the array, because of the same reason.

```js
const userName = 'Oulico';
const oulico = [userName, 'Male', 2021 - 1992];
```



You can **put arrays inside**

```js
const speakLanguage = ['Korean', 'French', 'English'];
const oulico = ['Oulico', 'Male', 2021 - 1992, speakLanguage];
```



## What CAN'T I do with array?



```js
const friends = ['Michael', 'Steven', 'Peter'];
friends = ['Bob', 'Alice']; // this is illegal
```

**You cannot change the entire of the array**.



``` js
const bodyWeights = [67, 55, 80];
const gainedWeights = [1, 2, 3];

console.log(bodyWeights + gainedWeights); // this doesn't work

console.log(bodyWeights[0] + gainedWeights[0],bodyWeights[1] + gainedWeights[1],bodyWeights[2] + gainedWeights[2],); // you should do this separately.
```



__You cannot operate the entire of the array. The operation should be done with actual values, separately.__

