---
layout: post
title: "[Spring] 스프링의 라이브러리 가볍게 살펴보기"
date: 2021-07-22
categories: backend
tags: spring
comments: true
---

* 스프링이란   
    - 자바빈(POJO)를 사용해서 할 수 있도록 하면서도 EJB에서만 가능했던 많은 일을 가능하도록 지원   
    - EJB를 사용할 때 알아야했던 수많은 디자인 패턴을 신경 쓰지 않아도 됨   
  

#### [ 라이브러리 살펴보기 ]    
* 스프링부트 라이브러리  
> Gradle은 의존 관계가 있는 라이브러리를 함께 다운로드함  
 - spring-boot-starter-web  

        |   
        |------- spring-boot-starter-tomcat : 톰캣(웹서버)   
        |------- spring-webmvc : 스프링 웹 MVC   
 - spring-boot-starter-thymeleaf : 타임리프 템플릿 엔진(View)  
 - spring-boot-starter(공통) : 스프링부트 + 스프링코어 + 로깅  

        |  
        |------- spring-boot   
                |--------- spring-core  
        |------- spring-boot-starter-logging  
                |--------- logback, slf4j  

* 테스트 라이브러리  

 - spring-boot-starter-test  

            |------- junit: 테스트 프레임워크  
            |------- mockito: 목 라이브러리  
            |------- assertj: 테스트 코드를 좀 더 편하게 작성하게 도와주는 라이브러리  
            |------- spring-test: 스프링 통합 테스트 지원  

* Thymeleaf 템플릿 엔진 동작
    - 웹 환경과 비웹 환경 모두에서 작동할 수 있는 Java XML/XHTML/HTML5 템플릿 엔진
    - 동작 환경 그림(출처 : 인프런 스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술)
    <img width="602" alt="스크린샷 2021-07-25 오후 6 42 48" src="https://user-images.githubusercontent.com/56791347/126894815-66fb0ba5-6aee-43c7-81a0-c6ede66e030f.png">
