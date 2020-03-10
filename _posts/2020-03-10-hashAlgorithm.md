---
layout: post
title: "[ 프로그래머스 ] 완주하지 못한 선수(해시)"
date: 2020-03-10
categories: study
tags: algorithm
comments: true
---

~~~ cpp
#include <algorithm>
#include <string>
#include <vector>

using namespace std;

string solution(vector<string> participant, vector<string> completion) {
    string answer = "";
    sort(participant.begin(), participant.end());
    sort(completion.begin(), completion.end());
    
    int num = 0;
    
    for(int i = 0; i < participant.size(); i++){
        if(participant[i] != completion[i])
            return participant[i];
    }
    
    return answer;
}
~~~

여기서 가장 주목해서 생각해야 할 부분은 먼저 해시의 데이터를 sort하는 것. sort만 하면, 나머지 부분들은 쉽게 해결할 수 있었다.
