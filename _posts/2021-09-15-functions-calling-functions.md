---
layout: post
title: "Functions calling other functions"
date: 2021-09-15 09:22:50 +0200
categories: Notes-JavaScript
tags: Notes JavaScript function
---



Functions can call other functions. 



### Example:

```js
const cutPieces = function (fruit) {
  return fruit * 4;
};

const fruitProcessor = function (apples, oranges) {
  const applePieces = cutPieces(apples);
  const orangePieces = cutPieces(oranges);
  
  const juice = `Juice with ${applePieces} pieces of apple and ${orangePieces} pieces of orange.`;
  return juice;
};

console.log(fruitProcessor(2, 3));
```

1. `console.log(fruitProcessor(2, 3));` 

2. `const fruitProcessor = function (apples, oranges) {` //the arguments `2` and `3` are replaced withe the parameter `apples` and `oranges` 
3. `const applePieces = cutPieces(apples);` and `const orangePieces = cutPieces(oranges);`// and then here, the argument is assigned to the parameters in the lines in code block. 
4. and then it calls the function, `function(fruit)` 
5. The calculated value will be captured in a variable, `cutPieces` 
6. The returned value of `cutPieces` will be stored in `applePieces` and `orangePieces`.
7. Now, value of the variables `applePieces` and `orangePieces` will be shown in the template literal.

![image-20210915102148180](/assets/img/2021-09-15-functions-calling-functions/image-20210915102148180.png)





## Why is it important?

+ It is very common for one function to call another function
+ To follow the principle, the DRY (Don't repeat yourself)

