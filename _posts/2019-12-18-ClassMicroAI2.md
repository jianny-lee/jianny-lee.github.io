---
layout: post
title: "[Class] Micro - AI 특강 2일차"
date: 2019-12-18
categories: study
tags: class, ai, machinelearning, deeplearning, microAI
comments: true
---

### [ Radio ]
- Power Level이 높을수록 신호가 멀리 수송 가능함
- channel을 맞춰서 송신하면 메시지를 받을 수 있음

```python
from microbit import *
import radio
radio.on()
radio.config(channel=48) # Choose your own channel number
radio.config(power=7) # Turn the signal up to full strength
message_to_master = "dokylee and jianny"
# Event loop.
while True:
    radio.send(message_to_master)
    incoming = radio.receive()
    if incoming is not None:
        display.show(incoming)
        print(incoming)
	  sleep(500)
```

-> 이 방식은 와이파이를 사용한 것이 아님. wi-fi는 ip를 사용함 / 우리가 사용한 것은 radio로 채널 중심

```python
#버튼에 따른 microbit의 display에 대한 코드
from microbit import *
import love
while True:
    if button_a.is_pressed():
        love.badaboom()
    elif button_b.is_pressed():
        display.show(Image.HAPPY)
    else:
        display.show(Image.GHOST)
    sleep(100)
```

$$ python에서 pass란 + No Operation + $$
$$ while True 란 Repeat forever $$
$$ list는 값이 변하는 List `list = {11,22,3}` $$

```python
from microbit import *
high_scores = [25, 20, 10, 15, 30] # Create a list and store some values in
print(high_scores[0]) # Print 25 print(high_scores[3]) 
total_score = 0
for score in high_scores: # For each element ...
    total_score = total_score + score
print(total_score)
average = total_score / len(high_scores)
print(average)
```

$$ Tuples는 값이 변하지 않는 상태의 lists 저장할 때 `tuples = (11,2,3)`$$
$$ set은 순서가 없이 저장됨 -> 집합은 중복을 허용하지 않음$$

---

### [Function]
-> 중복을 피하기 위해서 사용함
: function을 사용하려고 할 때는 `def functionName() :`이라고 선언해줘야 함

---

### [ Classes and Objects ]
-> object = instance, 메모리에 저장됨
-> Object는 메모리내에서 추가 가능

```python
class Player():
    total_count = 0
    
    def __init__(self, name):
        self.name = name
        self.score = 0
        self.total_count += 1
    
    def update_score(self, score):
        self.score = score
    
    def change_name(self, name):
        self.name = name
        
# Create an instance of an object of class Player
player_1 = Player("teapot418")
player_2 = Player("r00t")
# Change value of score of player_1
player_1.update_score(40)
# Change value of name of player_1
player_2.change_name("bott0m")

print(player_1.name)
print(player_1.score)
print(player_1.total_count)

print(player_2.name)
print(player_2.score)
print(player_2.total_count)
```

**self란?**
: 메모리 내에 있는 자기 자신을 가리키는 의미로 , 나열이 포함되어있는 것들
-> instance 내에 있는 것으로 self라고 지칭을 함

---

아두이노 내에서
파일 -> 환경설정 -> 추가적인 보드 매니저에 [https://sandeepmistry.github.io/arduino-nRF5/package_nRF5_boards_index.json](https://sandeepmistry.github.io/arduino-nRF5/package_nRF5_boards_index.json) 추가

microbit의 cpu는 다르기 때문에, 맞는 compiler를 다운받아서 보드 매니저로 설정해줘야 함
![01-2](https://user-images.githubusercontent.com/56791347/71094252-03542280-21ee-11ea-92e1-1b32cdbbd59e.PNG)


참고문헌
UCL BBC micro:bit MicroPython Tutorial