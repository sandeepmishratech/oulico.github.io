---
layout: post
title: prettier hack 붙여넣기한 라인이 깨질 때
date: 2022-05-10 18:00:50 +0900
categories: Configures_and_Hacks
tags: Vscode Prettier
---



장문의 글을 vscode에 붙여넣고, 각 줄에 커서를 두고 <p> 태그로 감쌌더니 문장이 마구 깨져버린다면?

## TL;DR

- prettier의 경우, 저장시 형식을 정돈해주는 `formatOnSave` 기능과 `formatOnPaste` 이 기본값으로 설정되어있다.
- `formatOnPaste`가 바로 문단을 깨뜨리는 주범이다. 해당 설정을 false로 바꿔주는 것으로 해결가능하다. 





## 문제 상황

![image-20220510184236056](/assets/img/2022-05-10-prettier-hack-붙여넣기한-라인이-깨질-때/image-20220510184236056.png)

이렇게 여러줄의 문장으로 구성된 여러개의 문단을 복사 붙여넣기 한 뒤,([사용한 텍스트 소스](https://n.news.naver.com/mnews/article/014/0004831242?sid=101))

각 문단을 <p>로 감싸기 위해 각 라인을 option키를 누르고 선택하고 `Emmet: Wrap with Abbreviation` 기능을 사용하려고 하면, 해당 기능을 위한 단축키를 누르자 마자 다음과 같은 문제상황이 발생한다



![image-20220510184504278](/assets/img/2022-05-10-prettier-hack-붙여넣기한-라인이-깨질-때/image-20220510184504278.png)



태그 명을 입력하고 그대로 진행하면, 다음처럼 라인이 죄다 깨져버린다.



![image-20220510184555476](/assets/img/2022-05-10-prettier-hack-붙여넣기한-라인이-깨질-때/image-20220510184555476.png)



## 해결방법



### 1. 먼저 settings.json을 찾는다.



- 맥의 경우: ~/Libarary/Application Support/Code/User/.settings.json
- 윈도우즈의 경우: %AppData%/Roaming/Code/User/settings.json
- 리눅스의 경우: ~/.config/Code/User/settings.json



### 2. 다음과 같은 라인을 추가한다.

```js
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.formatOnPaste": false
}
```



## 3. VSCode를 재실행한다.



![image-20220510185030018](/assets/img/2022-05-10-prettier-hack-붙여넣기한-라인이-깨질-때/image-20220510185030018.png)



태그로 감싼 직후, prettier가 작동하지 않았기 때문에 문제가 생기지 않았다.

여기서 저장을 누르면, formatOnSave 기능이 작동하면서 문제 없이 형식이 정돈된다.



![image-20220510185158577](/assets/img/2022-05-10-prettier-hack-붙여넣기한-라인이-깨질-때/image-20220510185158577.png)





## 참고

[세팅](https://glebbahmutov.com/blog/configure-prettier-in-vscode/#settings)