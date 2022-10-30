---
title: "[Error] React todo list 중 에러"
excerpt: "React 에러"

categories:
  - React
tags:
  - [React]

toc: true
toc_sticky: true

date: 2022-10-30
last_modified_at: 2022-10-30
---

오늘은 `React`로 `Todo List`를 만드는 연습 중에 나온 에러를 정리하려고 한다.

# 에러

![2022-10-30-React-bindImg1](https://user-images.githubusercontent.com/11023303/198876278-c9a4ec2a-2241-4abd-b726-7b604301b50a.png)

위와 같이 아이템 목록중에 삭제 버튼을 클릭하면 아이템이 삭제가 되어야 하는데 삭제는 안되고 아래와 같은 에러 메세지가 떴다.

![2022-10-30-React-bindImg2](https://user-images.githubusercontent.com/11023303/198876288-c7cedf71-58b1-4815-a54f-567446712e87.png)

이유는 onClick에는 함수 포인터를 넘겨야하는데 함수를 호출하고 있어서 에러가 나오던 것이였다.

# 해결방법

첫 번째로는 bind 함수를 사용하는 방법이다.

![2022-10-30-React-bindImg3](https://user-images.githubusercontent.com/11023303/198876298-b381c80f-47d9-403d-8a30-2afce272cf4c.png)

bind 함수는 새로운 함수를 반환해줘서 가능하다고 한다.

두 번째 방법은 onClick으로 호출하는 함수를 따로 만드는 방법이다.

![2022-10-30-React-bindImg4](https://user-images.githubusercontent.com/11023303/198876308-d16f1bee-b82b-4726-8de9-fe4a60098f69.png)

이렇게 해주면 onClick에서 함수를 바로 호출하지 않기 때문에 에러가 나지 않는다.
