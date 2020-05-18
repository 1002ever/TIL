# 1. 30

## 알고리즘 이론 2



### *** 정렬



* 버블 정렬  => O(N^2)

  ​       (자료수 = N)

  - 리스트 공간 하나만 활용 

  - 두 개씩만 비교하여 일정 기준에 따라 자리 변경

    -> N-1 바퀴, 바퀴 마다 N-1 번 돌면 완료

    ​    => 최악의 경우 (N-1)(N-1) 회 변환



``` python
# 7 6 5 4 3 2 1 입력 시
nums = list(map(int, input().split()))

for j in range(len(nums)-1):
    for i in range(len(nums)-1-j):
        if nums[i] > nums[i+1]:
            nums[i], nums[i+1] = nums[i+1], nums[i]

print(nums)
# [1, 2, 3, 4, 5, 6, 7]


# 위와 동일한 for문 임을 참고
# 가변 인자로 전달할 때 range 활용할 것

nums = list(map(int, input().split()))

for j in range(len(nums)-1, 0, -1):
    for i in range(j):
        if nums[i] > nums[i+1]:
            nums[i], nums[i+1] = nums[i+1], nums[i]

print(nums)


# 탈출 조건(변환이 없는 경우) 추가한 버전

nums = list(map(int, input().split()))

for j in range(len(nums)-1, 0, -1):
    cnt = 0
    for i in range(j):
        if nums[i] > nums[i+1]:
            nums[i], nums[i+1] = nums[i+1], nums[i]
            cnt += 1
    # 변환이 없으면 중지
    if cnt == 0:
        break

print(nums)
```



- 카운팅 정렬

  - 정수 / 중복 자료에만 유효하게 작동

  - 정렬 대상 리스트 / 각 숫자의 카운트를 저장하는 리스트 / 최종 정렬 결과를 저장하는 리스트

    => 정렬 대상의 요소가 count의 인덱스가 되며

    ​     각 숫자의 카운트를 저장 -> 위치를 파악하기 위하여 점차 sum

    

  ```python
  nums = [0, 4, 1, 3, 1, 2, 4, 1]
  cnt = [0] * len(set(nums))
  temp = [-1] * len(nums)   # -1 이면 수정되지 않은 것
  print(cnt)
  
  for num in nums:
      cnt[num] += 1
  
  for idx in range(1, len(cnt)):
      cnt[idx] = cnt[idx-1] + cnt[idx]
  
  for idx in range(len(nums)-1, -1, -1):
      temp[cnt[nums[idx]]-1] = nums[idx]
      cnt[nums[idx]] -= 1
  
  print(temp)
  ```

  

  

