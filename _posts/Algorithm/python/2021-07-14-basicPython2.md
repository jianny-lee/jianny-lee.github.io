---
layout: post
title: "[ 파이썬 문법 ] 파이썬의 자료형-1"
date: 2021-07-14
categories: algorithm
tags: python
comments: true
---

이번에 이어질 두개의 포스팅은 파이썬의 자료형에 대해서 간단하게 소개할 것이다.  
  
* 데이터 타입  

```python  
v_str1 = "Niceman"
v_bool = True
v_str2 = "Goodboy"
v_float = 10.3
v_int = 7
v_dict = {
    "name" : "Lee",
    "age" : 26
}

v_list = [3,5,7]
v_tuple = 3,5,7
v_set = {7,8,9}

print(type(v_tuple))
print(type(v_set))
print(type(v_float))

i1 = 39
i2 = 939
big_int1 = 9999999999999999999999999999999999999
big_int2 = 8887787878878887777777777777777778888
f1 = 1.234
f2 = 3.784
f3 = .5
f4 = 10.

print(i1 * i2)
print(big_int1*big_int2)
print(f1**f2)
print(f3+i2)

result = f3 + i2
print(result, type(result))

a = 5.
b = 4
c = 10

print(type(a), type(b))
result2 = a+b
print(result2)
```  
  
  
* 형변환  
> int, float, complex(복소수)  

```python
print(int(result2))
print(float(c))
print(complex(3))
print(int(True))
print(int(False))
print(int('3'))
print(complex(False))

y = 100
y *= 100
print(y)
```
  
* 수치 연산 함수  

```python
print(abs(-7))
n,m = divmod(100,8) #몫과 나머지 구해주는 것
print(n,m)

import math

print(math.ceil(5.1))
print(math.floor(3.874))
```

 [문자열]  

> 문자열, 문자열연산, 슬라이싱  

```python
str1 = "I am Girl."
str2 = 'NiceMan'
str3 = ''
str4 = str() #공백

print(len(str1),len(str2),len(str3),len(str4))

escape_str1 = "Do you have a \"big collection\""
print(escape_str1)

escape_str2 = "Tab\tTab\tTat"
print(escape_str2)
```
  
* Raw String  
```python
raw_s1 = r'C:\Programs\Test\Bin'
print(raw_s1)
raw_s2 = r"\\a\\a"
print(raw_s2)
```   
   
* 멀티라인  
```python
multi = \
    """
    문자열 
    
    멀티라인 
    
    테스트
    """
print(multi)
```
  
*  문자열 연산  

```python  
str_o1 = '*'
str_o2 = 'abc'
str_o3 = "def"
str_o4 = "Niceman"

print(str_o1*100)
print(str_o2+str_o3)
print(str_o1*3)
print('a' in str_o4)
print('f' in str_o4)
print('z' not in str_o4)
```
  
* 문자열 형 변환  

```python  
print(str(77)+'a')
print(str(10.4))
``` 
  
* 문자열 함수  

~~~python  
a = 'niceman'
b = 'orange'

print(a.islower())
print(b.endswith('e'))
print(a.capitalize())
print(a.replace('nice','good'))
print(list(reversed(b)))  
~~~

* 문자열 슬라이싱  

```python
a = 'niceman'
b = 'orange'
  
print(a[0:3])
print(a[0:4])
print(a[0:len(a)])
print(a[:])
print(b[0:4:2])
print(b[1:-2])
print(b[::-1])  
```