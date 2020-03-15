---
layout: post
title: "[ 프로그래머스 ] 가운데 글자 가져오기 (연습문제)"
date: 2020-03-15
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

string solution(string s) {
    string answers;
    
    int length = s.size(); //s의 길이 구하기
    
    //짝수, 홀수에 따라서 s를 answers에 추가
    if(length%2==0){
        answers+=s[length/2-1];
        answers+=s[length/2];
    } 
    if (length%2==1){
        answers+=s[length/2];
    }
    
    return answers;
}
```

비교적 쉬웠던 알고리즘 문제. 생각을 조금만 한다면 금방 풀 수 있다.
5분만에 풀었다 헤헤
<img width="814" alt="스크린샷 2020-03-15 12 23 15" src="https://user-images.githubusercontent.com/56791347/76694569-c053ff00-66b7-11ea-9798-0a424160529c.png">
