---
title: "[알고리즘] 문자열 검색 Naive Pattern Searching Algorithm"
excerpt: "문자열 검색 Naive Pattern Searching Algorithm"

categories:
  - Javascript
tags:
  - [Javascript, Algorithm]

toc: true
toc_sticky: true

date : 2022-06-18
last_modified_at : 2022-06-18
---

이번엔 문자열 검색 알고리즘인 Naive Pattern Searching Algorithm을 공부하려고 한다.

이 알고리즘은 단순하게 처음부터 끝까지 문자를 하나하나 비교해가면서 일치하는 것을 찾는 알고리즘이다.

> 과정

1. 문자열(arr)과 찾고자하는 문자열(val)이 주어진다.

2. arr의 첫 번째 값과 val의 첫 번째 값을 비교한다.

3. 두 값이 일치하면 arr의 두 번째 값과 val의 두 번째 값을 비교한다.

4. 이번에도 두 값이 일치하면 인덱스를 1씩 늘려가며 val의 값이 모두 일치한지 검사를 한다.

5. 모두 일치하면 count 값을 1 증가 시킨다.

6. 만약 일치하지 않으면 arr의 두 번째 값부터 다시 위의 과정을 반복한다.

이 처럼 단순하게 모든 배열의 값들을 하나하나 비교하는 과정이다.

위 과정을 자바스크립트 코드로 봐보자 ❗

예제 코드 👇

```javascript
function naive(arr, val){
    let count = 0;

    for(let i=0; i<arr.length; i++){ // 문자열을 하나씩 반복한다.
        for(let j=0; j<val.length; j++){ // 찾고자하는 문자열도 마찬가지로 하나씩 반복한다.
            if(arr[i+j] !== val[j]){
                break;  // 서로 비교 했을 때 같지 않으면 바로 다음으로 넘기기 위해 break
            }
            if(j === val.length - 1){ // val값과 모두 일치하기 때문에 count 1 증가
                count++;
            }
        }
    }
    return count; // 찾은 문자열의 갯수를 출력
}
```

이렇게 문자열 검색은 끝이 났다. 

위 코드보다 더 잘 짜여진 코드가 있겠지만 차근차근 하나씩 배워 나가보자 ❗❗