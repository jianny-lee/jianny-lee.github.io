---
layout: post
title: "[Spring] AppConfig"
date: 2021-08-01
categories: backend
tags: spring
comments: true
---

> 인프런에 게시 되어있는 "스프링 핵심 원리-기본편" 수업을 기본으로 작성된 게시물  

* AppConfig
    - 애플리케이션의 전체 동작 방식을 구성(config)하기 위해, **구현 객체를 생성**하고, **연결**하는 책임을 가지는 별도의 설정 클래스
    - 애플리케이션의 실제 동작에 필요한 **구현 객체를 생성**함
        - ex) MemberServiceImpl.class, MemoryMemberRepository.class, OrderServiceImpl.class, FixDiscountPolicy.class
    - 생성한 객체 인스턴스의 참조(레퍼런스)를 **생성자를 통해서 주입(연결)**해준다.
        - ex) 
            ```java 
            //MemberServiceImpl는 이제부터 의존관계는 신경쓰지 말고, 실행만 집중!
            public class MemberServiceImpl implements MemberService {
                private final MemberRepository memberRepository;
                
                public MemberServiceImpl(MemberRepository memberRepository) {
                    this.memberRepository = memberRepository;
                }
                public void join(Member member) {
                    memberRepository.save(member);
                }
                public Member findMember(Long memberId) {
                    return memberRepository.findById(memberId);
                } 
            }
            ```

    - 리팩터링
        - 구성 정보에서 역할과 구현을 명확하게 분리!
        - 역할이 잘 드러나게!
        - 중복은 제거!!!