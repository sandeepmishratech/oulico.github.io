---
layout: post
title: Transition, transform, animation
date: 2022-05-26 19:00:50 +0900
categories: HTML
tags: HTML  
---



왠지 헷갈리는 transition, transform, animation 모아보기

# Transition, transform, animation

## TL;DR

- transition은 css 속성의 변화에 지연시간을, 변화 시간을 줘서 애니메이션으로 만드는 것이다

- transform은 다른 속성의 하위 속성이 아니라, css 속성중 하나로 모양의 변형을 하게 해주는 속성이다. 

- animation은 keyframe에 변화 속성을 단계에 따라서 나누어서 준 뒤에 이를 호출해서 복합적인 애니메이션을 가능케 한다.

  

## transform 

- 선택요소의 크기, 회전, 이동, 기울임 등 변형을 하기 위한 속성.

- 2D, 3D 지원됨





1. rotateY(각도deg) - Y축회전

2. rotateX(각도deg) - X축회전

3. translateX(거리) - X축이동

   - 단위: px, %

   - 현재 위치로부터 이동
   - 기준점은 요소의 왼쪽
   - % 단위를 쓸 경우 기준은 요소의 width
   - 이동방향: + 는 오른쪽, - 는 왼쪽

4. translateY(거리) - Y축이동

   - 단위: px, %
   - 현재 위치로부터 이동
   - 기준점은 요소의 윗선
   - % 단위를 쓸 경우 기준은 요소의 height
   - 이동방향: +는 아랫쪽, - 는 윗쪽

5. translate(X축거리,Y축거리) - X,Y축 이동

   - 단위: px, %
   - 현재 위치로부터 이동
   - 기준점은 요소의 왼쪽선과 윗선
   - % 단위를 쓸 경우 기준은 요소의 width와 height
   - 이동방향: + 는 오른쪽/아랫쪽, - 는 왼쪽/윗쪽

6. rotate(각도deg) - 원형회전

   - 각도의 숫자가 양수면 시계방향으로 회전

   - 기본회전축은 정중앙

     (transform-origin: 가로값 세로값; 으로 변경가능)

7. skew - x, y축 기울임

   - transform: skewY(45deg);

     (y축 방향으로 잡아당겨서 45도가 되게 한다.)

8. scale(x축배수, y축배수)

   - 값을 하나만 쓰면 양방향에 같은 값으로 적용됨
   - 배수가 1보다 크면 확대, 작으면 축소
   - scaleX(배수), scaleY(배수) - x, y축별
   - 값이 0이면 요소가 사라짐

9. 복합적용하기

   - 트랜스폼은 단 한번만 쓸 수 있다. 대신 속성을 여러개 쓸 수 있다.

     transform: 속성1 속성2 속성3 ...;

10. 앞뒤로 있는 이미지 뒤집기

    - 셋팅: 한박스 안에 이미지가 2장 있을때, 이 이미지들을 겹쳐지게 하려면 이미지 position: absolute;로 준다.
    - 앱솔루트끼리는 서로 겹쳐진다
    - 순서는 나중에 그려진 요소가 위에 온다

```css
      /* 1. 앞면 처음상태(돌아옴) */
      /* Y축 0도로 돌아옴 - 0.4초 기다림 */
#trans10 img:last-child {
  transform: rotateY(0deg);
  transition: transform 0.4s ease-out 0.4s;
}

      /* 2. 앞면 오버상태 */
      /* Y축 90도회전 - 회전후 안보임*/
#trans10:hover img:last-child {
  transform: rotateY(90deg);
  transition: transform 0.4s ease-in;
}

      /* 3. 뒷면 처음상태(돌아옴) */
      /* 처음에 이미 Y축 90도 회전상태 - 안보임 */
#trans10 img:first-child {
  transform: rotateY(90deg);
  transition: transform 0.4s ease-in;
}

      /* 4. 뒷면 오버상태 */
      /* Y축 0도로 회전
         - 보거미 0.4초 돌동안 기다렸가 0.4초돌기 */
#trans10:hover img:first-child {
  transform: rotateY(0deg);
  transition: transform 0.4s ease-out 0.4s;
  /* ease-out 정속도를 받아 끝날 때 느려진다 */
}
```





## transition : 속시이지

**transition: 속성 시간 이징 지속시간**


    1. 속성명 - 애니메이션 지정 대상속성

       - height값을 쓰면 height에 대한 애니메이션만 나온다

           - all 이라고 쓰면 모든 CSS변화과정이
               애니메이션으로 연출됨!(또는 all생략!)

    2. 시간 - 애니메이션 동작시간

       - 초단위로 표시, 뒤에 s라는 단위씀

       - 초단위 중 0.5s 이런식의 0.소수일
         경우 앞의 0을 생략하여 .5s 이런식으로
         사용하기도함!

    3. 이징(easing) - 애니메이션 가속도설정

       - ease-in: 시작할 때 천천히
       - ease-out: 끝날 때 천천히
       - ease-in-out: 시작과 끝에 천천히
       - linear: 등속도
       - ease: 약한정도로 시작과 끝에 천천히(기본값)

       - 그 밖에 다양한 베지어곡선 가속도가 있다!

    4. 지연시간 - 애니메이션 시작전 대기시간
               - 초단위(뒤에 s)

## animation : 이시이지반방마



**animation: 이름 시간 이징 지속시간 반복 방향 마지막상태**



1) 이름(animation-name) : keyframe 이름
2) 시간(animation-duration) : 애니메이션 동작시간(초단위:s)
3) 이징(animation-timing-function) : easing 가속도
4) 지연(animation-delay) : 애니메이션 시작지연시간(초단위:s)
5) 반복여부(animation-iteration-count) : 애니메이션 반복횟수
    - 기본값 1, 숫자를 쓰면 반복횟수
    - 영원히는 infinite(인피니트)
6) 방향(animation-direction) : 시작->끝
    - 대체경로 설정하기 : alternate : 시작->끝,끝->시작
    - 대체경로는 반복횟수가 2이상 또는 infinite 이여야함
7) 마지막상태(animation-fill-mode) : 애니메이션이 끝났을때
    - 처음상태로 돌아가는 것이 기본!
    - 마지막 상태를 유지하고 싶을때 forwards(앞쪽에...즉,애니끝장면)

```css
#arm2 {
  animation: shakeAni 0.4s ease-in-out 7.6s infinite alternate;
}

@keyframes shakeAni {
  from {
    transform: rotate(-160deg);
  }
  to {
    transform: rotate(-140deg);
  }
}
//animation은 keyframes와 항상 함께 쓰인다.
```







