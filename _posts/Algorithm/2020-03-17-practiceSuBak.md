---
layout: post
title: "[ 프로그래머스 ] 수박수박수박수박수박수? (연습문제)"
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

string solution(int n) {
    string answer = "";
    string su = "수";
    string bak = "박";
    
    for(int i=1;i<=n;i++){
        if(i%2!=0){ //홀수
            answer += su;
        }else if(i%2==0){
            answer += bak;
        }
    }
    return answer;
}
```

<img width="805" alt="스크린샷 2020-03-17 15 08 18" src="https://user-images.githubusercontent.com/56791347/76826994-2465f700-6861-11ea-8bd0-891e6ee1cbd5.png">
