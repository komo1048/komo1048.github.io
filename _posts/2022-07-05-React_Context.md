---
title: "[React] Context"
excerpt: "Context에 대해 알아보자"

categories:
  - React
tags:
  - [React]

toc: true
toc_sticky: true

date : 2022-07-05
last_modified_at : 2022-07-05
---

오늘은 React의 Context에 대해서 알아보자.

# Context 란?

리액트에 내장된 `state` 저장소가 있는데 그것이 리액트 `Context`라는 개념이다.

![2022-07-05-React_ContextImg](https://user-images.githubusercontent.com/11023303/177318373-fed98657-70b0-4a8f-806a-f6d4967e9983.png)

~~발그림 😅~~

이 이미지로 설명을 하려고한다. 만약 `Context`라는 것을 모른다 가정해보자.

`1-1 컴포넌트`에서 로그인에 대한 정보를 얻는다.

근데 그 정보를 `2 컴포넌트`에서 사용한다고 한다. 그럼 `1 컴포넌트`에 전달 -> `App` -> `2 컴포넌트`에 전달. 이런 로직이 될 텐데,

이렇게 예시를 간단하게 해서 이 정도면 할만 하다고 생각하겠지만 만약 더 복잡한 로직이라면 관리하기 힘들 것이고,

다른 여러 곳에서 사용해야 한다면 더욱 더 힘들 것이다.

그래서 사용하는 것이 `Context` 라는 개념이다 !

`Context`를 사용한다면 `1-1 컴포넌트`에서 얻은 로그인에 대한 정보를 `Context`에 저장 후

그 정보를 필요로 하는 컴포넌트에서 바로 가져다 쓰면 된다 !

하지만 `Context`를 항상 사용하는 것은 아니다. `state`가 짧은 시간에 여러 번 변경되는 경우,

`Context`를 사용한 버튼 같은 컴포넌트는 `Context`가 없이는 재사용이 힘들기 때문에 사용을 삼가해야한다.

> context 사용방법

`Context`의 기본 폼은 아래와 같다.

```javascript
const MyContext = React.createContext(defaultValue);
```

매개변수 `defaultValue` 자리에는 `Context`로 전달할 값을 넣어주면 된다.

예제 코드 👇

```javascript
import React from "react";

const MyContext = React.createContext({
  contextEx: false // 기본값
});

export default MyContext;
```

이렇게 선언한 후에 필요로하는 컴포넌트를 `MyContext`로 감싸면 된다.

예제 코드 👇

```javascript
<MyContext.Provider value={{
  contextEx: false // 기본값, 여기서 변경가능
}}> 
..context를 사용할 컴포넌트들
</MyContext.Provider>
```

그 다음 `Context`를 사용하려는 컴포넌트에 가서는

예제 코드 👇

```javascript
<MyContext.Consumer>
  {(value) => {return (
    /*JSX코드*/
    value.contextEx
    )}} // 여기서 value는 MyContext.Provider의 값을 가져옴
</MyContext.Consumer>
```

`Context`는 이렇게 사용하면 되는데 더 간단하게 만들 수도 있다.

`useContext`를 사용하는 것이다 !

맨 위에 `useContext`를 선언 해주고 `MyContext`를 넣어주면 된다.

예제 코드 👇

```javascript
const myContext = useContext(MyContext);
```

이렇게 해주면 `Consumer`를 사용하지 않고 `contextEx` 값을 바로 사용할 수 있다.

예제 코드 👇

```javascript
import { useContext } from 'react';
import MyContext from ...; // 경로에 맞게 넣어준다.

...
const myContext = useContext(MyContext);

return (
  {myContext.contextEx &&(
    <div>Hi </div>
  )}
);

...
```

이렇게 더 간단하게 `Context`를 사용할 수도 있다. 

오늘은 이렇게 `Context`라는 개념에 대해서 공부해봤는데 리액트는 공부할수록 어려워지는 거 같다 ㅠㅠ

# 💡 틀린 것이 있다면 지적 부탁드립니다 !!!