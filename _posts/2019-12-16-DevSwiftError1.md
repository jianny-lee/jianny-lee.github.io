---
layout: post
title: "[Error] : this class is not key value coding-compliant for the key 에러 발생시"
date: 2019-12-16
categories: study
tags: ios
comments: true
---

Info.plist의 파일을 다 수정한 이후에도 계속 *this class is not key value coding-compliant for the key*라는 오류가 떠서 outlet이 연결된 것이나 action 연결들을 보니 flexible space bar button item들이 들어있는 상위 카테고리의 toolBar를 아웃렛 변수로 추가해서 Run을 했을 때 꼬여서 그런 것 같다. 
개발 하면서 library에 있는 것들을 실수로 연결해놓고 삭제를 안해서 이런 연결 문제가 생긴듯.
앞으로는 이런 실수는 하지 말도록 주의할 것!

<img width="261" alt="스크린샷 2019-12-16 18 36 26" src="https://user-images.githubusercontent.com/56791347/70896117-782f2d00-2033-11ea-9e7b-156e9ad5cb34.png">

>>>> referencing Outlet 부분에 추가되었던 두개의 연결이 오류의 원인이었음 