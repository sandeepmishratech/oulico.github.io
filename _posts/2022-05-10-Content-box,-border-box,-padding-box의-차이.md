---
layout: post
title: Content box과 border box과 padding box의 차이
date: 2022-05-10 10:00:50 +0900
categories: HTML_심화
tags: HTML  
---

Content box, border box, padding box의 차이는?

## TL;DR

- 박스 영역을 세가지로 나뉘어진다.
- Content box 는 박스 안의 내용물 영역
- Padding box는 내용물 바깥 패딩까지 포함한 영역
- Border box는 패딩 바깥 보더까지 다 포함한 영역 



## 영역의 차이



html과 css로 웹페이지를 만들다 보면 어느순간 내 생각과는 다른 크기로 박스의 폭과 높이가 정해져 있음을 깨닫게 된다. 

이는 보더 사이즈와 패딩 사이즈가 더해지면서 박스크기가 달라지는 것인데, 그럴때면 `box-sizing: border-box` 를 사용해서 이를 해결하곤 한다. 



border-box가 무엇인지에 대해서 좀 더 자세히 알아보자



`background-clip` 옵션으로 각 박스 영역의 차이를 알아볼 수 있다. 



## Default (Border-box)

![image-20220510102400349](/assets/img/2022-05-10-Content-box,-border-box,-padding-box%E1%84%8B%E1%85%B4-%E1%84%8E%E1%85%A1%E1%84%8B%E1%85%B5/image-20220510102400349.png)



> 회색 영역이 보더 박스다.





## Padding-box

![](/assets/img/2022-05-10-Content-box,-border-box,-padding-box%E1%84%8B%E1%85%B4-%E1%84%8E%E1%85%A1%E1%84%8B%E1%85%B5/image-20220510102255389.png)



## Content-box

![image-20220510102529397](/assets/img/2022-05-10-Content-box,-border-box,-padding-box%E1%84%8B%E1%85%B4-%E1%84%8E%E1%85%A1%E1%84%8B%E1%85%B5/image-20220510102529397.png)





## 참고 

[box-sizing: border-box](https://www.codingfactory.net/10630)

