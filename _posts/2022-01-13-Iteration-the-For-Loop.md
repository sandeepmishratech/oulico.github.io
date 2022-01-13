~~~
layout: post
title: "Iteration: the For Loop"
date: 2022-01-13 17:36:50 +0300
categories: Notes-JavaScript
tags: Notes JavaScript Data_structure Loop iteration for 
~~~



# Iteration: the For Loop



Loop allows us to automate tasks.

Let's learn 'The for loop'



## 1. Basic

Loop has 3 parts;





1. Initial value of a counter

2. Logical Condition  (`For loop` keeps running while condition is TRUE.)

3. Increasing amount of counter

![Screen Shot 2022-01-13 at 5.28.35 PM](/assets/img/2022-01-13-Iteration-the-For-Loop/Screen Shot 2022-01-13 at 5.28.35 PM.png)



### Examples



```js
const oulico = [
  "Oulico",
  "Lee",
  2037 - 1991,
  "singer",
  ["Michael", "Peter", "Steven"],
];

const types = [];

for (let i = 0; i < oulico.length; i++) {
  // reading from oulico array
  console.log(oulico[i], typeof oulico[i]);

  //filling types array
  //types[i] = typeof oulico[i];
  types.push(typeof oulico[i]);
}
```



 ⚠︎Check the [Methods in JavaScript](/_posts/2021-09-27-methods-in-js.md) if you want to know about `.push`



```js
console.log(types);

const years = [1991, 2007, 1969, 2020];
const ages = [];

for (let i = 0; i < years.length; i++) {
  ages.push(2037 - years[i]);
}

console.log(ages);
```







## 2. Continue and break

### Continue

```js
console.log("--- ONLY STRINGS---");
for (let i = 0; i < oulico.length; i++) {
  if (typeof oulico[i] !== "string") continue;//<<--this part

  console.log(oulico[i], typeof oulico[i]);
}
```





### Break

```js
console.log("--- BREAK WITH NUMBER---");
for (let i = 0; i < oulico.length; i++) {
  if (typeof oulico[i] === "string") break;//<<--this part

  console.log(oulico[i], typeof oulico[i]);
}

```





### result

![image-20220113180540176](/assets/img/2022-01-13-Iteration-the-For-Loop/image-20220113180540176.png)

