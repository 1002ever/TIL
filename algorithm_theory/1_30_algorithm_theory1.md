# 1.30

## 알고리즘 이론 1



- 알고리즘 : 유한한 단계를 거쳐, 문제를 해결하기 위한 절차나 방법

  ​                 => 유한한 자원(시간, 공간)을 통해



- 알고리즘 표현 방법

  ㄱ. 슈더코드     =>    문법 상 올바르지는 않지만, 대략적인 이해 / 정리를 돕기 위한 코드

  ​                         =>    본 코드보다는 간소화 된 꼴이므로, 

  ​                                 프로젝트 시 타인과 소통 도구 / 개발자 스스로 코드 요약본 용도로 유용

  ㄴ. 순서도         =>   (조건에 의한)분기 구분이 명확해짐

  ​                                 딘. 복잡해질 시 순서도로 표현하기에 한계가 있을 수 있음

- 알고리즘 평가 기준

  1. 정확성 2. 작업량 3. 메모리 사용량 4. 단순성 5. 최적성 

     `=> 결과부터 내고, 최적화 할 것`



- 시간 복잡도 => 빅-오 표기법

  \-- O(1)  <  O(log n)  <  O(n)  <  O(n log n)  <  O(n^2)  <  O(2^n)  <  O(n!)



* 배열

  \- 일정한 자료형의 변수들을 하나의 이름으로 열거

  \- C와 JAVA와는 달리 파이썬에서는 여러 타입을 열거 가능, 배열의 길이도 가변 << List >>

​      

   ** 입력을 받아서 리스트를 만드는 코드

            ```python
# 12345 입력 시
ARR = [ x for x in input() ]    # ['1', '2', '3', '4', '5']
ARR = [ int(x) for x in input() ]  # [1, 2, 3, 4, 5], (숫자)문자 입력 시 에러 발생
                                   # 문자는 int 함수 적용 못하므로
# 1 2 3 4 입력 시
ARR = list( input().split() )   # ['1', '2', '3', '4']
ARR = list( map(int, input().split()) )  # [1, 2, 3, 4]

# input 의 속도가 느린 것이 염려될 떄
# 1 2 3 4 입력 시
import sys
list( map(int, sys.stdin.readline().split()) )  # [1, 2, 3, 4]
            ```



- 모든 경우의 수 탐색 - `완전 검색, Brute-force, generate and-test`

  => 수행 속도가 느림, 단 답은 항상 최적

  => 최초 문제 접근은 이 방식으로, 답이 나오면 속도 부분에서 개선할 것

- 눈 앞에 보이는 최적의 상황만을 쫓는 알고리즘

  => 수행 속도는 모든 경우의 수를 탐색하는 것 보다는 빠름

  => `but.. 항상 최적해를 보장하지는 않는다.`



** Baby-gin 문제 풀이

​    ㄱ. 6개의 0~9 숫자 카드 뽑기

​    ㄴ. 연속된 수 3개 -> Run

​          같은 수 3개 -> Triplet

​    ㄷ. Run이나 Triplet인 경우가 2개 이상이면 Baby-gin

​         (카드는 중복 사용 불가)

​         ex) 1 2 3 4 5 6  => Run 2회 - Baby-gin

​               1 1 1 2 3 4  => Run 1회, Triplet 1회 - Baby-gin

​               1 1 1 2 2 2  => Triplet 2회 - Baby-gin



```python
# brute-force 방식으로 접근

import sys

score = []
babygin_all = []

# 베이비진 모든 케이스 추가
for i1 in range(0, 10):
    for i2 in range(0, 10):
        for i3 in range(0, 10):
            a = [i1, i2, i3]
            if i1 == i2 == i3:
                score.append(a)
            if (i1 + 1) == (i2) and (i2 + 1) == (i3):
                score.append(a)

# 뽑은 카드와 일률적인 비교를 위해 sort
for i in score:
    for j in score:
        babygin_all.append(sorted(i+j))

# 주어진 카드 값 입력 및 베이비진 케이스와 일률적인 비교를 위해 sort
cards = sorted(list(map(int, sys.stdin.readline().split())))

if cards in babygin_all:
    print(cards)
    print('babygin!')
else:
    print(cards)
    print('패배')
```



```python
# greedy 알고리즘 방식으로 접근

import sys

# 기본 변수, nums - 뽑은 카드 , count - 카드 별 수
run, triplet = 0, 0
count = [0]*10
nums = list(map(int, sys.stdin.readline().split()))

for num in nums:
    count[num] += 1

    
# 왜 트리플 부터 검사하는 지는 에러 케이스를 분별하여 확인
idx = 0
while idx != len(count):
    # 트리플 진입
    if count[idx] >= 3:
        triplet += 1
        count[idx] -= 3
        continue
    # 런 진입
    if idx <= 7 and count[idx]>=1 and count[idx+1]>=1 and count[idx+2]>=1:
        run += 1
        count[idx] -= 1
        count[idx+1] -= 1
        count[idx+2] -= 1
        continue
    # 2점 획득 시 while문 탈출
    if run+triplet == 2:
        break
    idx += 1

if run+triplet == 2:
    print('baby-gin!')
else:
    print('lose')
```

