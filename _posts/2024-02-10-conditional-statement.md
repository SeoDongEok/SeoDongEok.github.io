---
layout: single
title:  "코딩 테스트를 위한 파이썬 문법-조건문, 비교,논리 연산자"
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
########
# 조건문 #
########
```


```python
x = 15
if x >= 17:
    print('조건1:', x)
elif x >= 15:
    print('조건2:', x)
else:
    print('조건3:', x)
```

    조건2: 15



```python
# 비교연산자
x=1
y=2

if x==y:
    print('x와 y는 같다')
elif x!=y:
    print('x와 y는 다르다')
elif x>y:
    print('x가 y보다 크다')
elif x<y:
    print('x가 y보다 작다')
elif x>=y:
    print('x가 y보다 크거나 같다')

# 논리연산자
if x<y and x!=y:
    print('조건1과 조건2가 True')

if 0 < x < 2:
    print('0과 2사이')

if x<y or x!=y:
    print('조건1 또는 조건2가 True')

if not x>y:
    print('조건1이 거짓이면 True')
    

a=[1,2,3,4,5]
remove_set={3,5}

result=[]
for i in a:
    if i not in remove_set:
        result.append(i)

print(result)
```

    x와 y는 다르다
    조건1과 조건2가 True
    0과 2사이
    조건1 또는 조건2가 True
    조건1이 거짓이면 True
    [1, 2, 4]
