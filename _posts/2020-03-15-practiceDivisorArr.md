---
layout: post
title: "[ 프로그래머스 ] 나누어 떨어지는 숫자 배열 (연습문제)"
date: 2020-03-15
categories: study
tags: algorithm
comments: true
---

**코드**
```cpp
#include <string>
#include <vector>
#include <algorithm> //sort를 사용하기 위해 추가

using namespace std;

vector<int> solution(vector<int> arr, int divisor) {
    vector<int> answer;
    int size = arr.size();
    
    for(int i=0;i<size;i++){
        if(arr[i]%divisor==0){ //나누어 떨어지는 값일 경우
            answer.push_back(arr[i]);
        }else if (arr[i]%divisor!=0){ //나누어 떨어지는 값이 아닐 경우
            continue;
        }
    }
    
    if(answer.size()==0){ //나누어 떨어지는 값이 하나도 없는 경우
        answer.push_back(-1);
    }
    sort(answer.begin(),answer.end()); //오름차순으로 정렬
    
    return answer;
}
```

<img width="819" alt="스크린샷 2020-03-15 12 57 08" src="https://user-images.githubusercontent.com/56791347/76694955-7c172d80-66bc-11ea-90f6-774e0102cef6.png">
