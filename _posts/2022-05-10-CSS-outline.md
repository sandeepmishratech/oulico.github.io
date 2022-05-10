---
layout: post
title: CSS-outline
date: 2022-05-10 12:16:50 +0900
categories: CSS
tags: CSS hack
---



Css 작성의 console.log, outline! 

## TL;DR

- 작업중인 공간을 표시하기 위해서는 outline을 사용해라.
- `border: 1px solid red` 는 공간을 차지하기 때문에 no



## outline을 써야하는 이유

![border:1px solid red is the console.log for me in css 🤣 - DEV Community](https://dev.to/social_previews/comment/264160.png)



정말 많은 사람들이 CSS를 작성할때 

`border: 1px solid red` 를 사용해 자신이 작업중인 공간을 가시화한다. 

그러나 이보다는 `outline: 1px solid red` 를 쓰는게 더 낫다!

왜냐하면 

**outline 속성은 border와 달리 박스모델의 구성속성이 아니다. 그래서 보더와 달리 아웃라인은 <u>크기를 차지하지 않고</u> 외곽선표시만 된다.**



