---
layout: post
title: "[ 프로그래머스 ] 콜라츠 추측 (연습문제)"
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

int solution(int num) {
    int answer = 0;
    long long tmpNum = num;
    long long count = 0;
    
    if(num == 1){
        return answer;
    }
    while(true){
        if(tmpNum%2==0){ //even
            tmpNum/=2;
            count++;
            if(tmpNum == 1 && count <= 500) {
                answer = count;
                break;
            } else if(tmpNum!=1&&count >=500){
                answer = -1;
                break;
            }
        } else if(tmpNum%2!=0.0){ //odd
            tmpNum = tmpNum*3 + 1;
            count++;
            if(tmpNum == 1 && count <= 500) {
                answer = count;
                break;
            } else if (tmpNum!=1&&count >= 500){
                answer = -1;
                break;
            }
        }
    }
    
    return answer;
}
```

<img width="578" alt="스크린샷 2020-03-21 09 14 43" src="https://user-images.githubusercontent.com/56791347/77214863-68544700-6b54-11ea-8508-caf47176eacc.png">

여기서 함정은 반복적으로 계산하는 tmpNum의 변수형이 관건이었다.
int로만 계산을 하다보면, 나중에 출력이 될 때 충분한 값이 들어가지 못하여 값이 이상하게 되는 경우가 있기에, byte를 많이 할당 가능한 long long으로 설정했다.
그러면 금방 쉽게 풀리는 문제
