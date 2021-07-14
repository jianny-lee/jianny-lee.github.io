---
layout: post
title: "[ 파이썬 문법 ] Print 함수의 이해"
date: 2021-07-14
categories: algorithm
tags: python
comments: true
---

현재 패스트캠퍼스에서 코딩 완주반(파이썬)을 듣는 중인데 항상 파이썬은 문법을 차근차근 공부 하기보다는  
당장 닥친 프로젝트(단편적 예로 자연어 처리,,,ㅎ)가 생기면 구글링 해가면서 코딩하는 스타일이었다.  
이번에 수업을 들으면서 파이썬 문법도 정리할 겸 파이썬 문법 정리 시작.  
###### 알고 있는 것도 아예 모른다는 생각으로 기초부터 듣는 중^^,,,
  
### 파이썬 기초 코딩
### print 구문의 이해
  
* 기본출력
```python
print('hello python!')
print("Hello python!")
print("""Hello Python!""")
```
  
* Seperator 옵션 사용
##### 안에 있는 값으로 문자열을 연결해줌
```python
print('T','E','S','T',sep='')
print('2019','02','19',sep='-')
print('niceman','google.com',sep='@')
```
  
* end 옵션 사용
```python
print('Welcom To',end='')
print('the black paradise',end='')
print('piano notes')
```
  
* format 사용 [],{},()

```python
print('{} and {}'.format('You','Me'))
print("{0} and {1} and {0}".format('You','Me'))
print("{a} are {b}".format(a='You',b='Me'))

print("%s's favorite number is %d" % ('Jian',7)) #$s:문자, %d:정수, %f:실수

print("Test1: %5d, Price: %4.2f" % (776, 6534.123))
print("Test1: {0: 5d}, Price: {1:4.2f}".format(776,6534.123))
print("Test1: {a: 5d}, Price: {b:4.2f}".format(a=776, b=6534.123))

print("'you'")
print('\'you\'')
print('"you"')
print("""'you'""")
print('\\you\\')
```
  
* 파이썬 기본 인코딩
```python
print(sys.stdin.encoding)
print(sys.stdout.encoding)
```
  
* 출력문
```python
print('My name is Kong!')
```
  
* 변수 선언
```python
myName = 'Goodboy'
```
  
* 조건문
```python
if myName == "Goodboy":
    print('Ok')
```
  
* 반복문  
```python
for i in range(1,10):
    for j in range(1,10):
        print('%d * %d = '%(i,j),i*j)
```
  
* 함수선언

```python
def hello():
    print("Hello Pycham")

hello()
```
  
* 클래스  
```python
class Cookie:
    pass
```
  
* 객체 생성

```python
cookie = Cookie()

print(id(cookie))
print(dir(cookie))
```