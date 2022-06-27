---
title: "[오늘의 배움] 디스트럭처링 할당"
excerpt: "디스트럭처링 할당에 대해 알아보자"

categories:
  - Javascript
  - 오늘의배움
tags:
  - [Javascript, 오늘의배움]

toc: true
toc_sticky: true

date : 2022-06-27
last_modified_at : 2022-06-27
---

오늘은 자바스크립트의 디스트럭처링 할당에 대해서 알아보려고 한다.

개념은 간단한데 여기저기 많이 쓰이는 것 같아 알아두면 좋지 않을까 생각이 된다 😄

# 디스트럭처링 할당이란?

디스트럭처링 할당은 다른말로 구조 분해 할당이라고 한다. 할당할 때 이터러블을 할당하지 않으면 에러가 발생한다.

디스트럭처링을 MDN에서는 이렇게 정의하고 있다.

` 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식입니다.`

이게 무슨 말이냐?! 예제 코드로 이해해보자.

예제 코드 👇

```javascript
let arr = [1,2,3];

// 원래 배열 안에 값을 변수에 저장하려면 아래 처럼 하나하나 저장을 했어야 했다.
let one = arr[0];
let two = arr[1];
let three = arr[2]; 

// 하지만 디스트럭처링 할당을 사용하면 아래와 같다.
let [ one1, two1, three1 ] = arr;

console.log(one, two, three, one1, two1, three1); // result : 1 2 3 1 2 3
```

할당 될 때 위와 같이 순서대로 할당이 되는데 변수의 개수와 우변의 개수가 일치할 필요는 없다.

예제 코드 👇

```javascript
let [a, , c] = [1,2,3];

console.log(a, c); //result : 1 3 자리에 맞게 저장이 된다.
```

> 디스트럭처링 변수 기본값 설정

디스트럭처링 할당을 할 때 기본값을 설정할 수도 있다.

예제 코드로 봐보자.

예제 코드 👇

```javascript
let [a, b, c=3] = [1, 2];

console.log(a, b, c); //result : 1 2 3

let [d, e, f=1] = [1,2,3]; 

console.log(d, e, f); // result : 1 2 3 기본값보다 할당된 값을 우선한다.
```

> 객체 디스트럭처링 할당

디스트럭처링 할당은 객체로도 할당이 가능하다. 객체로 할당하는 경우에도 객체로 할당하지 않으면 에러가 발생한다.

객체를 할당하는 기준은 `프로퍼티 키`이다.

바로 예제 코드로 봐보자.

예제 코드 👇

```javascript
let test = { a:10, b:20 };

let { a, b } = test;

console.log(a, b); // result : 10 20
```

객체를 할당하는데 이렇게도 활용이 가능하다.

예제 코드 👇

```javascript
let str = 'test';

let { length } = str;

console.log(length); // result : 4
```

str는 `String`으로 선언되었기 때문에 `String 래퍼 객체`를 사용할 수 있다.

따라서 String 객체의 length를 할당한 것이다.

오늘은 디스트럭처링 할당에 대해서 알아보았다. 리액트를 공부하다가 이 디스트럭처링 할당에 대해서 나왔는데

처음엔 이게 뭐지 하고 어려웠는데 공부해보니 꽤 간단한 개념이였다. 오늘도 화이팅 해보자 !! 🔥

