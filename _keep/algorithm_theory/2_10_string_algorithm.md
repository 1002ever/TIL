# 문자열 패턴 인식 알고리즘



#### ** 보이어-무어 알고리즘

a b c d e f a b c d e f a b c d e f   - 검사 대상 ( N = 18 )

 

abc                                                  - 체크 패턴 ( M = 3 )



1. 세 칸부터 읽어서 c가 있는지 확인

2. 있으면 -> 순차적으로 앞 글자를 비교하고, 불일치 시 체크 패턴 길이 만큼 전진 - 검사 영역 변경

   없으면 -> 검사 대상 중 체크 패턴의 어떤 글자 있는지를 확인.

   ​                 그 위치에 맞춰 검사 영역 변경

   -> 교재 139~142p

   최악의 경우 : O(MN)     /   but 보통 O(N)  보다는 짧게 걸린다.





#### ** 브루트 포스 문자열 찾기

```python
p = 'mor'
txt = 'good morning'

tmp = 0
for i in range(len(txt)-len(p)+1):
    cnt = 0
    for j in range(len(p)):
        if txt[i+j] != p[j]:
            break
        else:
            cnt += 1
    if cnt == len(p):
        print('mor 시작 위치 : ', i)
        # mor 시작 위치 : 5
```



