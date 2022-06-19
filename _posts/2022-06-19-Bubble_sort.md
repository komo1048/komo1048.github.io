---
title: "[알고리즘] 버블정렬"
excerpt: "버블 정렬에 대해 알아보자"

categories:
  - [javascript, Algorithm]
tags:
  - [Algorithm, Javascript]

toc: true
toc_sticky: true

date : 2022-06-19
last_modified_at : 2022-06-19
---

오늘 알고리즘은 버블 정렬에 대해서 알아보려고 한다.

# 버블 정렬이란?

버블 정렬의 빅오표기법은 O(n^2)으로 데이터가 많으면 매우 오래걸리는 정렬이고 정렬이 거의 다 된

배열을 정렬한다고 하면 매우매우 비효율 적인 정렬 방법이다.

만약 [1,6,2,3,7] 이라는 배열을 정렬한다고 하자.

버블 정렬은 첫 번째 데이터(1)와 바로 옆에 있는 데이터(6)와 비교해 크면 자리를 바꾸고 아니면 옆 데이터(6)

와 그 옆에 데이터(7)를 비교해나가면서 정렬하는 정렬 방법이다.

말로 설명하는 건 잘 이해가 되지 않으니 바로 예제 코드로 봐보자.

예제 코드 👇

```javascript
function bubble(arr){
    for(let i=0; i<arr.length; i++){
        for(let j=0; j<arr.length; j++){
            if(arr[j] > arr[j+1]){ // 바로 옆 데이터와 비교
                let temp = arr[j]; // 크면 서로 데이터를 바꾸기 위해 임시 변수에 데이터를 넣는다.
                arr[j] = arr[j+1]; // 데이터 교체
                arr[j+1] = temp;
            }
        }
    }
    return arr;
}
```

위 예제 코드 처럼 배열의 데이터들을 전부 비교해가며 정렬을 한다.

근데 ❗ 위에 코드를 실행할 때 로그를 한번 찍어보면 마지막 수를 비교할 때 undefined와 비교하는 걸 볼 수가

있다. 그래서 두번째 반복문이 돌 때도 이미 정렬된 마지막 데이터까지 비교하는 것도 볼 수가 있다. 이것을 

최적화한 코드를 다시 짠다면 이렇게 될 것 같다.

예제 코드 👇

```javascript
function bubble(arr){
    for(let i=arr.length; i>0; i--){
        for(let j=0; j<i-1; j++){
            if(arr[j] > arr[j+1]){ // 바로 옆 데이터와 비교
                let temp = arr[j]; // 크면 서로 데이터를 바꾸기 위해 임시 변수에 데이터를 넣는다.
                arr[j] = arr[j+1]; // 데이터 교체
                arr[j+1] = temp;
            }
        }
    }
    return arr;
}
```

이 코드에서 한번 더 최적화를 한다면 이런 코드일 것이다 !!

```javascript
function bubble(arr){
    let fin;
    for(let i=arr.length; i>0; i--){
        fin = true;                
        for(let j=0; j<i-1; j++){
            if(arr[j] > arr[j+1]){ // 바로 옆 데이터와 비교
                let temp = arr[j]; // 크면 서로 데이터를 바꾸기 위해 임시 변수에 데이터를 넣는다.
                arr[j] = arr[j+1]; // 데이터 교체
                arr[j+1] = temp;
                fin = false;    // 만약 교환이 이루어지면 false
            }
        }
        if(fin) break; // 교환이 이루어지지 않았다하면 true로 들어와 반복문 종료 !
    }
    return arr;
}
```

이것으로 버블정렬과 버블정렬을 최적화한 코드까지 공부해보았다.

다음에는 선택정렬이라는 정렬 방법에 대해서 알아봐야겠다. (๑˃̵ᴗ˂̵)ﻭ