---
title: "[React] redux-toolkit - createSlice, useDispatch, useSelector "
excerpt: "redux-toolkit에 createSlice, useDispatch, useSelector에 대해"

categories:
  - React
tags:
  - [React]

toc: true
toc_sticky: true

date: 2022-08-09
last_modified_at: 2022-08-09
---

`createSlice`, `useDispatch`, `useSelector`에 대한 간단한 정리

`createSlice` : `reducer`와 같이 상황에 따라 상태를 변경할 수 있도록 하는 훅이다.

```javascript
const counterSlice = createSlice({
  name: "counter",
  initialState: initialCounterState,
  reducers: {
    increment(state) {
      state.counter++;
    },
    decrement(state) {
      state.counter--;
    },
    increase(state, action) {
      state.counter = state.counter + action.payload;
    },
    toggleCounter(state) {
      state.showCounter = !state.showCounter;
    },
  },
});
```

원래는 `state.counter++` 과 같이 기본 상태 값을 직접 변경하면 안되지만

`redux-toolkit`은 알아서 새로운 상태를 복제해(만들어서?) 반환해준다.

또 위와 같이 상태를 변경할 때 매개변수를 사용해 변경해야하는 상황이 온다면 `payload`로 받는다.

`payload`는 기본 값이기 때문에 변경할 수 없다.

`useDispatch` : `reducer`에 `dispatch`와 같이 상태를 변경하는 훅

`useSelector` : `useDispatch`로 상태를 변경한 값을 갖고오는 훅
