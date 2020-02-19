---
layout: post
title: "[Class] Micro - AI 특강 1일차"
date: 2019-12-17
categories: study
tags: machinelearning
comments: true
---


## Day 1
Natural Intelligence <-> Artificial Intelligence
* AI 란?
	* Editor(HTML, Browser 등), Complier(C,java등), Interpreter(python 등)이 있는데, 이 모든 것들의 상위계층은 다 tool / software
* Micro - AI란
	* 작은 hw에 AI를 접목 시키는 것을 /*Micro - AI*/라고 함
	* 적용 언어 : *C , C++ , python* , java , Node.js  -> 언어들을 사용하여 작은 hw에 적용하기 위함
	* tinyBASIC , microPython

### ::Microbit::
: microsoft가 아이들의 교육을 위해 만든 것
: python editor를 갖고 있음 -> microbit hardware 전용임. 
> microbit 사이트의 에디터에서 download -> ~.hex 파일 다운로드. -> microbit에 Import 해줘야함
![01](https://user-images.githubusercontent.com/56791347/70998135-ea7a3d00-2119-11ea-8ee6-d96631feee61.PNG)
![02](https://user-images.githubusercontent.com/56791347/70998136-eb12d380-2119-11ea-88aa-c24537d6ac3d.PNG)
![03](https://user-images.githubusercontent.com/56791347/70998137-eb12d380-2119-11ea-93ec-4c06eedac11f.PNG)
 #### microbit는 usb memory 자체로 usb처럼 사용도 가능

 ```python
print("지안 jianny")
print("ㅠ     ㅠ")
print(" 오     언")
print("늘     제 ")
print(" 수     끝")
print("업     나")

from math import *
print(sin(8))
 ```
 ![IMG_1837](https://user-images.githubusercontent.com/56791347/70999062-041c8400-211c-11ea-89be-3c2392e299a9.jpeg)

* ::Thonny:: 
: python이 내장되어 있음
REPL mode
Tools -> options -> interprets -> micropython(BBC micro:bit) -> port setting -> ok
> Shell 
Microbit 내에서 python이 실행 중
Script 부분에서 micro:bit에 저장시, 파일 이름을 main으로 저장하면 main이 우선 실행됨

```python
from microbit import *

while True :
#이 부분을 indentation이라 함
	display.scroll(‘Jianny’)
	display.show(Image.HEART)
	sleep(2000)
```

* Tera Term
	* Tera Term을 사용하려면, Thonny에서 disconnect 해주고 /setup -> Serial port 로 들어가서 setting/

``` python
from math import * #메모리 과다 사용 방지, 내가 원하는 것을 사용 가능
print(sin(9))
```

	* math : class라고 생각하면 됨
		* class 내에 function(method)가 들어가있음


## Basic Functions

```python
#1. Display a string or an image
from microbit import *
display.show(“Hello”)

#2. Scroll a string
Display.scroll(“Hello”)

#3. clear the display
Display.clear
```

## Advanced Functions

```python
# set a pixel
from microbit import *
display.set_pixel(0,4,9)

display.clear()
for x in range(0, 5):
	for y in range(0,5):
		display.set_pixel(x,y,9)

#위의 for문을 while문으로 변경
i=1
While i < 10:
	j=1
	while < 10:
		print(x,”*”,y,”=“,x*y)
		j = j+1
	i = I+1
```

## DIY images

```python
from microbit import *
boat1 = Image(“05050:”
                “05050:”
                “05050:”
                “99999:”
                “09990”)
boat2 = Image(“05050:”
                “00000:”
                “00000:”
                “00000:”
                “00000:”)
boat3 = Image(“00000:”
                “05050:”
                “00000:”
                “00000:”
                “00000:”)
boat4 = Image(“00000:”
                “00000:”
                “05050:”
                “00000:”
                “00000:”)
boat5 = Image(“00000:”
                “00000:”
                “00000:”
                “99999:”
                “00000:”)
boat6 = Image(“00000:”
                “00000:”
                “00000:”
                “00000:”
                “09990”)

all_boats = [boat1,boat2,boat3,boat4,boat5,boat6]
while True :
        display.show(all_boats,2000)
display.show(boat)
```

## Button

```python

from microbit import *

while True:
#버튼 A를 눌렀을 때 micro pixel에 A가 보여짐
    if button_a.is_pressed():
        display.scroll("A")
#아닐때 하트 모영 show
    else:
        display.show(Image.HEART)
```

```python
#A를 누른 count 횟수 출력
from microbit import *

while True:
    sleep(3000)
    count = button_a.get_presses()
    display.scroll(str(count))
```

```python
from microbit import *

while True:
    if button_a.is_pressed() and button_b.is_pressed():
        display.scroll("AB")
        break
    elif button_a.is_pressed():
        display.scroll("A")
    elif button_b.is_pressed():
        display.scroll("B")
    sleep(100)
#python에서 switch case문은 if,elif를 쓴다
```


### 기울어진 정도를 측정하는 것 (Acceleration measurements)
- Acceleration : 가속도
- syro : 회전량

```python
from microbit import *
while True:
    x = accelerometer.get_x()
    y = accelerometer.get_y()
    z = accelerometer.get_z()
    print("x, y, z:", x, y, z)
    sleep(500)
```

```python
#응용
from microbit import *
while True:
    x = accelerometer.get_x()
    y = accelerometer.get_y()
    z = accelerometer.get_z()
    print("x, y, z:", x, y, z)
    if x > 100:
        display.show(Image.HAPPY)
    elif x < -100:
        display.show(Image.ANGRY)
    sleep(500)
```
![IMG_1838](https://user-images.githubusercontent.com/56791347/70999064-041c8400-211c-11ea-8581-b78cf477a390.jpeg)
![IMG_1839](https://user-images.githubusercontent.com/56791347/70999065-041c8400-211c-11ea-8aee-3644f31bd232.jpeg)

```python
from microbit import *
while True:
    gesture = accelerometer.current_gesture()
    if gesture == "face up":
        display.show(Image.HAPPY)
    else:
        display.show(Image.ANGRY)

```

참고문헌
: UCL BBC micro:bit MicroPython Tutorial