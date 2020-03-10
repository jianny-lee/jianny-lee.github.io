---
layout: post
title: "[ 프로그래머스 ] 완주하지 못한 선수(해시)"
date: 2020-03-11
categories: study
tags: algorithm
comments: true
---

**기댓값이 다르게 나온 코드**

``` cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    std::vector<int> answer;
    std::vector<int> tmp;
    int num = commands.size(); //commands[num][?]
    
    for(int s = 0;s<num;s++){
        int i = commands[s][0] - 1;
        int j = commands[s][1] - 1;
        int k = commands[s][2] - 1;
        
        for(int p = i;p<j;p++){
            tmp.push_back(array[p]);
        }
        std::sort(tmp.begin(),tmp.end());
        answer.push_back(tmp[k]);
    }
    return answer;
}
```
<img width="827" alt="스크린샷 2020-03-11 05 02 01" src="https://user-images.githubusercontent.com/56791347/76354241-7389c480-6355-11ea-8f09-b7b7a7c09257.png">

이러한 오류가 발생하여서 구글링을 해보니, `answer.push_back(tmp[k])` 의 다음 줄에 `tmp.clear()`를 추가해줘야한다.


**올바른 코드**

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    std::vector<int> answer;
    std::vector<int> tmp;
    int num = commands.size(); //commands[num][?]
    
    for(int s = 0;s<num;s++){
        int i = commands[s][0] - 1;
        int j = commands[s][1];
        int k = commands[s][2] - 1;
        
        for(int p = i;p<j;p++){
            tmp.push_back(array[p]);
        }
        std::sort(tmp.begin(),tmp.end());
        answer.push_back(tmp[k]);
        tmp.clear();
    }
    return answer;
}
```
