---
layout: post
title: "[ 프로그래머스 ] x만큼 간격이 있는 n개의 숫자 (연습문제)"
date: 2020-03-21
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <vector>

using namespace std;

vector<long long> solution(int x, int n) {
    vector<long long> answer;
    long long pushNum = x;
    
    answer.push_back(pushNum);
    for(int i=1;i<n;i++){
        pushNum = pushNum + x;
        answer.push_back(pushNum);
    }
    return answer;
}
```

<img width="590" alt="스크린샷 2020-03-21 09 47 57" src="https://user-images.githubusercontent.com/56791347/77215710-0cd88800-6b59-11ea-94b3-755c38084abe.png">
