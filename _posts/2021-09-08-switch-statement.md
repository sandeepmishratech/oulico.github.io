---
layout: post
title: "Switch Statement in JavaScript"
date: 2021-09-08 12:31:20 +0200
categories: Notes-JavaScript
tags: Notes JavaScript switch_statement
---



**Switch statement** is alternative way of writing a complicated `if/else statement` when we want to compare one value to multiple different options.



Example:

```js
let day = "monday";

switch (day) {
  case "monday":
    console.log("study coding");
    console.log("post an article on the blog");
    break; // JavaScript execute everyline after ":", and you have to write a "break" code to exit from excuting lines
  case "tuesday":
    console.log("Lunch with Beth");
    console.log("Go to the gym");
    break;
  case "wednesday":
  case "thursday":
    console.log("study french");
    break;
  case "friday":
    console.log("Work");
    break;
  case "saturday":
  case "sunday":
    console.log("Enjoy the weekend");
    break;
  default:
    console.log("Invalide day");//you can set a default and it will be executed when the input is not valide.
}
```



