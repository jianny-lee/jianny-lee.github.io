---
layout: post
title: "[ 프로그래머스 ] 같은 숫자는 싫어 (연습문제)"
date: 2020-03-15
categories: study
tags: algorithm
comments: true
---

**코드**
```cpp
#include <vector>
#include <iostream>

using namespace std;

vector<int> solution(vector<int> arr) 
{
    vector<int> answer;
    int size;
    int tmpInt;
    
    size = arr.size();
    for(int i=0;i<size;i++){
        tmpInt = arr[i]; //비교하기 위해서 tmpInt에 i 위치의 숫자를 넣기
        if(tmpInt!=arr[i+1]){ //연속적으로 나타나는 숫자가 아닐경우
            answer.push_back(tmpInt); //answer 벡터에 입력
            tmpInt=arr[i+1]; //연속적으로 나타나는게 아닌 숫자로 tmpInt를 변경
        }else if(tmpInt==arr[i+1]){ //연속적으로 나타나는 숫자일 경우
            continue;
            i++;
        }
    }
    
    return answer;
}
```

이것도 비교적 쉬웠던 문제. 처음에는 살짝 방법을 꼬아서 생각하다가 단순하게 생각하자! 하고선 코딩하니 성공했다.
<img width="807" alt="스크린샷 2020-03-15 12 46 56" src="https://user-images.githubusercontent.com/56791347/76694825-0fe7fa00-66bb-11ea-9f1c-47342e25e034.png">
<img width="812" alt="스크린샷 2020-03-15 12 47 08" src="https://user-images.githubusercontent.com/56791347/76694827-170f0800-66bb-11ea-9eaf-5098b8589b69.png">
