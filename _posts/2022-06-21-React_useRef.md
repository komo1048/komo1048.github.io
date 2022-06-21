---
title: "[React] useRef"
excerpt: "useRef에 대해 알아보자"

categories:
  - React
tags:
  - [React]

toc: true
toc_sticky: true

date : 2022-06-21
last_modified_at : 2022-06-21
---

오늘은 리액트의 훅중 하나인 useRef에 대해서 공부해보려고 한다.

원래 앞에 내용도 공부해야하는데 먼저 메모한 useRef부터 남겨야 겠다 ㅎㅎ;;

# useRef 란?

사용자 입력에 접근할 수 있는 또는 특정 DOM을 가리킬 때 사용하는 hook 중 하나이다.

이것을 사용할 때는 특정 DOM에 대한 포커스, 엘리먼트 크기나 색상을 변경할 때 사용한다.

`useRef`는 자바스크립트에서 많이 사용하는 getElementById 같은 특정 DOM을 선택하는 것이라고 생각하면 될 것 같다.

사용자 입력을 `state`로 관리할 수 있지만 useRef를 사용하면 간단하게 접근이 가능하다.

`⭐ 사용자 입력을 변경할 때 useRef를 사용하는 것은 아니다 ! useRef로는 값을 읽기만 하고 변경하지 않는다.`

사용 방법은 `useState`처럼 상단에  import { useRef } from 'react'; 라고 선언해 주면 된다.

그리고 const 변수명 = useRef(); 라고 하고 가리키고 싶은 태그에 ref={변수명}을 추가 해주면 끝이다 ! 매우 간단하다 🤷‍♀️

ref는 항상 객체이고 안에 current 라는 프로퍼티를 항상 갖고있다.

current 프로퍼티로 전달된 인자(initialValue)로 초기화된 변경 가능한 ref 객체를 반환합니다.

오늘도 역시 코드로 한번 봐보자.

예제 코드 👇

```javascript
import React, { useRef } from 'react'; // 상단에 선언

const AddUser = (props) => {
    const inputRef = useRef();  // 가리킬 DOM을 갖고올 변수 선언

    ...생략

    return (
        <div>
            ...생략
            <input id="username" type="text" ref={inputRef} /> // 가리킬 DOM 설정
        </div>
    );
}

export default AddUser;
```

이 코드 처럼 위에 변수를 useRef 변수를 선언해주고 가리키고 싶은 태그에 ref={변수명}을 넣어주면 끝이 난다.

이제 current를 사용해 로그를 찍어보면 input 태그에 입력한 값이 찍히는 걸 볼 수가 있다.

`inputRef.current.value = 'hello world'; ` 이런식으로 값을 변경할 수 있지만 위에서 말했듯이 잘 사용하지 않는다.

오늘은 이렇게 useRef에 대해서 알아보았는데 아직 많이 부족한 것 같다,,

사실 앞부분도 잘 모른다,, 그래도 일단 쭉 공부하고 다시 복습하는 식으로 해야겠다.