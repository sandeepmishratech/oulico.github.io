---
layout: post
title: "Diffrence between '==' and '==='in JavaScript"
date: 2021-09-06 10:50:20 +0200
categories: Notes-JavaScript
tags: Notes JavaScript operator
---





There are two equality operators in JavaScript, `loose equality operator(==)` and `strict equality operator(===)`.





| Operator | Name                       |
| -------- | -------------------------- |
| `===`    | Strict equality operator   |
| `==`     | Loose equality operator    |
| `!==`    | Strict inequality operator |
| `!=`     | Loose inequality operator  |





The difference between `Strict equality operator (===)` and `Loose equality operator (==)` is **Type coersion**.



+ `===` doen't perform type coersion,

+ `==` perform type coersion.



![image-20210906105953232](/assets/img/2021-09-06-diffrence between '==' and '===' in JavaScript/image-20210906105953232.png)





>  ⚠︎ For clean code, **Avoid the loose equality operator** as much as you can. when you need the type conversion, it's better to convert the value manually before conversion.



> ⚠︎ Don't confuse the `assignment(=)` with the `copariaon operator(===, ==)`