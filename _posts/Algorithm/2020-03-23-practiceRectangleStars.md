---
layout: post
title: "[ 프로그래머스 ] 직사각형 별찍기 (연습문제)"
date: 2020-03-23
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <iostream>

using namespace std;

int main(void) {
    int a;
    int b;
    cin >> a >> b;
    
    for(int i=0;i<b;i++){
        for(int j=0;j<a;j++){
            cout<<'*';
        }
        cout<<endl;
    }
    return 0;
}
```

<img width="561" alt="스크린샷 2020-03-23 20 26 46" src="https://user-images.githubusercontent.com/56791347/77312076-9f894a80-6d44-11ea-852a-4dad58587ee2.png">
