---
layout: post
title: "[ 프로그래머스 ] 제일 작은 수 제거하기 (연습문제)"
date: 2020-03-23
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

vector<int> solution(vector<int> arr) {
    vector<int> answer;
    int min = arr[0];
    
    if(arr.size()==1){
        return {-1};
    }
    
    for(int i=1;i<arr.size();i++){ //최솟값 판별
        if(min > arr[i]){
            min = arr[i];
        }
    }
    
    for(int i=0;i<arr.size();i++){
        if(arr[i]!=min){
            answer.push_back(arr[i]);
        } else {
            continue;
        }
    }
    
    return answer;
}
```

<img width="519" alt="스크린샷 2020-03-23 20 15 57" src="https://user-images.githubusercontent.com/56791347/77311266-1cb3c000-6d43-11ea-930e-6f53b446131c.png">
