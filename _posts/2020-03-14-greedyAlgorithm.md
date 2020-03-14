---
layout: post
title: "[ 백준알고리즘 ] ATM (그리드 알고리즘)"
date: 2020-03-14
categories: study
tags: algorithm
comments: true
---

*코드*

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main(){
    int n;
    int total = 0;
    cin >> n;

    vector<int> person;
    vector<int> time;

    for(int i=0;i<n;i++){
        int pushNum;
        cin >> pushNum;
        person.push_back(pushNum);
    }

    sort(person.begin(),person.end()); //오름차순 순으로 정렬
    
    for(int i=0;i<n;i++){
        if(i == 0){
            time.push_back(person[0]);
        } else {
            int tmpTime = time[i-1] + person[i];
            time.push_back(tmpTime);
        }
    }
    
    for(int i=0;i<n;i++){
        total += time[i];
    }
    
    cout << total << endl;
    return 0;
}
```
