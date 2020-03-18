---
layout: post
title: "[ 프로그래머스 ] 평균구하기 (연습문제)"
date: 2020-03-17
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <vector>

using namespace std;

double solution(vector<int> arr) {
    double answer = 0;
    
    for(int i=0;i<arr.size();i++){
        answer += arr[i];
    }
    answer = answer / arr.size();
    return answer;
}
```

<img width="608" alt="스크린샷 2020-03-18 21 44 12" src="https://user-images.githubusercontent.com/56791347/76961929-9d4c7800-6961-11ea-81e0-dea3d54a006f.png">
