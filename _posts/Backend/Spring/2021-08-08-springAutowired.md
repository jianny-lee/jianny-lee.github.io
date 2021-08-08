---
layout: post
title: "[Spring] @Autowired"
date: 2021-08-08
categories: backend
tags: spring
comments: true
---

> 인프런에 게시 되어있는 "스프링 핵심 원리-기본편" 수업을 기본으로 작성된 게시물  

* @Autowired  
    - 의존관계 자동으로 주입해주는 기능  
    - 생성자에 지정하면, 스프링 컨테이너가 자동으로 해당 스프링 빈을 찾아서 주입해줌 -> 근데, 생성자가 딱 1개 있으면 생략해도 자동으로 주입 됨(스프링 빈에만 해당)
    - 기본 조회 전략 : 타입이 같은 빈을 찾아서 주입  
        - 타입(Type)으로 조회하기 때문에 getBean([classname].class)과 유사한 방식으로 동작  
    - ```required = false```을 옆에 입력하면, 자동 주입할 대상이 없을 때 수정자 메서드 자체가 호출 안됨  