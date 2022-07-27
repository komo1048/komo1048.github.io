---
title: "[React] useMemo"
excerpt: "useMemo에 대해 알아보자"

categories:
  - React
tags:
  - [React]

toc: true
toc_sticky: true

date: 2022-07-27
last_modified_at: 2022-07-27
---

오늘은 useMemo에 대해서 알아보려고 한다.

# useMemo 란?

`React.memo`의 인자로 들어간 컴포넌트에 어떤 props가 입력되는지 확인 후

입력되는 모든 props의 최신 값을 확인한 뒤 그것을 기존의 props의 값과 비교하도록 리액트에게 전달한다.

만약 비교했을 때 props의 값이 바뀐 경우에만 컴포넌트를 `재실행`하게 된다. 여기서 부모 컴포넌트가 변경되었지만

그 컴포넌트의 props의 값이 바뀌지 않았다면 그것은 무시하고 넘어간다.

예제 코드 👇

```javascript
const test = (prosp) => {
  console.log('hi');
  ...

  return ...
}

export default React.memo(test); //test의 props 값이 변경되었을 경우 test 컴포넌트를 재실행
```

처음 콘솔로그에는 `hi`라는 글이 써지지만 만약 props가 변경되지 않으면 그 다음에는 `hi`라는게 써지지 않는다.

만약 test 컴포넌트 아래 자식 컴포넌트가 있다면 당연히 재실행이 되지 않는다.

💡 이렇게 달라지지 않으면 재실행하지 않는 이렇게 좋은 훅을 왜 모든 컴포넌트에 적용시키지 않을까?

라는 생각이 드는데 이렇게 최적화를 하게 될 때 그 만큼 비용이 따르기 때문이다.

이 useMemo 훅은 변경이 발생할 때마다 기존 props 값과 최신의 props 값을 비교합니다.

이렇게 매번 비교를 하기 때문에 기존 props 저장공간과 비교하는 작업이 필요하기 때문에 모든 컴포넌트에

적용시키지 않는다. 만약 컴포넌트 트리가 매우 크고 `useMemo`를 사용하는 컴포넌트 위치가 상위에 있다면

전체 컴포넌트 트리에 대한 쓸데없는 재실행을 막을 수 있어서 유용하다.

반대로 컴포넌트의 변화가 있거나 props의 값이 변화가 드문 경우라면 `useMemo`는 안쓰는 편이 더 좋다.

아래는 [React 공식 홈페이지](https://ko.reactjs.org/docs/hooks-reference.html#usememo) 에 나와있는 `useMemo` 기본 형식이다.

`const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);`

맨뒤에 `[]`로 감싼 `a` 또는 `b` 값이 변경되었을 경우 재실행이 된다.

다음에는 useMemo와 같이 사용할 수 있는 useCallback에 대해서 포스팅해보려고 한다~!

요즘 포스팅을 많이 못쓰게 되었는데,,,~~귀찮~~ 그래도 꾸준히 해보자 ..! 🔥
