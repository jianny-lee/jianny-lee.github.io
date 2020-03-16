---
layout: post
title: "[ 프로그래머스 ] 문자열 내 p와 y의 개수 (연습문제)"
date: 2020-03-16
categories: study
tags: algorithm
comments: true
---

**코드**
```cpp
#include <string>
#include <iostream>
using namespace std;

bool solution(string s)
{
    bool answer = true;
    int size = s.size();
    int pNum = 0;
    int yNum = 0;
    
    //s에서 p와 y의 개수 모으기
    for(int i=0;i<size;i++){
        if(s[i]=='p'||s[i]=='P')
            pNum++;
        else if(s[i]=='y'||s[i]=='Y')
            yNum++;
    }
    
    //두개의 개수 비교
    if(pNum==yNum)
        answer = true;
    else
        answer = false;

    return answer;
}
```

<img width="813" alt="스크린샷 2020-03-16 21 19 33" src="https://user-images.githubusercontent.com/56791347/76757883-d5ba4d80-67cb-11ea-8fd4-e865f91e9453.png">
