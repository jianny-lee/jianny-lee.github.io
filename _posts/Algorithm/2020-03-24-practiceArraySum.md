---
layout: post
title: "[ 프로그래머스 ] 행렬의 덧셈 (연습문제)"
date: 2020-03-24
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <vector>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> arr1, vector<vector<int>> arr2) {
    vector<vector<int>> answer;
    vector<int> sumArr;
    int pushNum;
    
    for(int i=0;i<arr1.size();i++){ // 행
        for(int j=0;j<arr1[i].size();j++){ // 열
            pushNum = arr1[i][j] + arr2[i][j];
            if(pushNum < 500){
                sumArr.push_back(pushNum);
            }
            
        }
        answer.push_back(sumArr);
        sumArr.clear();
    }
    return answer;
}
```

<img width="685" alt="스크린샷 2020-03-24 18 28 53" src="https://user-images.githubusercontent.com/56791347/77409861-521ce400-6dfd-11ea-8105-a99e64a50e1d.png">

`vector<vector<int>>`라고 선언된 변수는 2차원 배열이라고 생각하고 풀면 편함!
