---
layout: post
title: "[ 프로그래머스 ] 서울에서 김서방 찾기 (연습문제)"
date: 2020-03-16
categories: study
tags: algorithm
comments: true
---

**코드**
```cpp
#include <string>
#include <vector>

using namespace std;

string solution(vector<string> seoul) {
    string answer = "";
    string answer1 = "김서방은 ";
    string answer2 = "에 있다";
    string locationNum;
    int size = seoul.size();
    
    for(int i=0;i<size;i++){
        if(seoul[i]=="Kim")
            locationNum = to_string(i);
    }
    answer += answer1;
    answer += locationNum;
    answer += answer2;
    return answer;
}
```
<img width="812" alt="스크린샷 2020-03-16 21 40 31" src="https://user-images.githubusercontent.com/56791347/76759315-c4267500-67ce-11ea-96ca-9064b803f19a.png">
