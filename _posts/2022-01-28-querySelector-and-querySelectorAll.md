---
layout: post
title: "querySelector and querySelectorAll"
date: 2022-01-28 10:21:50 +0300
categories: Notes-JavaScript
tags: Notes JavaScript querySelector querySelectorAll
---



## Limitation of querySelector

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <link rel="stylesheet" href="style.css" />
    <title>Modal window</title>
  </head>
  <body>
    <button class="show-modal">Show modal 1</button>
    <button class="show-modal">Show modal 2</button>
    <button class="show-modal">Show modal 3</button>

    <div class="modal hidden">
      <button class="close-modal">&times;</button>
      <h1>I'm a modal window 😍</h1>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
        veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
        commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
        velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
        occaecat cupidatat non proident, sunt in culpa qui officia deserunt
        mollit anim id est laborum.
      </p>
    </div>
    <div class="overlay hidden"></div>

    <script src="script.js"></script>
  </body>
</html>

```



```js
'use strict';

const modal = document.querySelector('.modal');
const overlay = document.querySelector(`.overlay`);
const btnCloseModal = document.querySelector(`.close-modal`);
const btnsOpenModal = document.querySelector(`.show-modal`);

console.log(btnsOpenModal);

```



when we use `querySelector` with a selector, which actually matches multiple elements, only the **first one** will get selected.

![image-20220128102156750](/assets/img/2022-01-28-querySelector-and-querySelectorAll/image-20220128102156750.png)



To select multiple elements we use `querySelectorAll`



## NodeList

When you use `querySelectorAll`, you'll see the `NodeList` in the console.

![image-20220128102316245](/assets/img/2022-01-28-querySelector-and-querySelectorAll/image-20220128102316245.png)



It's like an array but technically it's not like an array.

But for now, it works as though it was an array.



If you want to do something with all of these buttons,

You can loop through this NodeList



```js
'use strict';

const modal = document.querySelector('.modal');
const overlay = document.querySelector(`.overlay`);
const btnCloseModal = document.querySelector(`.close-modal`);
const btnsOpenModal = document.querySelectorAll(`.show-modal`);

console.log(btnsOpenModal);

for (let i = 0; i < btnsOpenModal.length; i++)
  console.log(btnsOpenModal[i].textContent);

```





Then, you can see this.

![image-20220128103235514](/assets/img/2022-01-28-querySelector-and-querySelectorAll/image-20220128103235514.png)





