---
layout: post
title: "[Study] Grammar : 배열과 반복문"
date: 2019-12-16
categories: study
tags: ios
comments: true
---

# Swift ) 배열과 반복문
### **2019.12.16 Mon** 
## 배열

> 배열을 선언하는 두가지 방법

``` swift
// 초기값을 대입하여 선언하는 방법
var color: [String] = ["red","yellow","blue"]
var value: [Int] = [255, 27,273]

// 빈 배열 선언 후 append method를 사용하여 배열 값 추가
var color = [String]()
var value = [Ing]()

color.append(“red”)
color.append(“yellow”)
color.append(“blue”)

value.append(24)
value.append(4)
Value.append(15)
```

> 선언한 배열을 참조하는 방법

``` swift
var color: [String] = ["red","yellow","blue"]
var value: [Int] = [255, 27,273]

color[1] = “pink”
value[2] = 0
var someVal = value[1]

print(“color = “,color)
print(“value = “,value)
print(“some Value = “,someVal)

// result
// color = [“red”, “pink”, “blue”]
// value = [255, 27, 0]
// some Value = 27
```


## 반복문
* for loop

``` swift
for Value in Range {
	[ Code ]
}

//example
for i in 1…9 {
	print(“number of i: \(i)”)
```

* while loop

``` swift
while condition { //condition이 false가 될 때 까지 구문 반복
	[ Code ]
}
```
