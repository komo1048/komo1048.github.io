---
title: "[오늘의 배움] 가상메모리"
excerpt: "가상메모리"

categories:
  - 오늘의배움
  - 운영체제
tags:
  - [오늘의배움, 운영체제]

toc: true
toc_sticky: true

date: 2022-12-28
last_modified_at: 2022-12-28
---

> 가상 메모리에 대해 알아보기 전 알아야할 개념 !

- 메모리는 내부 기억장치인 `주 기억장치`와 외부 기억장치인 `보조 기억장치`로 나눠진다.

```
주기억장치 : RAM, CPU의 레지스터, 캐시
보조 기억장치 : HDD, SSD
```

> 가상 메모리란?

가상 메모리는 사용자에게 메모리를 매우 큰 메모리로 보이게 만드는 것이다.

프로그램을 실행 시킬 때 현재 메모리로는 실행 시키지 못한다면, 프로그램을 실행 시킬 수 있는 최소한의 메모리를 `주기억장치`로 사용하고 나머지는 `보조기억장치`를 사용해 프로그램을 실행 시킨다.

이 처럼 실제 메모리를 적지만 `보조기억장치`의 도움을 받아 실행 시키므로 사용자에게 메모리를 더 커보이게 만들 수 있다.
