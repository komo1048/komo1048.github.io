---
title: "[오늘의 배움] 브라우저가 렌더링될 때"
excerpt: "브라우저가 렌더링될 때에 대해"

categories:
  - Javascript
tags:
  - [Javascript, 오늘의배움]

toc: true
toc_sticky: true

date: 2022-07-15
last_modified_at: 2022-07-15
---

오늘은 브라우저가 렌더링 될 때에 대해서 공부해보았다. 전부터 궁금하긴 했는데 이제서야 알아봤다 ㅎㅎ;

`html`파일을 브라우저 렌더링 엔진이 읽을 때 `html` 문서를 파싱해 브라우저가 이해 할 수 있는 자료구조인 `DOM`을 생성하게 된다.

과정은 서버에 있던 `html` 파일이 브라우저의 요청에 의해 응답이 되는데 이때 서버는 그 파일을 바이트 단위로 저장 후

보내게 된다. 이때 응답 받은 브라우저는 `html` 문서에 `meta` 태그의 `charset`에 의해 인코딩 방식을 기준으로 문자열로 변환된다.

그 다음 변환된 `html`문서를 읽어 들여 `토큰`들로 분해한다. 여기서 `토큰` 단위는

객체와 비슷하게 전달이 되는데 아래와 같이 전달된다고 한다.

```javascript
{
    startTag: 'html',
    contents: {
        startTag: 'head',
        contents: { ... },
        ...
    }
    endTag: 'html'
}  // 출처 : 모던 자바스크립트
```

잘보면 `html` 파일 처럼 `html` 태그와 `head` 태그가 보인다.

이렇게 `토큰` 단위로 분해를 한 후 `노드`로 생성이 된다. `토큰`의 따라서 `노드`는

`문서 노드`, `요소 노드`, `어트리뷰트 노드`, `텍스트 노드`가 생성이 된다.

그리고 이 `노드`들을 가지고 트리 구조로 구성하게 되는데 그것을 `DOM`이라고 한다.

이것을 공부하면서 전부터 궁금했던게 풀렸는데 스크립트 파일이 안먹으면 `javascript` 파일을 로드할 때

맨아래에다 넣어라 라고 하는 답변을 많이 봤었다. 그게 왜 그럴까? 했는데 이유는 파싱 과정에서 렌더링 엔진은 `html`를 한 줄씩 실행하고

파싱하면서 `javascript` 파일을 로드하는 `script` 태그를 만나면 `DOM` 생성을 `멈추고`

자바스크립트 파일을 실행하게 된다. 그래서 만약 자바스크립트 파일안에 `html` 문서의 특정 태그를 조작하는데

만약 그 태그를 아직 파싱하지 못했다면 해당 코드를 실행해봤자 아무 일이 일어나지 않는 것이다.

이 이유 때문에 `javascript` 파일을 로드하는 태그는 `html`문서 맨 아래에 선언해주는게 좋았던 것이였다 !!

궁금했을 때 빨리 검색해봤으면 더 빨리 이해할 수 있었을 텐데 이제 와서 알아보았다니,,

정말 게을렀던 것 같다 ㅋㅎㅋㅎ
