# 알고리즘

- 좋은 알고리즘

  1. 정확성
  2. 작업량
  3. 메모리 사용량
  4. 단순성
  5. 최적성

- 시간복잡도 (빅오표기법)

  <img src="C:\Users\a\TIL\algorithm\big-o.jpg" alt="big-o" style="zoom:50%;" />

#### 버블정렬

- 인접한 두 개의 원소를 비교하며 자리를 계속 교환하는 방식
- O(n**2)

```python
def BubbleSort(a) :
    for i in range(len(a)-1, 0, -1):
        for j in range(0, i):
            if a[j] > a[j+1]:
                a[j], a[j+1] = a[j+1], a[j]
```



#### 카운팅정렬

- 항목들의 순서를 결정하기 위해 집합에 각 항목이 몇 개씩 있는지 세는 작업
- O(n+k)

```python
def Conting_Sort(A, B, k)
# A [] --입력 배열 (1 to k)
# B [] --정렬된 배열
# C [] -- 카운트 배열

C = [0] * (k+1)

for i in range (0, len(A)) :
    C[A[i]] += 1

for i in range (1, len(C)) :
    C[i] += C[i-1]
    
for i in range (len(B)-1, -1, -1):
    B[C[A[i]]-1] = A[i]
    C[A[i]] -= 1

# 입력배열의 데이터를 카운트배열의 인덱스로 활용
# 카운트배열의 데이터를 정렬된배열의 인덱스로 활용
```

#### 순열 (완전탐색)

- 서로 다른 것들 중 몇 개를 뽑아서 한 줄로 나열 
- nPr = n * (n-1) * ... * (n-r+1) = n!/(n-r)!
- nPn = n!

#### 탐욕(greedy) 알고리즘

- 해선택 (부분문제의 최적해)
- 실행 가능성 검사
- 해 검사

```python
# 베이비진문제 카운트함수로 해결해보기

num = 456789
c = [0]

for i in range(6) :
    # 끝자리 숫자부터 빼기
    c[num % 10] += 1 
    num //= 10

i = 0
tri = run = 0
while i < 10 :
    if c[i] >= 3 : #triplete 조사 후 데이터 삭제
        c[i] -= 3
        tri += 1
        continue;
    if c[i] >= and c[i+1] >= 1 and c[i+2] >= 1 : # run 조사 후 데이터 삭제
        c[i] -= 1
        c[i+1] -= 1
        c[i+2] -= 1
        run += 1
        continue
    i += 1
if run + tri == 2 : print("baby gin")
else : print("Lose")    
```

