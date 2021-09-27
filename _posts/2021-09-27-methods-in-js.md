---
layout: post
title: "Methods in JavaScript"
date: 2021-09-27 12:22:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript method 
---

# Built-in functions which apply directly on arrays. 



## push

Add an element to the end of array



```js
const friends = ['Michael', 'Steven', 'Peter'];
friends.push('Jay');
console.log(friends);
```











## unshift

Add an element to the beginning of the array.

```js
friends.unshift('John');
console.log(friends);
```





## pop

Remove the last element

```js
friends.pop();// Remove last element

```



## shift

Remove the first element

```js
friends.unshift();// Remove first element
```



 ## indexOf

A method tells in which position a certain element is in the array.



```js
console.log(friends.indexOf('Steven'));// is 1
console.lof(friends.indexOf('Bob')); // if there's no such element, it says "-1"
```





## includes

this return `true` if the element is included. 

```js
console.log(friends.includes('Steven')); // is "true"
console.log(friends.includes('Bob')); // is "false"
```





⚠︎Since this is testing with strict equality, __it doesn't do type coercion__.

```js
friends.push(23);
console.log(friends.includes(23));
```





 

You can use the include method to write conditionals.



```js
if (friends.includes('Steven')) {
  console.log('You have a friend called Steven');
}
```



