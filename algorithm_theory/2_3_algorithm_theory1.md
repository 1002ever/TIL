# 2.3 알고리즘 이론



## * 2중 리스트



- 지그재그 순회 - 인덱싱 수식 봐두기.

```python
# 분기로 나눠주기
tmp = []
for i in range(len(Arr)):
    for j in range(len(Arr[0])):
        if i%2 == 1:
            tmp[i][j] = Arr[i][m-1-j]
        else:
            tmp[i][j] = Arr[i][j]
        
# 수식 합쳐주기
tmp = []
for i in range(len(Arr)):
    for j in range(len(Arr[0])):
        tmp[i][j] = Arr[i][j + (m-1-2*j) * (i%2)]   # 암기
```



- 배열 내 특정 방향으로 이동 => 좌표 변동 값 설정

```python
arr[n][n]
dx = [0, 0, -1, 1]    # 상하좌우 값 설정(인덱스 변동 값)
dy = [-1, 1, 0, 0]

# x,y는 현 index일 때
tmp_up = arr[x+dx[0]][y+dy[0]]     # 상
tmp_down = arr[x+dx[1]][y+dy[1]]   # 하
tmp_left = arr[x+dx[2]][y+dy[2]]   # 좌
tmp_right = arr[x+dx[3]][y+dy[3]]  # 우
```



- 전치행렬 => transposed(Arr) 구현

```python
arr[3][3]

for i in range(3):
    for j in range(3):
        if i < j:
            arr[i][j], arr[j][i] = arr[j][i], arr[i][j]
```

- python에서의 행렬 입력

```python
N = int(input())  # 행 수
# 한 줄씩 네 번 리스트로 읽어들여 리스트로 묶음 => 2중 리스트 = 행렬
arr = [list(map(int, input().split())) for i in range(N)]

# 4
# 1 2 3 4
# 5 6 7 8
# 9 1 5 2
# 2 7 6 9  입력 시

print(arr)
# [[1,2,3,4], [5,6,7,8], [9,1,5,2], [2,7,6,9]] 출력
```

- 2차원 배열(행렬)에서 각 인접한 요소들과의 차이들의 총합

```python
N = int(input())
arr = [list(map(int, input().split())) for i in range(N)]
ans = 0

dx = [0, 0, -1, 1]
dy = [-1, 1, 0, 0]

for i in range(N):
    for j in range(N):
        sums = 0
        for k in range(len(dx)): # 이동 명령 4개이므로
            if 0 <= i+dx[k] < N and 0 <= j+dy[k] < N:
                sums += abs(arr[i][j]-arr[i+dx[k]][j+dy[k]])
        ans += sums

print(ans)
```



- 세 원소의 모든 부분집합 찾기  => for문 사용.

  -> 특정 원소가 들어가면 1 값이라고 보고

     => 원소 수가 가변적일 때 또는 원소 수가 많을 때 한계점이 있다.

```python
for i in range(2):
    for j in range(2):
        for k in range(2):
            print(i,j,k)
            
# 0 0 0
# 0 0 1
#  ...
# 1 0 1
# 1 1 0
# 1 1 1
```



** 부분집합 수 ( 비트 연산 관련 )

​    = 2 ** 원소 수

​    = 1 << 원소 수         => 둘 다 같은 결과 but 비트 연산이 일반 연산 보다 훨씬 빠르다.

​                                           실제로 부분집합 수 구할 때 자주 사용 된다.



####   * i & (1 << j)

​      \# i 에서의 우측에서부터 j 번째 비트가 1인지 검사할 때 쓰는 수식



#### *** 비트 연산을 활용한 모든 부분집합 찾기

```python
arr = [3,6,9]

for i in range(1<<len(arr)):   # i = 0 ~ 7 , 000 001 010 011 100 101 110 111
    sub = []
    for j in range(len(arr)):  # h = 0 ~ 2 // j 는 arr에서 부분집합에 속할 인덱스 번호인 셈
        if i & (1<<j):         # i의 우측부터 j 번째 인덱스가 들어있다면
            sub.append(arr[j]) # 그 해당 값을 부분집합에 요소 추가.   
                               # => 우측부터 인덱스 세는 것.. 110 이면 2,3번째 요소 포함
    print(sub)
    
# []
# [3]
# [6]
# [3, 6]
# [9]
# [3, 9]
# [6, 9]
# [3, 6, 9]
```



