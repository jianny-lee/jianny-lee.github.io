---
layout: post
title: "[ 프로그래머스 ] 자연수 뒤집어 배열로 만들기 (연습문제)"
date: 2020-03-20
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

vector<int> solution(long long n) {
    vector<int> answer;
    
    long long tmpNum = n;
    long long pushNum;
    
    while(true){
        int tmpNum2;
        if(tmpNum / 10 == 0){
            pushNum = tmpNum;
            answer.push_back(pushNum);
            break;
        } else {
            pushNum = tmpNum % 10; //나머지
            tmpNum /= 10;
            answer.push_back(pushNum);
        }
    }
    return answer;
}
```

<img width="581" alt="스크린샷 2020-03-20 21 03 42" src="https://user-images.githubusercontent.com/56791347/77161998-49bb6500-6aee-11ea-85fe-51e8a57c2b07.png">

변수를 선언할때, parameter의 변수인`long long`으로 선언하는 것 잊지말기.
처음에 int로 했다가 분명 테스트에서는 맞는데 왜 안되지? 해서 보니까 내가 변수들을 int로 선언했다는 걸 깨달았다.
