---
layout: post
title: "[ 프로그래머스 ] 정수 제곱근 판별 (연습문제)"
date: 2020-03-23
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <cmath>
#include <iostream>

using namespace std;

long long solution(long long n) {
    long long answer = 0;
    double tmpNum = sqrt(n);
    
    if(tmpNum-(int)tmpNum == 0){ //tmpNum을 형변환 하면 몫만 남을테니,
        tmpNum += 1;             //이 값을 빼줬을 때에 대해 판별
        answer = pow(tmpNum,2);
    }else{
        answer = -1;
    }
    
    return answer;
}
```

<img width="603" alt="스크린샷 2020-03-23 20 05 27" src="https://user-images.githubusercontent.com/56791347/77310416-a5c9f780-6d41-11ea-9108-428dadceadab.png">
