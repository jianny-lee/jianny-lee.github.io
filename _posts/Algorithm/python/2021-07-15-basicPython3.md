---
layout: post
title: "[ 파이썬 문법 ] 파이썬의 자료형-2"
date: 2021-07-14
categories: algorithm
tags: python
comments: true
---

## 파이썬 데이터 타입(자료형)
  
#### 리스트(순서o, 중복o, 수정o, 삭제o)  
```python
a = []
b = list()
c = [1,2,3,4]
d = [10, 100, 'Pen', 'Banana', 'Orange']
e = [10, 100, ['Pen', 'Banana', 'Orange']]
```
  
* 인덱싱  
```python
print(d[3])
print(d[-3])
print(d[0]+d[1])
print(e[2][1])
print(e[-1][-2])
```
  
* 슬라이싱  
```python
print(d[0:3])
print(d[0:1])
print(d[0:2])
print(e[2][1:3])
```  
  
* 연산  
```python
print(c+d)
print(c*3)
print(str(c[0])+'hi')
```
  

*  리스트 수정, 삭제   
  
```python
c[0] = 77
print(c)

c[1:2] = [100, 1000, 10000]
print(c)
c[1] = ['a','b','c']
print(c)

del c[1] #인덱스가 있는 것을 삭제
print(c)
del c[-1]
print(c)
```
  

* 리스트 함수  
~~~python
y = [5,2,3,1,4]
print(y)
y.append(6)
print(y)
y.sort()
print(y)
y.reverse()
print(y)
y.insert(2, 7)
print(y)
y.remove(2) #내가 원하는 값을 삭제
print(y)
y.pop()
print(y) #LIFO
ex = [88,77]
y.extend(ex)
print(y)
~~~
  

* 삭제 : del, remove pop  
  

#### 튜플 (순서 o, 중복 o, 수정x, 삭제x)  
```python
a=()
b=(1,)
c=(1,2,3,4)
d=(10,100, ('a','b','c'))

print(c[2])
print(c[3])
print(d[2][2])

print(d[2:])
print(d[2][0:2])

print(c+d)
print(c*3)
print()
print()
```
  

* 튜플 함수  

~~~python
z = (5,2,1,3,4)

print(z)
print(3 in z)
print(z.index(5))
print(z.count(1))
~~~
  

#### 딕셔너리(Dictionary) : 순서x, 중복 x, 수정o, 삭제o  
  
* Key, Value(Json) ->MongoDB  
* 선언  
  
~~~python
a = {'name': 'Kim', 'Phone':'010-4443-9304', 'birth':960907}
b = {0: 'hello python', 1:'hello coding'}
c = {'arr': [1,2,3,4,5]}
~~~
  

* 출력  

~~~python
print(a['name'])
print(a.get('name'))
print(a.get('address'))
print(c.get('arr')[1:3])
~~~
  

* 딕셔너리 추가
~~~python
a['address'] = 'Seoul'
print(a)
a['rank'] = [1,2,3]
a['rank2'] = (1,2,3,)
print(a)
~~~
    
     
* keys, values, items  

~~~python
print(a.keys())

temp = list(a.keys())
print(temp[1:3])

print(a.values())
print(list(a.values()))

print(list(a.items()))
print(1 in b)

print('name2' not in a)
~~~
  
  
#### 집합(Sets) (순서x, 중복x)  
~~~python
a = set()
b = set([1,2,3,4])
c = set([1,4,5,6,6])

print(type(a))
print(c)

t = tuple(b)
print(t)
l = list(b)
print(l)

print()
print()

s1 = set([1,2,3,4,5,6])
s2 = set([4,5,6,7,8,9])

print(s1.intersection(s2)) #교집합
print(s1 & s2)

print(s1 | s2)
print(s1.union(s2)) #합집합

print(s1 - s2)
print(s1.difference(s2))
~~~
  

* 추가&제거  
  
~~~python  
s3 = set([7,8,10,15])  
s3.add(18)  
s3.add(7)  
print(s3)  

s3.remove(15)  
print(s3)  

print(type(s3))  
~~~