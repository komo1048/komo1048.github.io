---
title: "[오늘의 배움] var vs let, const"
excerpt: "var vs let, const에 대해 알아보자"

categories:
  - Javascript
tags:
  - [오늘의배움, Javascript]

toc: true
toc_sticky: true

date: 2022-07-08
last_modified_at: 2022-07-08
---

어제 `ES5`와 `ES6`의 차이점에 이어 `var`과 `let`, `const`의 차이점에 대해서 알아보려고 한다.

사실 전에 [Scope](https://komo1048.github.io/posts/Scope/)에 대해서 올렸을 때 이 주제에 대해서 약간 언급한 적이 있다.

이 포스팅에서는 좀 더 자세하게 알아보자.

# var

먼저 `ES5`에서 있었던 `var`에 대해서 알아보자.

`var` 특징은 중복 선언이 가능하다. 보통 언어들을 보면 중복 선언이 불가능 한데 자바스크립트의 var는 가능하다.

예제 코드 👇

```javascript
var name = "cojaldan";
console.log(name); // result : cojaldan

var name = "hi";
console.log(name); // result : hi
```

이렇게 중복으로 선언이 되었을 경우 마지막에 할당한 값으로 할당이 된다.

심지어 에러도 안난다 ! 이렇기 때문에 `var`로 선언하면 나중에 오류가 발생할 위험이 있다.

`var`는 `함수 레벨 스코프`다. 위에 포스팅에서도 언급했지만 함수 안에서만 지역 스코프가 된다.

`for`, `if` 등도 전역 스코프가 되어 버린다.

예제 코드 👇

```javascript
for (var i = 0; i < 3; i++) {
  console.log(i); // result : 0 1 2
}

console.log(i); // result : 3
```

이렇게 `for`문에 `i`를 선언했지만 `for`문 밖에서도 값이 잘 나오는 걸 볼 수가 있다.

하지만 아래의 경우는 다르다.

예제 코드 👇

```javascript
function test() {
  var i = 10;
}

console.log(i); // Uncaught ReferenceError: i is not defined
```

위 코드와 같이 함수 안에 `i`가 선언 되었기 때문에 함수 안에서만 참조가 가능하다.

# let const

다음은 `ES6`부터 도입된 `let`, `const`이라는 키워드이다.

`let`은 `var`와 다르게 `중복선언`이 불가능하다.

`const`는 `중복선언`이 불가능하고 `재할당`도 불가능하다.

예제 코드 👇

```javascript
let test = 1;

console.log(test);

let test = 2; // test = 2; 이렇게 재할당은 가능하다 !
console.log(test); // result : SyntaxError: Identifier 'test' has already been declared

const test = 1;

console.log(test);

const test = 1; // test = 1; const로 선언된 변수는 이렇게 재할당도 안된다.

console.log(test); // result : SyntaxError: Identifier 'test' has already been declared
```

위와 같이 에러가 발생한다.

`let`과 `const`의 차이는 재할당을 할 수 있냐 없냐 차이이다. 즉 `immutable` 차이다.

그리고 `var`는 `함수 레벨 스코프` 였지만 `let`과 `const`는 `블록 레벨 스코프`를 갖는다.

예제 코드 👇

```javascript
for (let i = 0; i < 3; i++) {
  console.log(i); // result : 0 1 2
}

console.log(i); // result : ReferenceError: i is not defined
```

이렇게 아까 `var`와는 달리 에러가 뜬다. 이렇듯 `let`과 `const`는 `for`문, `if`문 등에서도 `지역 스코프`를 갖게 된다.

또 `호이스팅`에서도 차이가 나는데 `호이스팅`에 대한 것은 [이곳](https://komo1048.github.io/posts/hoisting/)에서 확인하면 될 것 같다 ㅎㅎ.
