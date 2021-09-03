---
layout: post
title: "Notes: JavaScript Basic"
date: 2021-09-01 16:28:07 +0200
categories: Notes-JavaScript
tags: Notes, JavaScript
---



Let's learn how to code JS! 

Very very basic rules.





## Basic

### How to link JavaScript to HTML?

1. insert `<script>` tag inside of the `<head>` tags or inside of the `<body>` tags. And code JavaScript inside the `<script>` tags.
2. make a `script.js` file and link it by add a line`<script src="script.js"</script>` in HTML



### What is 'variable' and 'value' ?

Variable is a container of data.

Value is a piece of data.



### Convention of naming of variables

+ `inCamelCase` - variable name should be written in camel case, `justLikeThis`.

+ `PI` - if the variable is a constant, you can write it in all uppercase. (i.e let PI = 3.1415;)

+ Examples of **Illegal variable names**

  - `3years` - You cannot start with a number

  - `m&M` - Variable name contains only `_`, `number`, `letters`, `$`

  - `new` - You can't use javascript reserved keywords

  - `Person` - it's not illegal but it doesn't match with the convention.

    

## Cleaner codes?

The more **descriptive** the cleaner.

```js
let myFirstJob = "Programmer";
let myCurrentJob = "Teacher";
//these are better than...

let job1 = 'Programmer';
let job2 = 'teacher';
//this.
```



