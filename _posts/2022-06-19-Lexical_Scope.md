---
title: "[오늘의 배움] Lexical Scope"
excerpt: "Lexical Scope에 대해 알아보자"

categories:
  - Javascript
tags:
  - [오늘의배움, Javascript]

toc: true
toc_sticky: true

date : 2022-06-19
last_modified_at : 2022-06-19
---

오늘은 Lexical Scope(렉시컬 스코프)라는 것을 공부해보자 ✍

# 렉시컬 스코프란?

__함수를 어디서 정의__ 했는지에 따라 상위 스코프를 결정하는 것이다.

같은 말로는 Static Scope(정적스코프)라고도 한다.

```
📌 참고 : 함수를 어디서 호출했는지에 따라 함수의 상위스코프를 결정하는 것은 동적 스코프라고 한다.

자바스크립트는 렉시컬 스코프를 따르기 때문에 여기서는 렉시컬 스코프를 설명하겠다 !!
```

코드로 다시 한 번 봐보자

예제 코드 👇

```javascript
var val = 1;

function test(){
    var val = 10;
    test2(); // 출력 1
}

function test2(){
    console.log(val); // 출력 2
}
```

이렇게 코드를 짰을 때 `출력 1`과 `출력 2`의 값은 어떻게 나올까?

나는 처음 당연히 `출력 1` 에선 10이라는 결과가 나올 줄 알았고 `출력 2` 에선 1이라는 결과가 나올 줄 

알았는데 `출력 1` 과 `출력 2` 에선 둘다 1이라는 결과가 나왔다. 엥 ( ꒪⌓꒪)?

위에서 말한 것 처럼 자바스크립트는 렉시컬 스코프를 따르기 때문에 1이라는 결과 값이 나온 것이다.

즉 test2 함수는 자신이 정의된 전역 스코프를 참조하기 때문에 전역 변수 x를 접근(참조)한다.

렉시컬 스코프는 클로저와 관련이 있어서 다음에는 클로저에 대해서 공부를 해봐야 겠다. ✍