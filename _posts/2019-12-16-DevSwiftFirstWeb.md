---
layout: post
title: "[Swift] 웹 개발 : 앱 시작 시 페이지 보이기"
date: 2019-12-16
categories: dev
tags: ios
comments: true
---


> 지정 웹 페이지 보여 주기
```swift
    func loadWebPage(_ url: String) {
        let myURL = URL(string: url)
        let myRequest = URLRequest(url: myURL!)
        webView.load(myRequest)
    }
```
	* Info.plist 파일 선택
	* Information Property List에 항목 추가
	* App Transport Security Setting 선택
		* App Transport Security Setting에 하위 항목 추가
		* Allow Arbitrary Loads 선택 -> value값을 Yes로 변경