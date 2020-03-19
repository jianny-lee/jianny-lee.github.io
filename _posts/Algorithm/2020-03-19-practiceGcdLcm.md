---
layout: post
title: "[ 프로그래머스 ] 최대공약수와 최소공배수 (연습문제)"
date: 2020-03-19
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <vector>

using namespace std;

vector<int> solution(int n, int m) {
    vector<int> answer;
    int a = n,b = m;
    
    while(true){
        if(b == 0){
            int multi1 = n / a;
            int multi2 = m / a;
            answer.push_back(a);
            answer.push_back(multi1*multi2*a);
            break;
        } else {
            int tmp = a;
            a = b;
            b = tmp % b;
        }
    }
    
    return answer;
}
```

<img width="711" alt="스크린샷 2020-03-19 18 45 25" src="https://user-images.githubusercontent.com/56791347/77053506-cd535400-6a11-11ea-91b7-c4cabc897eae.png">

요즘 알고리즘 수업시간에 배운 Euclid's method가 나와서 덕분에 쉽게 이해하고 풀을 수 있었던 문제.
