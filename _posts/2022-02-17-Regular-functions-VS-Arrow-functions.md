---
layout: post
title: "This keyword with Regular functions and Arrow functions"
date: 2022-02-17 14:16:00 +0900
categories: Notes-JavaScript
tags: Notes JavaScript Arrow Function
---



Let's see some pitfalls of the `this` keyword related to regular functions.



## 1. Arrow functions don't get its `this` keyword

```js
const oulico = {
  firstName: 'oulico',
  year: 1991,
  calcAge: function () {
    console.log(this.year)
  },
  
  greet: () => console.log(`Hey ${this.firstName}`), 
};

oulico.greet();
```

As you can see if you use arrow function, 

`this` will be undefined:

![image-20220216143013965](/assets/img/2022-02-16-Regular-functions-VS-Arrow-functions/image-20220216143013965.png)





And even though you're using arrow functions, if you declare `firstName` variable with `var`, as it creates properties on the global object, `this` will point to the global object  and the method `firstName` in `oulico` will not be called but the `var` variable, `firstName`.

```js
var firstName = `Matilda`;

const oulico = {
  firstName: 'oulico',
  year: 1991,
  calcAge: function () {
    console.log(this);
    console.log(2037 - this.year);
  },

  greet: () => console.log(`Hey ${this.firstName}`),
};

oulico.greet();

```



Result:

![image-20220216143536160](/assets/img/2022-02-16-Regular-functions-VS-Arrow-functions/image-20220216143536160.png)





 

In short,

You should **never use an arrow function as a method.**

That's even true if you're not even using the this keyword in a particular method.

Because if you have this rule of never using an arrow function as a method, then **you never have to think about which type of function you should use**.





If you use regular functions:

```js
const oulico = {
  firstName: 'oulico',
  year: 1991,
  calcAge: function () {
    console.log(this.year)
  },
  
  greet: () => console.log(`Hey ${this.firstName}`), 
};

oulico.greet();
```



Result:

![image-20220216144246861](/assets/img/2022-02-16-Regular-functions-VS-Arrow-functions/image-20220216144246861.png)





## 2. Function inside of a method









One final example of a pitfall of this keyword is when we have a function inside of a method.

And that is a pretty common thing to happen.

And so let's now take a look at an example of that. 

```js
const oulico = {
  firstName: 'oulico',
  year: 1991,
  calcAge: function () {//❶
    console.log(2037 - this.year);

    const isMillenial = function () {
      console.log(this.year >= 1981 && this.year <= 1996);//❷
    };
    isMillenial();
  },

  greet: () => {
    console.log(this);
    console.log(`Hey ${this.firstName}`);
  },
};

oulico.greet();
oulico.calcAge();
```



Inside of this function(❶), we are using the this keyword. And the result is:

![image-20220217152847580](/assets/img/2022-02-16-Regular-functions-VS-Arrow-functions/image-20220217152847580.png)



It cannot read properties of undefined (reading 'year')

That is ❷.

`this` keyword is `undefined` .

Why?

Because this is a regular function call. Even though it happens inside of a method.

## How to solve it

#### 1. Use `self` (pre ES6 solution) 

Use an extra variable that we usually call `self` or `that`

```js

const oulico = {
  firstName: 'oulico',
  year: 1991,
  calcAge: function () {
    console.log(2037 - this.year);
    const self = this; //make an extra variable
    const isMillenial = function () {
      console.log(self.year >= 1981 && self.year <= 1996); // and use `self` instead of `this`
    };
    isMillenial();
  },

  greet: () => {
    console.log(this);
    console.log(`Hey ${this.firstName}`);
  },
};

oulico.greet();
oulico.calcAge();
```





#### 2. To use an arrow function

```js
const oulico = {
  firstName: 'oulico',
  year: 1991,
  calcAge: function () {
    console.log(2037 - this.year);
    const isMillenial = () => {
      console.log(this.year >= 1981 && this.year <= 1996);
    };
    isMillenial();
  },

  greet: () => {
    console.log(this);
    console.log(`Hey ${this.firstName}`);
  },
};

oulico.greet();
oulico.calcAge();
```



It works because an `arrow function ` uses the `this` keyword from its parent scope.













					