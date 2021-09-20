#### 2차원 배열

```python
arr = [[0] * M for _ in range(N)]

for i in range(len(arr)):
    for j in range(len(arr[i])):
        arr[i][j]

#지그재그 순회 (m:len(arr[0]), m 없어도 가능)     
for i in range(len(arr)):
    for j in range(len(arr[0])):
        arr[i][j + (m-1-2*j) * (i%2)]
        
#전치행렬 - 대각선기준 양쪽 바꾸기
for i in range(3):
    for j in range(3):
        if i < j:
            arr[i][j], arr[j][i] = arr[j][i], arr[i][j]
        
# 델타 이용 4방향 탐색
dx = [0, 0, -1, 1] # 상하좌우
dy = [-1, 1, 0, 0]
for x in range(len(ary)):
    for y in range(len(ary[x])):
        for I in range(4):
            x = x + dx[mode]
            y = y + dy[mode]
```

#### 부분집합

- 부분집합의 수는 2**n개 (포함시키거나 포함시키지않거나)

#### 비트연산자

- & and, | or , << 비트열 왼쪽으로, >> 비트열 오른쪽으로 이동
- 1 << n  : 2**n 원소 n개일 경우 모든 부분집합의 수

```python
#부분집합 생성
n = len(arr)
for i in range(1<<n): # 1 << n 부분집합의 개수 (2**n)
    for j in range(n): # 원소의 수만큼 비트 비교
        if i & (1<<j): # i의 j번째 비트가 1이면 j번째 원소 출력
            print(arr[j], end=", ")
    print()
print()
```



#### 순차검색 (sequential search)

- 일렬로 되어있는 자료를 순서대로 검색
- 배열이나 연결 리스트 등 순차구조에서 유용
- O(n)

```python
#정렬되어있지 않은 경우
def sequentialSearch(a, n, key):
    i <- 0
    while i < n and a[i]!= key:
        i <- i+1
    if i<n : return i
    else : return -1
    
#정렬되어있는 경우 
def sequentialSearch2(a, n, key):
    i <- 0
    while i < n and a[i]< key:
        i <- i+1
    if i<n and a[i] == key : 
        return i
    else : 
        return -1
```



#### 이진검색 (binary search)

- 자료의 가운데에 있는 항목의 키값과 비교하여 다음 검색 위치 결정하고 검색 진행 (정렬된 상태여야)

```python
def binarySearch(a, key):
    start <- 0
    end <- length(a)-1
    while start <= end :
        middle = (start+end)//2
        if a[middle] == key:
            return true
        elif a[middle] > key:
            end = middle - 1
        else:
            start = middle + 1
   return false

# 재귀이용
def binarySearch2(a, low, high, key):
    if low > high:
        return False
    else:
        mid = (low + high) // 2
        if key == a[mid]:
            return True
        elif key < a[mid]:
            return binarySearch2(a, low, mid-1, key)
        elif a[mid] < key:
            return binarySearch2(a, mid+1, high, key)

```



#### 선택정렬 (selection sort)

- 최소값 찾아 맨앞과 교환
- O(n**2)

```python
def selectionSort(a) :
    for i in range(0, len(a)-1):
        min = i
        for j in range(i+1, len(a)):
            if a[min] > a[j]:
                min = j
        a[i], a[min] = a[min], a[i]
```



#### 셀렉션 알고리즘

- k번째로 큰 혹은 작은 원소를 찾는 방법
- O(kn)

```python
def select(list, k):
    for i in range(0, k):
        min = i
        for j in range(i+1, len(list)):
            if list[min] > list[j]:
                min = j
        list[i], list[min] = list[min], list[i]
    return list[k-1]
```



- 상하좌우 이동하기

```python
    dx = [0, 1, 0, -1] #우하좌상
    dy = [1, 0, -1, 0]
    k = 0
    x = 0
    y = -1

    while score <= (n * n):
        nx = x + dx[k%4]
        ny = y + dy[k%4]
        if nx in range(n) and ny in range(n) and arr[nx][ny] == 0:
            arr[nx][ny] = score
            score += 1
            x, y = nx, ny
        else:
            k += 1
```

