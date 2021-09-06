---
layout: post
title: "Type Conversion and Coersion"
date: 2021-09-05 17:11:20 +0200
categories: Notes-JavaScript
tags: Notes JavaScript Data-type
---



Type conversion and coersion is this.

> Type conversion : when we convert manually from one type to another.

> Type coersion : when JS converts types automatically.



Let's take a look with some examples.



## Type conversion to number

```js
const inputYear = '1991';
console.log(typeof inputYear);
// this is string.

console.log(typeof Number(inputYear));
// now it's number.

```

Result:

![Screen Shot 2021-09-05 at 11.25.06 AM](/assets/img/2021-09-05-type-conversion-and-coersion/Screen Shot 2021-09-05 at 11.25.06 AM.png)

⚠︎Remember that you need to start with a **capital letter**! (i.e. Number)





## Type conversion to String

```js
const inputYear = 1991;
console.log(typeof inputYear);
// this is number.

console.log(typeof String(inputYear));
// now it's string.


```

Result:

![image-20210905113714819](/assets/img/2021-09-05-type-conversion-and-coersion/image-20210905113714819.png)

⚠︎Remember that you need to start with a **capital letter**! (i.e. Number)



### Type Coersion 

JavaScript convert types automatically in some situation. This it the example.

```js
// type coersion
console.log('I am ' + 23 + " year's old")
```

Result:

![image-20210905114532293](/assets/img/2021-09-05-type-conversion-and-coersion/image-20210905114532293.png)

Even though I didn't convert the data type of `23` from number to strings, it's converted itself and concatenate the strings; `I am`, `23`, and `year's old`.  

It's because the  `plus operator(+)` triggers a coersion to strings here. 

Whenever there's a plus operator between a string and a number, the number will be converted .



**But with a minus operator`(-)`, it's opposite. **

The `minus operator(-)` triggers a coersion to a <u>number.</u>



Okay, let's see the example.

```js
// when you use minus operator
console.log('10'-10-'10');
```

Result: 

![image-20210905120006899](../assets/img/2021-09-05-type-conversion-and-coersion/image-20210905120006899.png)

It's converted to **numbers**!

but, if you use a plus operator,

```js
// when you use plus operator
console.log('10'+10+'10');
```

Result:

![image-20210905120248727](/assets/img/2021-09-05-type-conversion-and-coersion/image-20210905120248727.png)



WHATTTTT



I know right? So interesting.

It's because we use `+` to concatenate strings.

**Only `+` converts the data type to strings.**



| operator | coersion   |
| -------- | ---------- |
| +        | to strings |
| -        | to numbers |
| *        | to numbers |
| /        | to numbers |
| >        | to numbers |



