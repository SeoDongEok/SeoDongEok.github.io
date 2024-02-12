---
layout: single
title:  "코딩 테스트를 위한 파이썬 문법-표준 라이브러리"
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
###############
# 표준 라이브러리 #
###############

# 특정한 프로그램밍 언어에서 자주 사용되는 코드를 미리 라이브러리형태로 구현함.
# https://docs.python.org/ko/3/library/index.html
```


```python
# sum
r= sum({1,2,3,4})
print("sum:",r)

# min
r= min({2,4,6,4,6,3,2})
print("min:",r)

# max
r= max({2,4,6,4,7,3,10})
print("max:",r)
```

    sum: 10
    min: 2
    max: 10



```python
# eval
r = eval("(1+2)/3")
print("eval:",r)
```

    eval: 1.0



```python
# sort
r= sorted({2,4,6,4,7,3,10})
print("sort:",r)
r= sorted({2,4,6,4,7,3,10}, reverse=True)
print("sort-r:",r)

d= [2,4,6,4,7,3,10]
d.sort()
print(d)

d.sort(reverse=True)
print(d)

r= sorted([('가', 3),('나', 2),('다', 1)], key=lambda x:x[1], reverse=True)
print(r)
```

    sort: [2, 3, 4, 6, 7, 10]
    sort-r: [10, 7, 6, 4, 3, 2]
    [2, 3, 4, 4, 6, 7, 10]
    [10, 7, 6, 4, 4, 3, 2]
    [('다', 1), ('나', 2), ('가', 3)]



```python
# 세자리 경우의 수
from itertools import permutations
d= ["A","B","C"]
r = list(permutations(d,3))
print(r)
print()

# 두자리 경우의 수
from itertools import combinations
r = list(combinations(d,2))
print(r)
print()

# 중복허용 두자리 경우의 수
from itertools import product
r = list(product(d,repeat=2))
print(r)
print()

from itertools import combinations_with_replacement
r = list(combinations_with_replacement(d,2))
print(r)
print()
```

    [('A', 'B', 'C'), ('A', 'C', 'B'), ('B', 'A', 'C'), ('B', 'C', 'A'), ('C', 'A', 'B'), ('C', 'B', 'A')]

    [('A', 'B'), ('A', 'C'), ('B', 'C')]

    [('A', 'A'), ('A', 'B'), ('A', 'C'), ('B', 'A'), ('B', 'B'), ('B', 'C'), ('C', 'A'), ('C', 'B'), ('C', 'C')]

    [('A', 'A'), ('A', 'B'), ('A', 'C'), ('B', 'B'), ('B', 'C'), ('C', 'C')]




```python
# heapq
# heap que 사용
import heapq

def heapsort(iterable):
    h = []
    r = []
    # 모든 원소 차례대로 삽입
    for v in iterable:
        heapq.heappush(h,v)
        print(h)
    print("---------")

    # 차례로 꺼내기
    for i in range(len(h)):
        r.append(heapq.heappop(h))
        print("h:", h)
        print("r:", r)
        print()
    return r

r= heapsort([1,3,5,7,9,2,4,6,8,0])
print(r)
```

    [1]
    [1, 3]
    [1, 3, 5]
    [1, 3, 5, 7]
    [1, 3, 5, 7, 9]
    [1, 3, 2, 7, 9, 5]
    [1, 3, 2, 7, 9, 5, 4]
    [1, 3, 2, 6, 9, 5, 4, 7]
    [1, 3, 2, 6, 9, 5, 4, 7, 8]
    [0, 1, 2, 6, 3, 5, 4, 7, 8, 9]
    ---------
    h: [1, 3, 2, 6, 9, 5, 4, 7, 8]
    r: [0]

    h: [2, 3, 4, 6, 9, 5, 8, 7]
    r: [0, 1]

    h: [3, 6, 4, 7, 9, 5, 8]
    r: [0, 1, 2]

    h: [4, 6, 5, 7, 9, 8]
    r: [0, 1, 2, 3]

    h: [5, 6, 8, 7, 9]
    r: [0, 1, 2, 3, 4]

    h: [6, 7, 8, 9]
    r: [0, 1, 2, 3, 4, 5]

    h: [7, 9, 8]
    r: [0, 1, 2, 3, 4, 5, 6]

    h: [8, 9]
    r: [0, 1, 2, 3, 4, 5, 6, 7]

    h: [9]
    r: [0, 1, 2, 3, 4, 5, 6, 7, 8]

    h: []
    r: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]



```python
# bisect
# 정렬된 배열에서 틀정한 원소를 찾는데 효율적임
from bisect import bisect_left, bisect_right

a = [0,1,2,3,4,5,6,7,8,9]
x = 5

#5인 원소 왼쪽에 넣으려면 인덱스 5번주소
print(bisect_left(a,x))
#5인 원소의 오른쪽에 넣으넣으려면 인덱스 6번주소
print(bisect_right(a,x))
```

    5
    6



```python
#############
# collections
# deque 데이터의 시작과 끝에 데이터를 삽입 삭제에 효율적임
from collections import deque

d= deque([2,3,4])
d.appendleft(1)
d.append(5)

print(d)
print(list(d))
print('-----------')
print()

#############
# Counter 원소의 갯수 리턴
from collections import Counter

counter = Counter(['red','blue','red','green','blue','blue'])

print(counter['blue'])
print(counter['green'])
print(dict(counter))
```

    deque([1, 2, 3, 4, 5])
    [1, 2, 3, 4, 5]
    -----------

    3
    1
    {'red': 2, 'blue': 3, 'green': 1}



```python
########
# math
# 자주 사용되는 수학적인 기능인 팩토리얼, 제곱근, 최대공약수 등을 포함하고 있음

import math

# 팩토리얼 1*2*3*4*5=120
print("팩토리얼:",math.factorial(5))

# 제곱근
print("제곱근:",math.sqrt(4))

# 최대공약수
print("최대공약수:",math.gcd(18,27))

# 원근
print("원근:",math.pi)

# 자연상수
print("자연상수:",math.e)

```

    팩토리얼: 120
    제곱근: 2.0
    최대공약수: 9
    원근: 3.141592653589793
    자연상수: 2.718281828459045