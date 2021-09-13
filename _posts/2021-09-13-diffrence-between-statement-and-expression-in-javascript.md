---

layout: post
title: "Diffrence between 'statement' and 'expression' in JavaScript"
date: 2021-09-13 17290:20 +0200
categories: Notes-JavaScript
tags: Notes JavaScript statement expression

---



Difference between statements and expressions





### Expression 

> A piece of code that produces a value

#### Examples:

`3 + 4` 

`1991`

`true && false && !false`

`string`



### Statement

> A bigger piece of code that is executed and which does not produce a value on itself

#### Examples:

`if/else statement`

`switch statement`

Normaly whenever something ends with a semicolon, that's a statement.





### Why is it important to know?

JavaScript expects statements and expressions in **different places.**

For example, in a `template literal`, we can only insert `expressions`, but not `statements`



