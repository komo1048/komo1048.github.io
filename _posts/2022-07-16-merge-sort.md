---
title: "[Algorithm] 합병 정렬"
excerpt: "합병 정렬에 대해 알아보자"

categories:
  - Javascript
  - Algorithm
tags:
  - [Algorithm, Javascript]

toc: true
toc_sticky: true

date: 2022-07-16
last_modified_at: 2022-07-16
---

오늘은 알고리즘 중 `합병 정렬`에 대해서 알아보려고 한다.

# 합병 정렬이란?

합병 정렬은 이름 그대로 합병과 정렬이라는 두 가지 조합으로 이루어져 있는데 사실 `분할`, `정렬,` `합병`

이 세 가지가 모두 일어난다.

다음을 한 번 봐보자.

```
[3,6,9,5,1,7,2,4] --> 분할

[3,6,9,5] [1,7,2,4] --> 분할

[3,6] [9,5] [1,7] [2,4] --> 분할

[3] [6] [9] [5] [1] [7] [2] [4] --> 정렬

[3,6] [5,9] [1,7] [2,4] --> 정렬

[3,5,6,9] [1,2,4,7] --> 정렬 및 합병

[1,2,3,4,5,6,7,9]
```

이렇게 해서 3가지 일이 일어나는 것이다.

다음 코드는 위와 같은 방법은 아니지만 정렬되어 있는 배열을 `합병정렬`로 정렬하는 방법이다.

예제 코드 👇

```javascript
function mergeSort(arr1, arr2) {
  let result = [];
  let arr1P = 0; // arr1 배열의 포인터
  let arr2P = 0; // arr2 배열의 포인터

  while (arr1P < arr1.length && arr2P < arr2.length) {
    if (arr2[arr2P] > arr1[arr1P]) {
      result.push(arr1[arr1P]);
      arr1P++;
    } else {
      result.push(arr2[arr2P]);
      arr2P++;
    }
  }
  // 두 배열의 크기가 다르면 나머지 부분을 result 배열의 넣는다.
  while (arr1P < arr1.length) {
    result.push(arr1[arr1P]);
    arr1P++;
  }
  while (arr2P < arr2.length) {
    result.push(arr2[arr2P]);
    arr2P++;
  }

  return result;
}

mergeSort([1, 6, 25], [3, 17, 55, 99]); // result : [1, 3, 6, 17, 25, 55, 99]
```

다음은 정렬까지 포함한 코드로 봐보려고 한다 !! 보기전에 `재귀함수`에 대해서 알고있으면 이해하기 더 쉽다.

💡 맨 위에 숫자로 합병 정렬 방법을 설명한 것도 참고해서 보면 더 이해하기 쉬울 것 같다 !

```javascript
function mergeSort(arr1, arr2) {
  let result = [];
  let arr1P = 0;
  let arr2P = 0;

  while (arr1P < arr1.length && arr2P < arr2.length) {
    if (arr2[arr2P] > arr1[arr1P]) {
      result.push(arr1[arr1P]);
      arr1P++;
    } else {
      result.push(arr2[arr2P]);
      arr2P++;
    }
  }

  while (arr1P < arr1.length) {
    result.push(arr1[arr1P]);
    arr1P++;
  }
  while (arr2P < arr2.length) {
    result.push(arr2[arr2P]);
    arr2P++;
  }

  return result;
}

function merge(arr) {
  if (arr.length <= 1) return arr; // 길이가 1이면 반환
  let midP = Math.floor(arr.lengh / 2); // 배열의 중간 지점 포인터
  let left = merge(arr.slice(0, mid)); // 재귀 함수 !!
  let right = merge(arr.slice(mid)); // 재귀 함수 !!
  return mergeSort(left, right);
}

merge([56, 32, 96, 74]); // result : [32, 56, 74, 96]
```

위에 코드를 다시 한 번 숫자로 설명하자면 다음과 같다.

```javascript
[56, 32, 96, 74] --> 중간 지점으로 나누기 --> Math.floor(arr.lengh/2)

--> merge 함수 호출(재귀함수) merge(arr.slice(0, mid)) --> [56, 32]
                            merge(arr.slice(mid)) --> [96, 74]

[56, 32] [96, 74] -->  중간 지점 나누기 --> Math.floor(arr.lengh/2)

--> merge 함수 호출(재귀함수) merge(arr.slice(0, mid)) --> [56] --> return
                            merge(arr.slice(mid)) --> [32] --> return
                            --> 정렬 !!

--> merge 함수 호출(재귀함수) merge(arr.slice(0, mid)) --> [96] --> return
                            merge(arr.slice(mid)) --> [74] --> return
                            --> 정렬 !!

이제 아까 정렬된 함수를 합병 시켜주는 mergeSort 함수를 호출 --> mergeSort(left, right)

결과 --> [32, 56, 74, 96]
```

재귀함수 부분만 잘 이해할 수 있으면 나머지 부분은 그렇게 어려운 것 같지 않다. ~~사실 어려움~~

마지막으로 합병정렬의 빅오는 최적, 평균, 최악이 모두 O(nlog n)으로 같다.
