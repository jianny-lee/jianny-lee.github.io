---
layout: post
title: "[ 프로그래머스 ] 핸드폰 번호 가리기 (연습문제)"
date: 2020-03-20
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string phone_number) {
    string answer = "";
    int size = phone_number.size();
    
    for(int i=0;i<size-4;i++){
        answer += "*";
    }
    for(int i=size-4;i<size;i++){
        answer+=phone_number[i];
    }
    return answer;
}
```

<img width="594" alt="스크린샷 2020-03-20 21 22 50" src="https://user-images.githubusercontent.com/56791347/77163219-f565b480-6af0-11ea-9975-5e739849e611.png">
