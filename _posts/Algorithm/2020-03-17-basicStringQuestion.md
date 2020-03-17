---
layout: post
title: "[ 프로그래머스 ] 문자열 다루기 기본 (연습문제)"
date: 2020-03-17
categories: study
tags: algorithm
comments: true
---

**코드**

```cpp
#include <string>

using namespace std;

bool solution(string s) {
    bool answer = true;
    
    if(s.size()==4 || s.size()==6){ //문자열이 4 혹은 6일때
        for(int i=0;i<s.size();i++){ //숫자로 구성되어 있는지 판단
            if(s[i] >= '0' && s[i] <= '9'){
                continue;
            } else if(s[i] >= 'a' && s[i] <= 'z' || s[i] >= 'A' && s[i] <= 'Z'){
                answer = false;
            }
        }
    } else { //문자열이 4 혹은 6이 아닐경우
        answer = false;
    }
    
    return answer;
}
```

<img width="811" alt="스크린샷 2020-03-17 14 39 40" src="https://user-images.githubusercontent.com/56791347/76825386-26c65200-685d-11ea-93c5-545c646b5353.png">

분명 알고리즘을 제대로 작성한 것 같은데, 코드를 채점하고 제출하니 87.5의 정확도가 나오며 두개가 자꾸 실패를 했다.
뭐가 잘못되었나 다시 문제를 읽어보니, ~**‘문자열 s의 길이가 4 혹은 6이고’**~ 를 간과하고 있었다….주륵,,,,

그래서 문자열의 길이를 확인하는 코드를 추가하니, 한번에 해결되었다.
이번 문제를 풀면서, 문제에서 제시한 요구사항들이 무엇인지에 대해서 놓치지 말고 꼼꼼히 봐야한다고 생각했다….
