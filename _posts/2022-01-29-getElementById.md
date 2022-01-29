---
layout: post
title: "Difference between querySelector and getElementById"
date: 2022-01-29 10:47:00 +0300
categories: Notes-JavaScript
tags: Notes JavaScript 
---







When you want to select `id`, there's an another way to do it instead of using `querySelector`.

That is `getElementById`.

They're actually doing **same thing** but `getElementById` is supposed to be **faster** than the other. (very slightly)



```js
const score0 = document.querySelector(`#score--0`);

const score0 = document.getElementById(`score--0`);

//they're same but the latter is faster than the former.
```

