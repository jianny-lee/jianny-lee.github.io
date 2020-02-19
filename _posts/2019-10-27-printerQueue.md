---
layout: post
title: "1966번 프린터큐"
date: 2019-10-27
categories: study
tags: algorithm
comments: true
---

### **2019.10.27 Sun**
#### 이번에 풀은 문제
<img width="1200" alt="printQueue" src="https://user-images.githubusercontent.com/56791347/67636670-514b5900-f916-11e9-9f41-b777252c38b3.png">

~~~ cpp
#include <iostream>
#include <queue>

using namespace std;

queue < pair <int,int> > q; //큐 q
priority_queue<int> pq; //우선순위 큐 pq
int N,M;
int result[100];

int printQueue(int a){
    int count = 0;
    if(N ==1) count = 1;
    else {
        while(!q.empty()){
            if(pq.top()!=q.front().second){ //pq에 넣은 weight와 q에 넣은 weight의 값이 다르면
                pair <int,int> tmp = q.front(); //q의 가장 앞 정수를 tmp에 넣기
                q.pop();
                q.push(tmp);

            } else { //pq의 weight와 q의 weight가 같을때
                if(M == q.front().first){ //M과 q에 넣은 weight의 위치 값이 같으면 인쇄
                    count++;
                    break;
                }else{
                    count++;
                    pq.pop();
                    q.pop();
                }
            }
        }
    }
    result[a] = count;
    return result[a];
}
int main(){
    int test_case;
    cin >> test_case;

    for(int i=0;i<test_case;i++){
        cin >> N >> M;

        //weight값 넣고 queue에 값 넣음
        for(int j=0;j<N;j++){
            int weight;
            cin >> weight;
            q.push(pair<int,int>(j,weight)); //weight와 위치(j)를 같이 push
            pq.push(weight);

        }
        printQueue(i);

        //queue 초기화
        while(!q.empty()&&!pq.empty()){
            q.pop();
            pq.pop();
        }
    }

    for(int i=0;i<test_case;i++)
        cout << result[i] << endl;

    return 0;
}
~~~
#### 매번 c로만 queue 코드를 작성하다가 c++ 공부 시작하면서 처음 작성해본 cpp queue인데 여러가지 시행착오도 있었고 구글링도 있었지만 발전하는 과정이라고 생각한다.
#### 다음에는 작성할 때 좀 더 코드줄을 줄이는게 목표

### *코드 작성하며 굿노트에 적었던 생각의 흐름*
![note_1966](https://user-images.githubusercontent.com/56791347/67636777-51982400-f917-11e9-816c-12e58d6e946a.png)
#### 예전에는 이렇게 안 적고 무작정 코드 작성하기로 달려들었는데, 나는 그렇게 하다보니 더 체계가 안잡혀있어서
#### 더 코드가 작성 안되고 이상한 늪으로 빠지는 기분이 많았다. 그래서 처음 코드 작성할때는 문제의 요점을 이해하고 코드를 작성하려고 함
