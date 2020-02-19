---
layout: post
title: "[Study] Pytorch : 지도/비지도/강화 학습"
date: 2019-12-15
categories: study
tags: machinelearning
comments: true
---

### **2019.12.15 Sun**

## 특징
> */Define by Run/* 계산 그래프 구축 방법을 이용 -> 동적으로 구성 가능. 하지만 비용이 많이 들음
> *자동미분 가능*


## 관련 라이브러리 목록
> Jupyter, pillow, matplotlib, pandas (데이터 다루는 함수 제공), scikit-learn (머신러닝 관련 함수 제공), konlpy (자연어 처리용 함수 제공) -> konlpy는 다른 라이브러리와 다르게 설치 시 `pip install konlpy` 사용



 [ Machine Learning ]
## * 개념
데이터를 반복적으로 학습해서 데이터에 포함된 패턴을 찾아내는 것.
## * 과정
	
![IMG_E24A6A7BE1E5-1](https://user-images.githubusercontent.com/56791347/70860778-65e8bc80-1f69-11ea-8a39-50b9ef460620.jpeg)


### 1) 지도 학습 (supervised learning)
: 정답을 포함하는 데이터를 학습 데이터로 사용 ( 입력변수 - 목적변수)
* 과정
> 학습 데이터를 훈련 / 테스트 데이터로 분류
> 훈련 데이터로 학습 모형의 결과값 get -> 테스트 데이터에 대한 답 예측 결과값 get
> 테스트 데이터의 *설명변수*와 *목적변수* 비교

![IMG_FA5B3B429F49-1](https://user-images.githubusercontent.com/56791347/70860781-68e3ad00-1f69-11ea-8630-df1287dd5f18.jpeg)



### 2) 비지도 학습 
: 설명변수만으로 구성된 데이터를 학습 데이터로 사용
-> 패턴을 만드는 것이 불가능. 때문에 특징값에 기초하여 직접 패턴과 모형을 만듦
1) 클러스터링 : 데이터를 여러 그룹으로 나누는 것
2) 차원축소 : 데이터를 더 적은 차원으로 요약하는 것


### 3) 강화학습 (reinforcement learning)
: 자가 학습을 통해 처리를 최적화하기 위한 학습
-> 주어진 환경에서 행동을 취하면 관측 결과와 보상을 받으면서 보상을 최대화하는 행동을 학습을 지속적으로 반복하며 *행동 최적화 및 보상 극대화*



참고 문헌
: 코이즈미 사토시, 『pytorch를 활용한 머신러닝,딥러닝 철저 입문』, 심효섭, 위키북스(2018)