---
title: "[오늘의 배움] async await"
excerpt: "async await에 대해"

categories:
  - Javascript
tags:
  - [오늘의배움, Javascript]

toc: true
toc_sticky: true

date: 2022-08-21
last_modified_at: 2022-08-21
---

오늘은 `async await`에 대해서 알아보자.

먼저 들어가기 전에 [Promise](https://komo1048.github.io/posts/Promise/)에 대해서 먼저 알고 보면 더 좋을 것 같다.

`async await`이란 프로미스 기반으로 비동기 코드를 동기 코드처럼 보이게 도와주는 키워드이다.

`await` 키워드는 반드시 `async` 함수 내부에서 사용해야 한다. 아니면 에러가 난다.

`async` 함수는 프로미스를 반환한다.

코드로 보면서 다시 이해해보자.

예제코드 👇

```javascript
const timer = (time) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(time);
    }, time);
  });
};

timer(1000).then(console.log); // 1초 후 결과 -> 1000
```

만약 `Promise`로 1초 뒤 실행이 되는 코드를 짠다면 이런식으로 될 것이다.

1초 후 실행되는 코드 다음 또 다시 1초 후 실행되는 코드를 짠다면 아래와 같을 것이다.

```javascript
const timer = (time) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(time);
    }, time);
  });
};

timer(1000)
  .then((time) => {
    console.log(time);
    return timer(time);
  })
  .then(console.log);
```

이렇게 계속 해서 찍는다면 또 코드가 복잡해진다..

그래서 나온게 `async await` 인데 바로 바꿔 보자.

예제코드 👇

```javascript
const timer = (time) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(time);
    }, time);
  });
};

let time = await timer(1000);

console.log(time);

time = await timer(1000);

console.log(time);
```

위 코드를 실행하면 어떻게 될까??

위에서 말했듯이 `async` 없이 `await` 만 쓴다면 에러가 난다.

그래서 `await` 을 `async` 함수 내부로 옮겨준다.

```javascript
const timer = (time) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(time);
    }, time);
  });
};

const run = async () => {
  let time = await timer(1000);

  console.log(time);

  time = await timer(1000);

  console.log(time);
};

run();
```

코드만 본다면 일반적인 자바스크립트 처럼 동기 코드로 보인다.

하지만 실제로 아래 코드처럼 `run` 함수 위아래로 `console.log`를 찍고 실행해보면 비동기적으로 동작을 한다.

```javascript
// ...생략

console.log("start");
run();
console.log("end");

/*
result

start
end
run함수내용..

*/
```

이렇게 오늘은 `async await`에 대해서 공부해 봤는데 약간 이해가 되면서도 헷갈리는 부분이 조금 있는 거 같다..

요즘 공부하기 귀찮아졌는데,, 화이팅 해보자 !!🔥
