---
layout: post
title: "[ 프로그래머스 ] 정수 내림차순으로 배치하기 (연습문제)"
date: 2020-03-19
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

long long solution(long long n) {
    long long answer = 0;
    long long tmpN = n, tmp1,tmp2;
    long long multiNum = 10;
    vector<int> sumArr;
    
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
    
    sort(sumArr.begin(),sumArr.end()); 
    //오름차순으로 정리하기 (만약에 내림차순으로 하고싶다면)
    //sort(sumArr.begin(),sumArr.end(),greater(int));라고 해도 되지만,
    //여기서 원하는건 vector가 아니라서 오름차순으로 처리함
    
    for(int i=0;i<sumArr.size();i++){
        if(i!=0){
            answer = answer + sumArr[i]*multiNum;
            multiNum *= 10;
        } else {
            answer += sumArr[i];
        }
        
    }
    return answer;
}
```

<img width="620" alt="스크린샷 2020-03-19 19 18 55" src="https://user-images.githubusercontent.com/56791347/77056905-7bf99380-6a16-11ea-984a-47646d2d78f4.png">

문제에서 원하는건 정수를 내림차순으로 배치하는 것이었지만, 나는 vector에 넣고 오름차순으로 먼저 배치했다.
그 다음에 long long으로 return하기위해 vector의 사이즈의 자릿수들 만큼 곱해서 더해주었다.
