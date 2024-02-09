---
layout: single
title:  "코딩 테스트를 위한 파이썬 문법-문자, 튜플 자료형"
categories: coding-test
tag: [python]
toc: true
author_profile: false
sidebar:
  nav: "coding-test"
search: true
typora-root-url: ../
---

```python
##############
# 문자열 자료형 #
##############

# Python 문법 중에서 문자 자료형에 관한 실습과정이다.
```


```python
# 생성 및 초기회
data = 'hello World'
print(data)

data = 'reset String'
print(data)
```

    hello World
    reset String



```python
# 문자열 연상
ㄱ = 'hello'
ㄴ = 'World'
print(ㄱ + " " +ㄴ) # append

print(ㄱ * 3) # 문자열 곱하기도 가능함.

a ="012345"
# 문자열을 인덱스 형태로 추출도 가능함.
# index 2에서 시작하여 4 이전까지의 문자열 추출
print(a[2:4]) 
```

    hello World
    hellohellohello
    23



```python
#############
# 튜플 자료형  #
#############

# 튜플은 한 번 저장된 값을 변경할 수 없다.
# 자료형태는 () 소괄호를 사용한다.
# 알고리즘을 구현하는 과정에서 변경하지 말아야 값이 오류나 버그로 인해 변경되지 못하도록 사용할 수 있다.
```


```python
a=(0,1,2,3,4,5)
print(a)

a[2] =7
```

    (0, 1, 2, 3, 4, 5)



    ---------------------------------------------------------------------------
    
    TypeError                                 Traceback (most recent call last)
    
    Cell In[13], line 4
          1 a=(0,1,2,3,4,5)
          2 print(a)
    ----> 4 a[2] =7


    TypeError: 'tuple' object does not support item assignment



```python

```


```python

```
