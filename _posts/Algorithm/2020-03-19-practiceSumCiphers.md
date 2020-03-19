---
layout: post
title: "[ 프로그래머스 ] 자릿수 더하기 (연습문제)"
date: 2020-03-19
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <iostream>
#include <vector>

using namespace std;
int solution(int n)
{
    int answer = 0;
    vector<int> sumArr;
    int tmpN = n, tmp1, tmp2;
    
    while(true){
        if(tmpN/10 == 0){ //제일 큰 자리수의 값 넣기
            sumArr.push_back(tmpN%10);
            break;
        } else { //큰 자리수를 제외한 값들을 벡터에 넣기
            tmp1 = tmpN / 10;
            tmp2 = tmpN % 10;
            sumArr.push_back(tmp2);
            tmpN = tmp1;
        }
    }
    
    for(int i=0;i<sumArr.size();i++){
        answer += sumArr[i];
    }

    return answer;
}
```

<img width="757" alt="스크린샷 2020-03-19 19 07 47" src="https://user-images.githubusercontent.com/56791347/77055841-ed384700-6a14-11ea-8a3b-f60e124948cf.png">

문제를 먼저 봤을때, 주어지는 N이 세자리수인가? 하고 생각했는데 엄청나게 크길래 이걸 어떻게 처리할지 먼저 고민했다. 
그러다가 10으로 나누었을 때 나머지는 먼저 지정한 벡터 변수에 push하고 몫을 10으로 나누고,,, 
뭐 이런걸 계속 반복해서 마지막에 10으로 나누었을 때 몫이 0이 되면 나머지를 넣고 break를 하도록 코드를 작성하니 한번에 완료.
