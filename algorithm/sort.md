# Sort

#### 퀵 정렬

```python
def quickSort(A, l, r):
    if l < r:
        s = partition(A, l, r)
        quickSort(A, l, s-1)
        quickSort(A, s+1, r)
    return A

# Hoare-Partition 알고리즘 (양방향에서 안으로 움직임)
def partition(A, l, r):
	p = A[l]  # p 피봇값
    i, j = l, r
    while i <= j:
    	while i <= j and A[i] <= p:
            i += 1
        while i <= j and A[j] >= p:
            j -= 1
        if i < j : 
            A[i], A[j] = A[j], A[i]
    A[l], A[j] = A[j, A[l]
    return j
    
# Lomuto partition 알고리즘 (한방향으로 가다가 피봇기준 나눠짐)
partiton(A[], p, r)
	x <- A[r]
    i <- p - l
    for j in p -> r-1
    	if A[j] <= x
        	i++, swap(A[i], A[j])
    swqp(A[i+1], A[r])
    return i+1
```



#### 이진검색

```python
def binarySearch(n, S, k):
    low = 0
    high = n-1
    while low <= high:
        mid = low + (high - low) // 2
        
        if S[mid] == key:
            return mid
        elif S[mid] > key:
            high = mid - 1
        else:
            low = mid + 1
   return -1

def binarySearch(S, low, high, key):  # 재귀구조
    if low > high:
        return -1
    else:
        mid = (low + high) // 2
        if key == S[mid]:
            return mid
        elif key < a[mid]:
            return binarySearch(a[], low, mid-1, key)
        else:
            return binarySearch(a[], mid+1, high, key)
```



#### 백트래킹

- 꽝에 도달하면 최근 선택으로 되돌아와서 다시 시작 (이전 선택으로 되돌아가기)
- 백트래킹과 깊이 우선 탐색과의 차이 
  - 어떤 노드가 해결책으로 이어지지 않을 것 같으면 시도횟수 줄임 -> Prunning 가지치기
  - 깊이우선 탐색은 모든경로 추적 백트래킹 불필요한 경로 조기 차단
  - 일반적으로 백트래킹이 경우의 수 줄어들지만 최악의 경우 여전히 지수함수 시간 걸릴 수도 

```python
# powerset 구하는 백트래킹 알고리즘

def backtrack(A, k, input):
    c  -> 후보 리스트
    ncan  -> 후보 수
    
    if k == input:
        process_solution(A, k)
    else:
        k ++
        make_candidates(A, k, input, c, ncan)
        for i in 0 -> ncan - 1
        	a[k] <- c[i]
            backtrack(a, k, input)
def make_candidates(A, k, n, c, ncan)
	c[0] <- True
    c[1] <- False
    nacna <- 2
def process_solution(A, k)
	for i in range(1, k):
        if a[i] == True:
            print(i)
            
A <- powerset 저장할 배열
backtrack(A, 0, 3)  3개의 원소가지는 powerset
    
```

