# 투 포인터

- 투 포인터 알고리즘: 리스트에 순차적으로 접근해야 할 때 두 개의 점의 위치를 기록하면서 처리하는 알고리즘
- 리스트에 담긴 데이터에 순차적으로 접근해야 할 때는 시작점과 끝점 2개의 점으로 접근할 데이터의 범위 표현

## 특정한 합을 가지는 부분 연속 수열 찾기
```
N개의 자연수로 구성된 수열
합이 M인 부분 연속 수열의 개수
```
```
1. 시작점(start)과 끝점(end)이 첫 번째 원소의 인덱스(0)을 가리키도록 한다.
2. 현재 부분 합 == M : 카운트
3. 현재 부분 합 < M : end + 1
4. 현재 부분 합 >= M : start + 1
5. 모든 경우를 확인할 때까지 2번부터 4번까지의 과정 반복
```
- M = 5
- 1 2 3 2 5
```
1. s(0), e(0) : 부분합 1 => e + 1
2. s(0), e(1) : 부분합 3 => e + 1
3. s(0), e(2) : 부분합 6 => s + 1
4. s(1), e(2) : 부분합 5 => cnt + 1
5. s(2), e(2) : 부분합 3 => e + 1
6. s(2), e(3) : 부분합 5 => cnt + 1
7. s(3), e(3) : 부분합 2 => e + 1
8. s(3), e(4) : 부분합 7 => s + 1
9. s(4), e(4) : 부분합 5 => cnt + 1
cnt = 3
```
```python
# 데이터의 개수
n = 5
# 찾고자 하는 부분합
m = 5
# 전체 수열
data = [1, 2, 3, 2, 5]

cnt = 0
cur_sum = 0
end = 0

# start를 차례대로 증가시키며 반복
for start in range(n):
    # end를 가능한 만큼 이동시키기
    while cur_sum < m and end < n:
        cur_sum += data[end]
        end += 1
    # 부분합이 m일 때 카운트 증가
    if cur_sum == m:
        cnt += 1
    cur_sum -= data[start]

print(cnt)
```