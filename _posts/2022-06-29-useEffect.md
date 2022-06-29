---
title: "[React] useEffect"
excerpt: "useEffect에 대해 알아보자"

categories:
  - React
tags:
  - [React]

toc: true
toc_sticky: true

date : 2022-06-29
last_modified_at : 2022-06-29
---

오늘은 리액트의 중요한 개념인 useEffect에 대해서 알아보려고 한다.

# useEffect 란?

useEffect는 리액트가 제공해주는 기본 hook중 하나이다.

useEffect는 컴포넌트가 렌더링 될 때 어떤 일을 실행할 수 있게 해준다.

근데 무조건 그 일을 실행하는 것이 아니라 렌더링 되는 경우가 따로 있다.

- 컴포넌트가 렌더링 되고 난 후 한번만 실행되는 경우
- useEffect에 지정한 값이 변경이 되는 경우

물론 이거 말고 더 있을 수 있으나,, 지금 공부한건 이 두가지이다. ㅠ.,ㅠ

useEffect는 두개의 매개변수와 함께 호출되는데 

첫 번째는 함수 두 번째는 지정할 값을 넣으면 된다.

여기서 두 번째에 넣은 값이 변경될 때마다 첫 번째에 넣었던 함수가 실행되는 것이다 !!

한 번 코드를 보고 다시 이해해 보자.

예제 코드 👇

```javascript
... 코드 생략

useEffect(() => { // 1번
    console.log('EFFECT RUNNING');

    return () => { // 2번
      console.log('EFFECT CLEANUP');
    }
}, []);

useEffect(() => { // 3번
    const timer = setTimeout(()=>{
        console.log('Check form');
        
        setFormIsValid(
            enteredEmail.includes('@') && enteredPassword.trim().length > 6
        );  
    }, 500);

    return () => { // 4번
        console.log('CLEANUP');
        clearTimeout(timer);
    }
}, [enteredEmail, enteredPassword]); 

... 코드 생략
```

이 코드에는 안나와 있지만 3번 코드에 두 번째 매개변수로 `enterdEmail, enteredPassword`가 들어가 있는데

이게 `enterdEmail, enteredPassword` 이 두 가지 중 변경되는 값이 있으면 3번의 함수를 실행한다는 것이다.

만약에 1번 `useEffect`와 같이 지정한 값이 없으면 맨 처음 렌더링 될 때 한 번 실행이 된다.

근데 여기서 2번과 4번 처럼 반환 되는 함수가 있는데 이걸 `cleanup` 함수 라고한다.

만약 `cleanup` 함수가 지정 되어 있다면 컴포넌트가 언마운트가 될 때, 업데이트가 되기 직전에 `cleanup` 함수가 실행된다.

여기서 2번 처럼 두 번째 매개변수가 빈 배열이라면 컴포넌트가 언마운트 될 때 실행이 되고,

4번 처럼 두 번째 매개변수에 값을 지정해주었다면 지정해준 값이 업데이트가 되기 직전에 `cleanup` 함수가 실행된다.

또 ❗ 만약에 이렇게 사용하지는 않는다고 하지만 두 번째 매개변수에 아무것도 넣지 않는다면 

예제 코드 👇

```javascript
useEffect(() => {
    console.log('EFFECT RUNNING');
});
```

렌더링 될 때 마다 실행이 된다.

이렇게 오늘은 useEffect에 대해서 알아보았다. 

리액트는 공부하면 할수록 더 어려워 지는 것 같다,, 😥