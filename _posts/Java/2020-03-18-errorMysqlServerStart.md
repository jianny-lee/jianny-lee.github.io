---
layout: post
title: "[Error/BackEnd(mySQL)] The server quit without updating PID file"
date: 2020-03-18
categories: study
tags: java
comments: true
---

요즘 **백엔드 공부**를 시작했다.
근데 mysql을 다운하려는데, 자꾸 같은 오류가 나서 구글링하다가 나중에 또 같은 오류가 날 것 같아서 작성하는 글

<img width="650" alt="스크린샷 2020-03-18 16 10 58" src="https://user-images.githubusercontent.com/56791347/76965742-29619e00-6968-11ea-9541-553d46214844.png">

자꾸 이런 오류가 나면서 당최 감을 잡지 못했다. 
그러다가 스크린샷에 있는 경로의 *.err 파일을 보면 뭔가 풀릴까 싶어서 들어가봤다

<img width="1121" alt="스크린샷 2020-03-18 16 11 28" src="https://user-images.githubusercontent.com/56791347/76965751-2e265200-6968-11ea-8dae-309a768c2e77.png">

에러 파일의 로그를 들여다보니 'Address already in use'를 보았다.
처음에 딱 보자마자 ‘엥? 내가 언제 mysql 포트를 썼다고???' 라고 생각했는데, 과거를 생각해보니 저번에 node.js랑 mysql 연동해서 웹사이트 만든다고 했던게 생각났다.
그때 공부할때 쓰고선 mysql을 종료를 안했던 것 같았다. 그래서 이미 사용중인 port를 정지 시키고 다시 사용하고자 했다.

<img width="649" alt="스크린샷 2020-03-18 16 11 48" src="https://user-images.githubusercontent.com/56791347/76965761-31214280-6968-11ea-9460-f1b3fd50bd04.png">

`isof -i: 3306`으로 저 포트를 사용중인 PID를 찾고자 했다.
그러고선 `kill -9 PID_NUM` 을 사용해서 포트를 죽여버렸다. ㅎㅎ;;

<img width="448" alt="스크린샷 2020-03-18 16 12 09" src="https://user-images.githubusercontent.com/56791347/76965763-32eb0600-6968-11ea-8a99-7ebdfe9d725d.png">

그러고선 다시 `mysql.server start`를 사용하니 잘 된다!
만약에 이러한 오류가 생기면, 먼저 에러 로그를 읽어보고선 **어디에서 오류가 난건지 분석하고 해결하려는 습관 들이기!!!**
