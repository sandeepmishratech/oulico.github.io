---

layout: post
title: "Boolean logic AND, OR, NOT in JavaScript"
date: 2021-09-06 12:31:20 +0200
categories: Notes-JavaScript
tags: Notes JavaScript boolean

---



Boolean logic is a branch of computer science, which uses true and false values to solve complex logical problems.



To understand the Boolean, let's take a look into logical operators first.



## AND, OR, NOT - Logical Operators



### A AND B

| **AND**      | A: TRUE | A: FALSE |
| ------------ | ------- | -------- |
| **B: TRUE**  | TRUE    | FALSE    |
| **B: FALSE** | FALSE   | FALSE    |

True when **ALL** are true.



### A OR B

| AND          | A: TRUE | A: FALSE |
| ------------ | ------- | -------- |
| **B: TRUE**  | TRUE    | TRUE     |
| **B: FALSE** | TRUE    | FALSE    |

True when at least **ONE** is true



### NOT A, NOT B



Inverts true/false value.



## &&, ||, !



|      | in JavaScript | Example |
| ---- | ------------- | ------- |
| AND  | &&            | A&&B    |
| OR   | \|\|          | A\|\|B  |
| NOT  | !             | !A      |



---



### Example





##### Boolean variables

whan age = 16,

+ A: Age is greater or equal 20 = false
+ B: Age is lestt than 30 = true



##### Operators

+ !A = true
+ A AND B = false
+ A OR B = true
+ !A AND B = true
+ A OR !B = false



## Truthy and falsy values



False values are values that are not exactly false, but will become false when we try to convert them into a boolean.



In JavaScript, there are only **five** falsy values.



### 5 Falsy Values in JavaScript

+ 0
+ ''(empty strings)
+ Undefined 
+ Null
+ NaN(not a number)



These will be converted to **false** when we attempt to convert them to a boolean.



Examples:

```js
console.log(Boolean(0));
console.log(Boolean(0));
console.log(Boolean('String'));
console.log(Boolean({})); // this is an empty object
console.log(Boolean(''));
```



Results:

![image-20210907184119443](/assets/img/2021-09-06-Boolean-logic/image-20210907184119443.png)

The type coersion will be performed **always** if it is to boolean, When...

+ Using logical operators
+ in a logical context (i.e. if/else statement)



### Examples in if/else statement



#### situation1:

```js
const money = 0;
if(money) {
  console.log("con't spend it all")
} else {
  console.log('You should get a job')
}
```



#### Result:

![image-20210908111959959](/assets/img/2021-09-06-Boolean-logic/image-20210908111959959.png)



It's because `0` is falsy value.





#### Situation2: 

```js
let height = 0;
if(height) {
  console.log('height is defined')
} else {
  console.log('height is UNDEFINED')
}
```



#### Result:

![image-20210908112038775](/assets/img/2021-09-06-Boolean-logic/image-20210908112038775.png)



### Why?

Even though the height is defined as "0", the `0` is falsy value.



