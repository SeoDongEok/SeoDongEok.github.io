---
layout: single
title:  "코딩 테스트를 위한 파이썬 문법-수 자료형"
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
#############
## 수 자료형 ##
#############
```

```python
######################
# 정수형
a=1000 #양수
b=-7   #음수
print(a,b)
```

    1000 -7



```python
######################
# 실수형
a=157.83  # 양의 실수
b=-324.23 # 음의 실수
c=5. # 소수가 0이면 생략
d=.12 # 정수가 0이면 생략
print(a,b,c,d)
```

    157.83 -324.23 5.0 0.12



```python
######################
# 지수표현
# 10억 지수표현
a = 1e9     #1000000000.0
b = 75.25e1 #752.5
c = 3954e-3 #3.954
print(a,b,c)
```

    1000000000.0 752.5 3.954



```python
######################
# 연산
a = 0.3 + 0.6
print(a)

if a == 0.9:
    print(True)
else:
    print(False)

# 실수형은 값 비교 시 주의 필요
a = round(a,4)
print(a)

if a == 0.9:
    print(True)
else:
    print(False)

a=7
b=3
print(a/b) # 나누기
print(a%b) # 나머지
print(a//b) # 몫
print( a**b) # 제곱
```

    0.8999999999999999
    False
    0.9
    True
    2.3333333333333335
    1
    2
    343



```python
######################
# 리스트 자료형
a = [1,2,3,4,5,6]
print(a)

# 인덱스 4 색인
print(a[4])

# 생성자
a = list()
a.append(1)
print(a)

# 초기화
a = []

# 1차원 리스트 초기화
a=[0]*10
print(a)
```

    [1, 2, 3, 4, 5, 6]
    5
    [1]
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]



```python
######################
# 리스트 자료 색인
a = [1,2,3,4,5,6]

# 뒤 첫번째
print(a[-1])

# 인덱스 편집
a[2] = 8
print(a)

# 인덱스 레인지 조회
print(a[2:4])
```

    6
    [1, 2, 8, 4, 5, 6]
    [8, 4]



```python
######################
# 조건 리스트 생성자
# 0~20 중 홀수 리스트 생성
array = [i for i in range(20) if i % 2 == 1]
print('홀수:', array)

# 0~20 중 짝수 리스트 생성
array = []
for i in range(20):
    if i % 2 == 0:
        array.append(i)
print('짝수:', array)

# 오름차순
array.sort()
print('오름:', array)

# 내림차순
array.sort(reverse=True)
print('내림:', array)

# 역순
array.reverse()
print('역순:', array)

# 인덱스 데이터 헨들링
array.insert(2,11)
array.insert(2,11)
print('index 2 added 11', array)

# 데이터 count
print('11 count:', array.count(11))

# 데이터 제거 한개만.
array.remove(11)
print('removed:', array)
```

    홀수: [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
    짝수: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
    오름: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
    내림: [18, 16, 14, 12, 10, 8, 6, 4, 2, 0]
    역순: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
    index 2 added 11 [0, 2, 11, 11, 4, 6, 8, 10, 12, 14, 16, 18]
    11 count: 2
    removed: [0, 2, 11, 4, 6, 8, 10, 12, 14, 16, 18]

```python
######################
# not in 필터
a =[1,2,3,4,5,5,5]
remove_set={3,5}
result = [i for i in a if i not in remove_set]
print(result)
```

    [1, 2, 4]