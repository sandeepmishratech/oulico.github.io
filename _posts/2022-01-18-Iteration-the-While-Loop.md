---
layout: post
title: "Iteration: the While Loop"
date: 2022-01-18 16:09:00 +0300
categories: Notes-JavaScript
tags: Notes JavaScript while loop
---





# Iteration: the While Loop



## While Loop



```js
let rep = 1;
while (rep <= 10) {
  console.log(`Lifiting weights repetition ${rep}`);
  rep++;
}
```



You can only specify a **condition**, 

That is, to run `while`, only the condition is necessary.

So, actually you can make an repetition with out the counter like below :



```js
while (dice !== 6) {
  console.log(`You rolled a ${dice}`);
  dice = Math.trunc(Math.random() * 6) + 1;
  if (dice === 6) console.log(`Loop is about to end...`);
}
```



