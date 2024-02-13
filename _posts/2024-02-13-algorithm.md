---
layout: single
title:  "코딩 테스트를 위한 파이썬 문법-알고리즘"
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
##########
# 알고리즘 #
##########
```


```python
#  matrix 90 회적
def rotate_a_matrix_by_90_degress(a):
    r_length = len(a)
    c_length = len(a[0])

    # matrix replica set
    res = [[0] * r_length for _ in range(c_length)]
    
    for r in range(r_length):
        for c in range(c_length):
            print("r,c:", r, ",", c)
            res[c][r_length-1-r] = a[r][c]
    print(res)
    return res

matrix= [[1,2,3], [4,5,6],[7,8,9]]

print(rotate_a_matrix_by_90_degress(matrix));
```

    r,c: 0 , 0
    r,c: 0 , 1
    r,c: 0 , 2
    r,c: 1 , 0
    r,c: 1 , 1
    r,c: 1 , 2
    r,c: 2 , 0
    r,c: 2 , 1
    r,c: 2 , 2
    [[7, 4, 1], [8, 5, 2], [9, 6, 3]]
    [[7, 4, 1], [8, 5, 2], [9, 6, 3]]



```python
# 소수 판별
def is_prime_number(x):
    # 2부터 (x-1)까지의 모든 수를 확인
    for i in range(2, x):
        # x가 해당 수로 나누어 떨어질 때
        if x % i == 0:
            return False
    return True

print(is_prime_number(4))
print(is_prime_number(7))

# 개선된 소수 판별
def is_prime_number(x):
    # 2부터 (x-1)까지의 모든 수를 확인
    for i in range(2, int(math.sqrt(x))+1):
        # x가 해당 수로 나누어 떨어질 때
        if x % i == 0:
            return False
    return True

print(is_prime_number(4))
print(is_prime_number(7))
```

    False
    True
    False
    True



```python
# 에라토스테네스의 체
# 2배수,3배수 4배수를 제거하여 여러 소수를 식별
import math

n = 1000
array = [True for i in range(n+1)] # 초기 0~1001 전체 true 세팅 

for i in range(2, int(math.sqrt(n)) +1): #2~32 for문 수행
    if array[i] == True: 
        j = 2
        while i * j <= n:
            array[i*j] = False
            j += 1

for i in range(2, n + 1):
    if array[i]:
        print(i, end=' ')
```

    2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 101 103 107 109 113 127 131 137 139 149 151 157 163 167 173 179 181 191 193 197 199 211 223 227 229 233 239 241 251 257 263 269 271 277 281 283 293 307 311 313 317 331 337 347 349 353 359 367 373 379 383 389 397 401 409 419 421 431 433 439 443 449 457 461 463 467 479 487 491 499 503 509 521 523 541 547 557 563 569 571 577 587 593 599 601 607 613 617 619 631 641 643 647 653 659 661 673 677 683 691 701 709 719 727 733 739 743 751 757 761 769 773 787 797 809 811 821 823 827 829 839 853 857 859 863 877 881 883 887 907 911 919 929 937 941 947 953 967 971 977 983 991 997 


```python
# 투 포인터
# 특정한 합을 가지는 부분 연속 수열찾기 문제에 유용하다.
# 투 포인터는 음수 데이터가 포함되어 있는 경우 해결할 수 없다.
n = 5 # 데이터의 개수
m = 5 # 찾고자 하는 부분합
data = [1,2,3,2,5]

count = 0
interval_sum = 0
end = 0

# start를 차례대로 증가시키며 반복
for start in range(n): # 0~5까지 수행
    # end를 가능한 만큼 이동시키기
    while interval_sum < m and end < n:
        interval_sum += data[end]
        print("a:",data[end])
        print("interval_sum:",interval_sum)
        end += 1
    # 부분합이 m일 때 카운트 증가
    if interval_sum == m:
        
        count += 1
    interval_sum -= data[start]

print()
print("답:",count)
```

    a: 1
    interval_sum: 1
    a: 2
    interval_sum: 3
    a: 3
    interval_sum: 6
    a: 2
    interval_sum: 5
    a: 5
    interval_sum: 7
    
    답: 3



```python
# 투 포인트 - 두 리스트의 합집합
# 사전에 정렬된 리스트 A와 B 선언
n, m = 3, 4
a = [1, 3, 5]
b = [2, 4, 6, 8]

# 리스트 A와 B의 모든 원소를 담을 수 있는 크기의 결과 리스트 초기화
result = [0] * (n + m)
i = 0
j = 0
k = 0

# 모든 원소가 결과 리스트에 담길 때까지 반복
while i < n or j < m:
    # 리스트 B의 모든 원소가 처리되었거나, 리스트 A의 원소가 더 작을 때
    if j >= m or (i < n and a[i] <= b[j]):
        # 리스트 A의 원소를 결과 리스트로 옮기기
        result[k] = a[i]
        print("a:",result)
        i += 1
    # 리스트 A의 모든 원소가 처리되었거나, 리스트 B의 원소가 더 작을 때
    else:
        # 리스트 B의 원소를 결과 리스트로 옮기기
        result[k] = b[j]
        print("b:",result)
        j += 1
    k += 1

# 결과 리스트 출력
for i in result:
    print(i, end=' ')

```

    a: [1, 0, 0, 0, 0, 0, 0]
    b: [1, 2, 0, 0, 0, 0, 0]
    a: [1, 2, 3, 0, 0, 0, 0]
    b: [1, 2, 3, 4, 0, 0, 0]
    a: [1, 2, 3, 4, 5, 0, 0]
    b: [1, 2, 3, 4, 5, 6, 0]
    b: [1, 2, 3, 4, 5, 6, 8]
    1 2 3 4 5 6 8 


```python
# 구간합 튜닝: 
  # 구간별 중간 합 리스트 생성 for문 리소스 감소
# 데이터의 개수 N과 전체 데이터 선언
n = 5
data = [10, 20, 30, 40, 50]

# 접두사 합(Prefix Sum) 배열 계산
sum_value = 0
prefix_sum = [0]
for i in data:
    sum_value += i
    prefix_sum.append(sum_value)

print(prefix_sum)
# 구간 합 계산 (세 번째 수부터 네 번째 수까지)
left = 3
right = 4
print(prefix_sum[right] - prefix_sum[left - 1])
```

    [0, 10, 30, 60, 100, 150]
    70



```python
# 순열과 조합, 경우의 수 구하는 방법
import itertools

data = [1, 2, 3]

# 순열
print("순열:")
for x in itertools.permutations(data, 2):
    print(list(x), end=' ')
print()
print('------------')

# 조합
print("조합:")
for x in itertools.combinations(data, 2):
    print(list(x), end=' ')
```

    순열:
    [1, 2] [1, 3] [2, 1] [2, 3] [3, 1] [3, 2] 
    ------------
    조합:
    [1, 2] [1, 3] [2, 3] 
