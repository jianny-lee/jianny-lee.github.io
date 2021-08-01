---
layout: post
title: "[Spring] 스프링 컨테이너"
date: 2021-08-01
categories: backend
tags: spring
comments: true
---
> 인프런에 게시 되어있는 "스프링 핵심 원리-기본편" 수업을 기본으로 작성된 게시물  

* 스프링 컨테이너  
    - 생성하기
        ```java
        ApplicationContext applicationContext = new AnnotationConfigApplicationContext(AppConfig.class);
        ```
        - **ApplicationContext**를 스프링 컨테이너라고 함
        - **ApplicationContext**는 인터페이스!
        - 스프링 컨테이너는 XML 기반으로 만들 수도 있으며, Annotation 기반의 자반 설정 클래스로도 만들 수 있음

        <img width="648" alt="스크린샷 2021-08-01 오후 8 28 55" src="https://user-images.githubusercontent.com/56791347/127769212-3c685319-6b88-41b3-a307-fb40320763f4.png">

    - 스프링 빈 등록하기
        <img width="635" alt="스크린샷 2021-08-01 오후 8 29 08" src="https://user-images.githubusercontent.com/56791347/127769222-a4ff9c15-91ff-41ff-9518-aacbbb1019f2.png">