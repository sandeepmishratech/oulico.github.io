---
layout: post
title: "Behind the scene: Hoisting in Javascript"
date: 2022-02-04 14:00:50 +0300
categories: Notes-JavaScript
tags: Notes JavaScript hoisting Temporal_dead_zone TDZ
---

## Hoisting



Hoisting is a mechanism which makes some types of variables accessible, or usable in the code before they are actually declared in the code.

Many people simply define hoisting by saying that variables are magically lifted or moved to the top of their scope but it is not how it works.

**The code is basically scanned for variable declarations before it is executed.** 

**Then, for each variable that is found in the code, a new property is created in a variable environment object.**

Hoisting doesn't work the same for all variable types.



## Hoisting for function declarations

Function declarations are actually **hoisted** and the initial value in the variable environment is set to the **actual function**

Which means, we can use function declarations before they are actually declared in the code again, because they are stored in the variable environment object, even before the code starts executing.

Function declarations are **block scoped**. 

Keep in mind that it is only true for `strict mode`.



## Hoisting for var variables

Variables declared with `var` also **hoisted**, but hoisting works in a different way here.

Unlike functions, when we try to access a var variable before it's declared in a code, we don't get the declared value but we get **undefined**.

`var` variables are **function scoped**

It is a common source of bugs on JavaScript, and this is one of the main reasons why in modern JavaScript we almost never use `var`.



## Hoisting for let and const variables

`let` and `const` variables **are not hoisted**. (Technically they are actually hoisted but their value is basically set to uninitialized.)

So there is no value to work with at all.

In practice, It is as if hoisting was **not happening at all**.

We say that these variables are placed in a so-called `Temporal Dead Zone` or `TDZ` which makes it so that we can't access the variables between the beginning of the scope and to place where the variables are declared.

As a consequence, if we attempt to use a `let` or `const` variable before it's declared, we get an error.

Also `let` and `const` are **block scoped**.



## Hoisting for function expressions and arrows

It depends if using `var` or `let`/`const`

Because these functions are simply variables. 

So they behave the **exact same way as variables in regards to hoisting**.

That is, a `function expression` or `arrow function` created with **`var`** is **hoisted** to **undefined**.

But if created with `let` or `const`, it's not usable before it's declared in a code because of `Temporal Dead Zone`





![image-20220204162002231](/assets/img/2022-02-04-Behind-the-scene%7C-Hoisting-in-Javascript/image-20220204162002231.png)







## Temporal Dead Zone





```js
const myName = 'oulico';

if (myName === 'oulico') {
  console.log('ouilco is a ${job}');
  const age = 2037 - 1989;
  console.log(age);
  const job = 'singer';
  console.log(x);
}
```



Let's look at the `job` variable. 

It is a `const` so it's scoped only to this `if block` and it's going to be accessible starting from the line where it's defined.

It's because there is the `Temporal Dead Zone` for the job variable.

![Screen Shot 2022-02-04 at 5.29.07 PM](/assets/img/2022-02-04-Behind-the-scene%7C-Hoisting-in-Javascript/Screen%20Shot%202022-02-04%20at%205.29.07%20PM.png)



Even though it is the region of the scope in which the variable is defined, the variable cannot be used in any way.

So **Temporarily** variable is **dead** in this **zone** 

If you try to access the variable while in the TDZ like we actually do in the first line of this `if block`,(`console.log('Jonas is a ${job}');`)

Then, we get a reference error.



And it has different kind of error message:

when TDZ:

![image-20220204175938607](../assets/img/2022-02-04-Behind-the-scene%7C-Hoisting-in-Javascript/image-20220204175938607.png)



When the variable is not defined:



![image-20220205094257386](../assets/img/2022-02-04-Behind-the-scene%7C-Hoisting-in-Javascript/image-20220205094257386.png)





## Why TDZ exists 

The main reason that the TDZ was introduced in ES6 is that **it makes it easier to avoid and catch errors.**

Because using a variable that is set to undefined before it's actually declared can cause serious bugs which might be hard to find.

Accessing variables before declaration is bad practice and should be avoided. And the best way is by simply getting an error when we attempt to do so. And that's exactly what a Temporal Dead Zone does.

A second reason is **to make `const` variables actually work the way they are supposed to.** 

`const` should never be reassigned. And so it's only assigned when execution actually reaches the declaration. And that makes it impossible to use the variable before.



## Why hoisting exists?



The creator of JavaScript basically implemented hoisting so that we can use function declarations before we use them.

Because this is essential for some programming techniques, such as `mutual recursion`

Some people also think that it makes code a lot more readable.



### Why does it works for var declarations 

Because that was the only way hoisting could be implemented at the time. 

So the hoisting of var variables is basically just a **byproduct of hoisting function**.

It seemed a good idea to simply set variables to `undefined`, which in hindsight is not really that great.

But we need to remember that JavaScript was never intended to become the huge programming laguage that it is today.

Also, we can't remove this feature from the language now.

And so we just use `let` and `const` to work around this.



