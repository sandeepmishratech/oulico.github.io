---
layout: post
title: "Data Structure in JavaScript pt.2"
date: 2021-09-27 12:22:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript Data_structure object_literal_syntax retrieve_and_modify_data_in_objects
---



Object literal Syntax, explanation of the difference between Objects and Arrays, How to retrieve and modify data in objects.



## Object literal Syntax



```js
const oulicoArray = [
  'Oulico',
  'Lee',
  2037 - 1992,
  'Editor',
  ['James','John','Choo']
]; // it is array

const oulicoObject = {
 	userName: 'Oulico',
  lastName: 'Lee',
  age: 2037 - 1992,
  job: 'Editor',
  friends: ['James', 'John', 'Choo']
}; // This is objects
```





## Difference Between Objects and Arrays

+ Objects : The **order of these values doesn't matter** when we want to retrieve them.
+ Arrays:  The order of values matters because that's how you access these elements.





## How to retreive and modify data in objects

### 1. Dot notation

~~~js
const oulico = {
  firstName: 'JH',
  lastName: 'Lee',
  age: 2037 - 1992,
  job: 'teacher',
  friends: ['Michael', 'Peter', 'Steven']
};

console.log(oulico.lastName);

~~~



![image-20211113144516324](/assets/img/2021-09-27/image-20211113144516324.png)



### 2. Brackets notation.

```js
const oulico = {
  firstName: 'JH',
  lastName: 'Lee',
  age: 2037 - 1992,
  job: 'teacher',
  friends: ['Michael', 'Peter', 'Steven']
};

console.log(oulico['lastName']);
```





### The difference between `Dot notation` and `Brackets notation` 

You can put **any expression**  that you'd like in `Brackets notation`



#### i.e

```js
const nameKey = 'Name';
console.log(oulico['first' + nameKey]);
console.log(oulico['last' + nameKey]); 
```

we could put any expression here, okay.

But it is not going to work with `Dot notation` like this:

```js
console.log(oulico.'last'+ nameKey);
```

#### Result

![image-20211113150153614](/assets/img/2021-09-27/image-20211113150153614.png)





that's the reason why we need

the brackets notation AND dot notation.



### How to choose between Dot notation and Bracket notation

So **when we need to first compute the property name**,

then we have to **use the bracket notation.**



In **any other case**, just use the **dot notation**,

which looks a lot cleaner and it's also easier to use.

