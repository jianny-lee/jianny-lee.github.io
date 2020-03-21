---
layout: post
title: "[ 프로그래머스 ] 하샤드 수 (연습문제)"
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

bool solution(int x) {
    bool answer = false;
    vector<int> arr;
    
    int pushNum,divisor=0,tmpNum = x;
    
    //각 자릿수의 숫자들을 vector에 입력
    while(true){
        if(tmpNum/10==0){
            pushNum = tmpNum;
            arr.push_back(tmpNum);
            break;
        } else {
            pushNum = tmpNum%10;
            tmpNum = tmpNum/10;
            arr.push_back(pushNum);
        }
    }
    
    //자릿수 합 구하기
    for(int i=0;i<arr.size();i++){
        divisor += arr[i];
    }
    
    //하샤드 수인지 판별
    if(x%divisor==0){
        answer = true;
    } else {
        answer = false;
    }
    return answer;
}
```

<img width="474" alt="스크린샷 2020-03-21 09 24 45" src="https://user-images.githubusercontent.com/56791347/77215119-cfbec680-6b55-11ea-8974-9cf9926fc1a7.png">
