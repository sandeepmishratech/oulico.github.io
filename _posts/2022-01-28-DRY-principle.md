---
layout: post
title: "DRY principle"
date: 2022-01-28 17:36:50 +0300
categories: Basic_attitude
tags: DRY refactoring
---

# DRY and Refactoring



DRY means **Don't repeat yourself**



## Why DRY 

-  to avoid to change the same code in multiple times when we want to change some functionality
- make it easy to read



At the beginning of your coding, you can duplicate some codes because the fact that the code works actually matters at that moment.

But then, as we move on into project, we have to do `refactoring`.

`Refactoring` means to **restructure** the code but without changing how it works.



## How to do Refactoring

1. Identify duplicated codes

2. Simplify it 

   by:

   - using `Conditional (ternary) operator`
   - Specifying a function as seperate function
   - Etc.



## Examples

Before

```js
'use strict';

const modal = document.querySelector('.modal');
const overlay = document.querySelector(`.overlay`);
const btnCloseModal = document.querySelector(`.close-modal`);
const btnsOpenModal = document.querySelectorAll(`.show-modal`);

console.log(btnsOpenModal);

for (let i = 0; i < btnsOpenModal.length; i++)
  btnsOpenModal[i].addEventListener(`click`, function () {
    console.log(`BtnsClicked`);
    modal.classList.remove(`hidden`);
    overlay.classList.remove(`hidden`);
  });



btnCloseModal.addEventListener(`click`, function () {
  modal.classList.add(`hidden`);
  overlay.classList.add(`hidden`);
});



```





After

```js
'use strict';

const modal = document.querySelector('.modal');
const overlay = document.querySelector(`.overlay`);
const btnCloseModal = document.querySelector(`.close-modal`);
const btnsOpenModal = document.querySelectorAll(`.show-modal`);

const openModal = function () {
  modal.classList.remove(`hidden`);
  overlay.classList.remove(`hidden`);
}; // made a function

for (let i = 0; i < btnsOpenModal.length; i++)
  btnsOpenModal[i].addEventListener(`click`, openModal);

const closeModal = function () {
  modal.classList.add(`hidden`);
  overlay.classList.add(`hidden`);
}; // made a function

btnCloseModal.addEventListener(`click`, closeModal);
overlay.addEventListener(`click`, closeModal);

```

