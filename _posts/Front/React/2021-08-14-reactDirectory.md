---
layout: post
title: "[React] React 디렉토리 파일"
date: 2021-08-14
categories: front
tags: react
comments: true
---

> 리액트 프로젝트 디렉토리의 파일

<img width="305" alt="스크린샷 2021-08-14 오후 11 29 56" src="https://user-images.githubusercontent.com/56791347/129449628-1a09da53-3dfa-489c-bc8f-4e68dddd2e36.png">

* node_modules Directory
    - 리액트 앱이 가지고 있는 의존성 라이브러리 파일들

* public
    - static 파일

* src
    - **소스코드** 작성하는 디렉토리
        - App.js : public/index.html에 렌더링할 내용 기술하는 곳
        - index.js : App.js에 작성된 내용을 public/index.html의 특정 dom(id='root')에 매핑 시켜줌

* package.json
    - 리액트의 버전, 의존성등이 기재되어 있는 파일.
    - 패키지 추가시, 추가한 패키지의 내용이 이곳에 기재됨
    - **spring boot와 연동하기 위한 proxy 설정을 이곳에서 함**