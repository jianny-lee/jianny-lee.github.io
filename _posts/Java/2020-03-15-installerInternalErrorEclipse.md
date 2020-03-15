---
layout: post
title: "[Error] Registry directory not available(Mac)"
date: 2019-12-15
categories: study
tags: java
comments: true
---

**Registry directory not available**
이클립스를 다시 삭제하려고 하니, 이러한 오류가 뜨면서 설치가 안됐음.
`rm -rf ~/.eclipse ~/.p2`를 사용하여 이클립스에 관련된 것들을 모두 삭제해버리고 설치하니 잘 된다.
내가 보기엔, 기존에 있던 이클립스 관련된 파일들을 제대로 삭제를 안하고 설치하려고 하니 디렉토리가 충돌하여 생기는 문제같다.
