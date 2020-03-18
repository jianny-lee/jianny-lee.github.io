---
layout: post
title: "[ 프로그래머스 ] 약수의 합 (연습문제)"
date: 2020-03-17
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <vector>
#include <iostream>

using namespace std;

int solution(int n) {
    int answer = 0;
    vector<int> sumArr;
    int checkNum;
    
    for(int i=1;i<=n;i++){
        for(int j=1;j<=n;j++){
            if(i*j==n) {
                sumArr.push_back(i);
                sumArr.push_back(j);
                break;
            }
        }
    }
    
    for(int i=0;i<sumArr.size()/2;i++){
        answer+=sumArr[i];
    }
    
    return answer;
}
```

<img width="797" alt="스크린샷 2020-03-18 18 01 33" src="https://user-images.githubusercontent.com/56791347/76943342-89dde480-6942-11ea-9616-b6e69725ef25.png">
