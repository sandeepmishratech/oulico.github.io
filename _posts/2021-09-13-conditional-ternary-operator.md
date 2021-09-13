---
layout: post
title: "Conditional (Ternary) Operator"
date: 2021-09-13 18:22:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript conditional-operator
---





In addition to the regular if/else statement and the switch statement, there's one another way to write  conditionals. That's the **conditional operator**.



## How to write the conditional operator



The conditional operator allows us to write something similar to an if/else statement but all in one line.





**Example:**

```js
const age = 23;
age >= 18 ? console.log(`I like to drink wine`) : console.log(`I like to drink water`);
```





⚠︎ After `?` you can write a **if** block and after `:` you should write the **else** block (it's <u>mandatory</u>) 



---



## Distinctive feature of the conditional operator



As it is an operator, it is an `expression` which creates a value. That is, we can assign that value to a variable.

With this we can make `the ternary operator` 

> Ternary means 'composed of tree parts'



#### Example:

`const age = 23;` 

`age >= 18 ? 'wine' : 'water';` // this creates value.(value : 'wine')

`const drink =` // assign the value above into this directly.

```js
const age = 23;
const drink = age >= 18 ? 'wine' : 'water';
console.log(drink);
```



#### Result: 

![image-20210913180526547](/assets/img/2021-09-13-conditional-ternary-operator/image-20210913180526547.png)



if we do this in regular if/else statement, that will be like this:

```js
const age = 23;
let drink;
if (age >= 18) {
  drink = "wine";
} else {
  drink = "water";
}
console.log(drink);
```



---



## Furthermore - with a template literal



Unlike a normal if/else statement, you can **insert the conditional operator** in a `template literal`, because it is `expression`.



#### Example:

```js
const age = 23;
console.log(`I like to drink ${age >= 18 ? 'wine' : 'water'}`);
```



This is Actually Awesome!



