---
title: "[알고리즘] 이진탐색 Binary Search"
excerpt: "이진탐색 Binary Search"

categories:
  - Javascript
  - Algorithm
tags:
  - [Javascript, Algorithm]

toc: true
toc_sticky: true

date : 2022-06-18
last_modified_at : 2022-06-18
---

이진 탐색 Binary Search 하는 방법에 대해서 알아보자.

> 이진 탐색 Binary Search

이진 탐색이란 정렬되어 있는 배열의 반을 나눠가며 검색을 하는 알고리즘이다.

빅오 표기법은 `O(log n)` 이다.

> 과정

1. 정렬되어 있는 배열의 처음 부분(left)과 끝 부분(right)을 포인터로 잡는다.

2. 배열의 중간 지점을 찾는다.

3. 중간 지점의 값(mid)과 찾고자 하는 값(val)을 비교한다.

4. mid 값이 더 클 경우 right를 mid 보다 한칸 앞으로 이동한다.

5. 반대의 경우 left를 중간 지점 보다 한칸 뒤로 이동한다.

6. 이동 후의 left와 right의 중간 지점을 다시 mid로 잡는다.

7. 다시 3번 과정부터 반복한다.

위 과정을 자바스크립트 코드로 다시 한번 봐보자 ❗

예제 코드 👇

```javascript
// 반복문이 끝나는 조건은 배열의 찾는 값이 있어 반환 되거나 배열의 찾는 값이 없을 때 -1을 반환하는 조건이다.

function binary(arr, val){
    let left = 0; // 배열의 첫 부분을 가리키는 포인터
    let right = arr.length - 1; // 배열의 마지막 부분을 가리키는 포인터
    let mid; // 배열의 중간 부분을 가리키는 포인터

    while(left <= right){   // 값이 없을 경우 무한반복 되는 것을 막기 위한 조건
        mid = Math.floor((left+right)/2); // mid 값을 구하는 과정
        if(arr[mid] === val){
			return mid; 	// 현재 인덱스가 val과 같으므로 현재 인덱스 값 반환
		}else if(arr[mid] > val){
			right = mid - 1; // mid 값이 더 큰 경우 mid보다 한칸 앞으로 설정
		}else{
			left = mid + 1; // mid 값이 더 작은 경우 mid 보다 한칸 뒤로 설정
		}
		return -1;
    }
}
```

위 예제 코드가 `과정` 에서 글로 설명한 것을 코드로 나타낸 것이다 ❗❗

이진 탐색은 그렇게 어렵지 않았지만 다른 알고리즘들은 더 어렵겠지 ༼ಢ_ಢ༽

열심히 해보자,, 💪💪