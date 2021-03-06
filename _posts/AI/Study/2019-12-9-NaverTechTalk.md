---
layout: post
title: "NAVER AI techTalk"
date: 2019-12-09
categories: study
tags: machinelearning
comments: true
---

[ 네이버 검색과 인공지능 기술 ]
## *네이버*
#### -> 다양한 인터넷 서비스의 집합
#### -> 이러한 서비스의 특징은, 네이버 안팎의 다양한 컨텐츠 검색이 가능하게 함

### * 검색의 특징
#### 	* 통합검색 (상당부분은 네이버 안에서 검색을 이루어지고, 이후에는 외부의 사이트에서도 검색 이용 가능)
#### * 연구 개발 미션 -> 사용자의 검색 의도에 맞춰 컨텐츠에 점수 부여

### >>>> AI <<<<<
#### 현재 네이버와 구글의 경우에는 검색에서 Deep learning이 아닌 ML을 많이 사용하고 있음

#### *Supervised learning* 
#### : 사용자 의도에 맞는 컨텐츠와 맞지 않는 컨텐츠를 구분하는 알고리즘을 자동으로 만들자

#### 검색 서비스 개발 과정
#### 1. 가이드라인에 따른 기계학습용 학습데이터 구축
##### 	1. 어떻게하면 좋은 검색결과를 도출할까? -> 네이버의 경우, 연관검색어를 참고하여 사용자들이 어떤 정보를 얻고자 검색을 진행하였는지 유추할 수 있음
##### 	2. 검색평가 가이드라인을 세우기 -> 각 정보에 따른 점수들을 부여함
##### 	3. 가이드라인에 따른 평가를 함
##### 	4. 학습용 데이터 집합
#### 2. 기계학습알고리즘을 이용하여 검색랭킹모듈을 학습
##### 	1. 검색은 아직 딥러닝보다는 머신러닝을 주로 이용하는 중
##### 	2. 데이터와 엔지니어들의 feature 발굴 —> 학습데이터에 저런 데이터들이 전부 다 들어가서 학습됨 —> 그에 따라 새로운 모델이 발굴 —> online test —> 서비스적용여부 판단 [ 기계 학습을 이용한 Feature의 발굴]
##### 		> 문서의 의도와 정확성
##### 		> semi-supervised learning
##### 		> 딥러닝 기술 일부 활용 (OCR, ocr과 음성인식 기술을 이용하여 동영상에서 			얼마나 품질이 좋은지를 평가 등)

###### [ 네이버 검색 블로그에서 현재 어떤 기술을 이용하고 있는지 볼 수 있음 ]


## POI Recommendation System
#### AirSPACE - >recommendation을 하는 부서
#### * 네이버의 각종 장소 검색, POI별 데이터랩, Smart Around

### Smart Around Service (주력 기술인듯)
#### * 개인화된 맞춤형 장소 추천 -> 주변 즐길거리도 추천
#### * location에 대한 기술, POI, User에 대한 기술이 필요

### 위치를 이해하는 장소 추천
#### 	사용자 주변의 업체 분포를 고려한 추천 반경 자동설정 -> 위치반경에서 사용자가 어떻게 장소를 이동할 수 있는지에 따라서 위치반경의 범위도 달라짐
### POI를 이해하는 장소 추천
#### 	리뷰, 검색, 클릭을 요약하는 인공지능
#### 	LSTM(테마와 관련하여 어떤 정보들이 드러나는지를 이용)과 CNN(사진을 인식하는데 특화된 기술->테마 키워드를 뽑아내는데 주로 사용)을 이용
#### 	Statistical Model -> 연령대, 시간대, 성비별 인기도에 따라서도 사용자들에게 정보를 제공

### Understanding Users (개인의 성향에 따른 추천이 필요함)
#### Co-Factor(MF모델) -> serendipity
#### POI2Vec(DNN) -> user coverage
#### Sttistical Model(통계모델), LC(DNN)

#### cofactor : factorization Meets the item embedding
#### poi2vec : embedding- based model  -> word2vec을 이용하여 정보를 추출

## 검색과 플랫폼 (System & Solution)
### 직접적으로 AI를 사용하지는 않는 곳. 근데 실제적인 관점에서 연구를 하는 곳
### 주로 실제적인 것에 관련된 것들을 많이 사용함
### 인플루언서 검색

#### 어떻게하면 사용자에게 깔끔하고 확실한 정보를 제공할 수 있는지에 대한
#### 일종의 탱커같은 팀,,,,, 이슈가 나왔을 때 가장 먼저 트래픽이 갑자기 변할 때 확장성에 대한 연구도 진행하는 팀임 (DevOps)
#### 엔진 -> 60억 문서 대상으로 빠른 색인, 평균 7ms의 검색(카페)에 응답을 하고있는데, 이러한 시간을 더 줄이는 것을 목표로 함
#### 대용량 트래픽의 분산 시스템 -> 서버도 많고! 데이터도 많다!!!!! 으악
#### ==> 그래서 많은 데이터(big data)와 GPGPU가 필요함.
#### 따라서 플랫폼이 중요하다는 결론을 내림
#### Data store에서 사용자에게 언제든지 필요한 정보를 제공하고자 함 따라서 이러한 서버를 관리하고 그러는 것도 AI에서 중요한부분이라고 생각함

### Hadoop
#### * ai 모델 개발 및 적용을 위한 플랫폼 (AI SUITE : End-to-end AI Platform)
#### * serving architecture continued
#### 	* 카테고리 매칭을 이용 ( 브랜드 같은 경우는 쉽게 나눌 수 있는데, 수제 물품이라던지 그런건 나누기가 힘들어서 치마나 원피스 등과 같은 것들로 나눌 수 있음)
#### * 검색서비스를 위한 플랫폼
#### 	* CLOUS 

#### [ DEVIEW 컨퍼런스 자료들을 찾아보고 그러기]

## NAVER LABS
### 다양한 기술들을 연구하는 조직 -> 개인적으로 굉장히 흥미로운 조직이라고 생각함
### >> 네이버의 온라인 서비스를 오프라인으로 연결하고자 하는게 Mission

### [ Indoor ]
###  *indoor Mapping* 
#### : 3D의 지도를 제공하여 여러가지 AR 네비게이션 등을 제공할 수 있는 기술, 3d rider와 고해상도 카메라 등을 갖고있는 로봇(M1) 이 자동으로 구석구석 장소 데이터를 얻어서 그 데이터를 이용하여 지도를 만들고 등고선 같은 3D map을 얻을 수 있음
### Visual Localization
#### : 지도상에서 어디에 위치해있는지에 대한 데이터를 제공해줌
### indoor AR Navigation
#### : 이러한 visual localization에서 받은 데이터를 이용하여 indoor ar navigation 서비스를 얻을 수 있음 -> 이 기술은 앞에서 설명한 POI 기술을 온라인에서 오프라인으로 가져온 것 이라고 생각함
### Around G (Autonomous Guide Robot)
### Self-Updating Map
#### : 지도에서 지속적으로 변하는 가게들의 정보를 로봇이 자동으로 돌아다니면서 정보를 제공하여 자동적으로 지도를 업데이트 해줌

### [ Outdoor ]
### Autonomous Driving
#### : 자율주행에서는 사방이 다 뚫려있어야 하기때문에 sensor coverage가 매우 중요
### ADAS Functions
### Outdoor Mapping
#### : indoor mapping보다 훨씬 더 어려운 기술, 자율주행 자동차가 안전하게 목적지에 도착하기 위해서 필요한 정보
##### -> map을 제작시에 사용하는 *R1 mapping 장비*를 이용하여 데이터를 수집함, 전방향이 잘 보이게 차 위에 설치를 해서 정보를 얻기 가능
##### -> ACROSS : 클라우드에 데이터를 지속적으로 업데이트하는 기술 

#### [ 기타 ]
#### AMBIDEX
##### : 이 로봇은 머리는 없는데, 이러한 머리에 들어가는 정보들을 클라우드에 올리자! 라는 아이디어를 사용 -> 5G Brainless Robot Platform을 이용 

#### [ Vision ]
#### A-CIty : 로봇과 사람이 친밀하게 지내는 세상을 향해 달려가는 중

#### >>>> 만약 지원하고자 한다면 recruit.naverlap.com

#### 네이버는 기술 플랫폼 회사로 발전하고자 함
#### 네이버로 오시면! 
#### * 빅데이터는 다 내꾸양 >_<
#### * 내 손끝에서 탄생한 service. 굉장히 파급력이 큰 서비스를 제공 가능함
#### * 유럽이나 일본에서 종사 가능

#### 인재상
#### * 뛰어난 개발 역량 보유
#### * 글로벌 사용자에게 제공할 새롭고 혁신적인 기술과 서비스를 만들고 싶은 분
#### * 새로운 기술을 배우는것에 즐거움을 느끼고, 포기안하는 사람
#### * 다양한 사람들과 communication하면서 team player를 하는 사람
