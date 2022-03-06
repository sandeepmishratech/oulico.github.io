---
layout: post
title: Javascript에서의 Express.js Middleware
date: 2022-03-04 18:00:50 +0900
categories: 번역
tags: Notes JavaScript   
---

# Javascript에서의 Express.js Middleware

[원문](https://afteracademy.com/blog/expressjs-middleware-in-javascript)



## middleware란?

middleware는 request와 상호작용을 하고 코드 안의 오브젝트에 응답하게 하기 위해 사용됩니다. 이름을 보면 알 수 있듯이, 중간에서 어플리케이션에게 서비스를 제공하죠. 그래도 뭐의 중간에 있냐고요? 음, 그림으로 한번 보시죠.



![image-20220304181212069](/assets/img/2022-03-04-Javascript%E1%84%8B%E1%85%A6%E1%84%89%E1%85%A5%E1%84%8B%E1%85%B4-Express.js-Middleware/image-20220304181212069.png)



middleware는 request 들을 바꿀 수 있고, 오브젝트에 리스폰스할 수 있으며, 리스폰스 사이클을 멈추게 할 수도 있습니다. 쉽게 생각해서 서버에 리퀘스트가 들어오면 작동되는 함수들의 집합을 middleware라고 보시면 됩니다.



## 왜 middleware를 쓰나요?

대부분의 사이트에서 당신이 브라우저와 상호작용할 때면 브라우저가 웹 서버에 정보를 요청합니다. 그러면 웹서버는 브라우저에게 리스폰스를 보내서 브라우저가 이를 변환하여 텍스트, 이미지, 비디오 등으로 보여주게 됩니다.



웹서버가 리퀘스트를 받으면, Express(node.js를 위한 웹 애플리케이션 서버 프레임워크)는 당신에게 리퀘스트 오브젝트를 주고, 이를 통해 당신은 IP 주소, 브라우저 언어, 패스된 파라미터등 유저 디테일을 볼 수. 있게 됩니다. 또한 Express는 Response 오브젝트에 액세스할 수 있게 됩니다. 이걸 보통 줄여서 `req` 와 `res` 라고 씁니다.



예를 들어보죠. 유저가 당신의 사이트에 방문해서 증명서를 가지고 로그인 했다고 칩시다. 이제 `request` 오브젝트는 당신의 웹서버로 보내졌어요. 당신은 유저 본인확인을 하고 유저가 로그인한 데이터베이스, 로그인한 시간, 사용한 디바이스 그리고 IP를 브라우저에게 response 오브젝트를 보내기 전에 로그로 남기게 될 겁니다. 게다가, 유저가 마지막으로 열람한 웹사이트의 페이지를 찾기 위해서 데이터베이스를 체크해야 할 것이고 그리고 request 오브젝트를 수정해서 유저가 거기에서부터 이어서 이용할 수 있게 해야겠죠. 이걸 어떻게 하냐구요? Middleware 펑션을 쓰는 겁니다!



Middleware 펑션은 `req` 와 `res` 오브젝트를 수정하기에 안성맞춤인 장소입니다. 예를 들어서, 유저가 로그인 하면 당신은 유저를 데이터베이스에서 확인하겠죠 그리고 그의 디테일들을 `res.user` 에 업데이트할 겁니다.



> Middleware는 앱의 request->response 사이클에서 당신에게 `req` 와 `res` 오브젝트에 접근할 수 있게 해줍니다.



Middleware 펑션은 다음과 같은 작업을 수행할 수 있습니다:

- 코드 실행
- request와 response 오브젝트를 수정하기
- Request-response 사이클을 끝내기
- `next()` 를 써서 다른 middleware를 호출하기



## `next()` 는 뭔데요?



앞서 말씀드린 것처럼 middleware는 request가 서버에 보내셨을 때의 펑션의 집합이라고 볼 수 있습니다. 그럼, 펑션의 집합이라고 했으니까, 이 펑션들이 실행되는 순서는 어떻게 될까요? 그리고 어떻게 실행 플로우가 유지될까요? 먼저, 실행 순서는 펑션의 로딩 순서에 의해서 결정됩니다. 기본적인 코드에서, 우리는 `app.get()` 를 통해서 펑션들을 로드할 겁니다. 다음의 예를 보시죠.



```js
app.get('/', authenticate, log_data, update_req);
```



이제 middleware 펑션의 순서는 정해졌습니다. -> `authenticate()`, `log_data()`, 그리고 그다음에 `update_req` 입니다.



하지만 어떻게 실행 플로우가 한 middleware에서 다른 middleware로 이어질까요? 네, 이제 `next()` 펑션이 등장할 차례입니다. 



Middleware 펑션은 흔히 다음의 세 arguments를 받습니다: `req`,`res`,`next`. `next`를 쓰면 현재 펑션 이후에 실행될 다음 펑션입니다.



![image-20220304200049963](/assets/img/2022-03-04-Javascript%E1%84%8B%E1%85%A6%E1%84%89%E1%85%A5%E1%84%8B%E1%85%B4-Express.js-Middleware/image-20220304200049963.png)





만약 현재 middleware 펑션이 request-response 사이클을 끝내지 않는다면, 이 펑션은다음 middleware 펑션에게 조작권을 전해주기 위해서  `next()` 펑션을 호출할 것입니다. 아니면, request는 미결인 상태로 남게 되겠죠.



예를 들자면, 위의 예시에서, 펑션의 순서는 `authenticate()` 이후에 `log_data ()`, 그러고나서 `update_req`입니다. middleware를 위한 코드는 이런 식으로 보이게 되겠죠:



```js
const authenticate = function (req, res, next) {
  // code to authenticate user
  next();
}
const log_data = function(req, res, next) {
  // code to lof signin data in database
  next();
}
const update_req = function(req, res, next) {
  // code to update req object
}
```



next 펑션은 다르게 이름 붙여도 됩니다만 혼동을 피하기 위해서 컨벤션으로 다들 이렇게 씁니다. 



중요: `next()`를 마지막 펑션에서 쓰는 건 해도 되고 안해도 됩니다. 그리고 써봐야 request-response 사이클의 가장 마지막 펑션이니 결국 아무 것도 안할 것입니다.



항상 `app.get()`의 arguments로 펑션을 로드하는 건 아닙니다. `app.use()`, `route.use()` 등도 씁니다.



## middleware 코딩하기

다양한 방법으로 middleware를 코딩할 수 있습니다. 만약 원하면 서드파티 middleware 펑션을 사용할 수도 있죠. 제일 먼저, middleware펑션을 로드해야 합니다. 두가지의 기본적인 방식이 있습니다:

- 위에서 본 것 처럼`app.get()`의 파라미터로서 로드하기
- `app.use()`를 써서 로드하기. 관습적으로 이렇게 하는데다, 훨씬 좋은 방식입니다.



`app.get()`는 사용된 HTTP 메소드가 `GET`일때만 호출됩니다. 반면에 `app.use()`를 사용해 펑션을 로딩하면, 애플리케이션에  request가 올때마다 항상 호출이 될 겁니다.(HTTP 메소드가 뭐건 간에 말이죠) 그러므로, `app.use()`가 middleware를 로드할 때 더 좋은 방식으로 여겨지는 겁니다.



그러면, 말씀드린 두번째 방법으로 코드를 업데이트한다면 이렇게 보일 겁니다.

```js
const authenticate = function (req, res, next) {
  // code to authenticate user
  next();
}
app.use(authenticate);

const log_data = function(req, res, next) {
  // code to lof signin data in database
  next();
}
app.use(log_data);

const update_req = function(req, res, next) {
  // code to update req object
}
app.use(update_req);
app.get('/');
```



여기보면, 펑션의 순서가 펑션이 로딩되는 순서대로 결정이 되었습니다. 즉, 처음에는 `authenticate` , 그리고 `log_data`, 마지막으로 `update_req` 순서대로 말이죠. 만약 당신이 내장 middleware 혹은 서드파티 middleware를 쓴다면, 펑션을 임포트하고 `app.use()`를 써서 로드하면 됩니다. 흔히 쓰이는 내장 middleware는 `cookie-parser`인데요, 쿠키 헤더를 파싱하고 `req.cookie`를 populate 할 때 씁니다. 당신의 코드에 간단하게 삽입할 수 있습니다. 이렇게요:



```js
const cookie_parser = require('cookie-parser');
app.use(cookie_parser());
```



## 마치며

middleware는 당신의 코드를 조직하여 request-response 사이클 안에서 작동되도록 하는 데 정말 좋은 도구입니다. 기본적으로 애플리케이션의 `req`와 `res` 오브젝트에 접근할 수 있는 펑션입니다. request가 애플리케이션에 의해 다뤄지지 전 디벨로퍼가 행하는 일련의 작업들이라고 생각해도 됩니다. 여러분은 여러분 고유의 middleware를 코딩하실 수도 있고 내장 middleware 혹은 서드파티 middleware를 사용할 수 있습니다.

