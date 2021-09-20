# 스택

### 스택

- 물건 쌓아 올리듯 자료를 쌓아 올린 형태
- 선형구조 (자료간 관계가 1대1의 관계
- 후입선출
- 마지막 원소위치 top
- 삽입 - push / 삭제 - pop / 공백인지 확인 - isEmpty / top에 있는 원소 확인 - peek
- 스택의 크기를 변경하기 어렵다는 단점 
  - 이를 해결하기 위해선 저장소를 동적으로 할당하는 동적 연결리스트 이용 -> 구현복잡하지만 메모리 효율적으로 사용하는 장점

```python
def push(item):
    s.append(item)

def pop():
    if len(s) == 0:
        # underflow
        return
   else:
    return s.pop(-1);
```



### 재귀호출

- 자기 자신을 호출하여 순환 수행되는 것

```python
def f(i, k): 
    if i == k: # 배열 벗어나면
        return
   	else:
        print(A[i])
        f(i+1, k) # 다음 원소로 이동
    
N = 3
A = [10, 20, 30]
f(0,N) # 배열 출력 함수
```

```python
def fibo(n):
    if n < 2:
        return n
   	else:
        return fibo(n-1) + fibo(n-2)   # 중복 호출 多 O(2**n)
```



### Memorization

- 이전 계산 값을 저장하여 매번 다시 계산하지 않도록하여 실행속도 빠르게  하는 기술 (동적 계획법의 핵심 기술)

```python
def fibo1(n):
    global memo
    if n >= 2 and memo[n] == 0: #len(memo1) <= n:
        memo[n] = fibo(n-1) + fibo(n-2) #memo1.append(fibo1(n-1) + fibo1(n-2))
    return memo[n]

n = 50
memo = [0] * (n+1) # memo1 = [0,1]
memo[0] = 0
memo[1] = 1
```



### DP (Dynamic Programming)

- 동적 계획 알고리즘은 그리디와 같이 최적화 문제 해결위한 알고리즘
- 입력크기가 작은 부분 문제들을 모두 해결한 후에 그 해들을 이용해 큰 크기의 부분 문제들을 해결하여 최종적으로 원래 주어진 입력 문제 해결
- 재귀적 구조보다 효율적 (재귀적 구조는 시스템 호출 스택을 사용하는 오버헤드 발생하기 때문)

```python
def fibo2(n):
    f = [0, 1]
    
    for i in range(2, n+1):
        f.append(f[i-1]+ f[i-2])
    return f[n]
```

```python
def fact(n):
    table[0] = 1
    for i in range(1, n+1):
        table[i] = i * table[i-1]
    return table[n]
n = int(input())
table = [0] * (n + 1)
```



### DFS (깊이우선탐색 Depth First Search)

- 비선형구조인 그래프 구조는 그래프로 표현된 모든 자료를 빠짐없이 검색하는 것이 중요
- 시작에서 한방향으로 경로 끝까지 깊이 탐색하다가 더이상 갈 곳이 없어지면 가장 마지막에 만났던 갈림길로 되돌아와 다른 방향 정점으로 계속 반복하여 모든 정점 방문하는 방법
- 가장 마지막 갈림길의 정점으로 되돌아가 다시 깊이 우선 탐색 반복해야 하므로 후입선출 구조의 스택 사용
- 방법
  1) 시작 정점 v를 결정하여 방문
  2) 정점 v에 인접한 정점 중에서 방문하지 않은 정점w가있으면 v를 스택에 push 후 정점 w 방문 그리고 w 를 v로 해서 다시 반복 / 정점 다 방문했으면 탐색방향 바꾸기 위해 스택 pop하여 마지막 정점 다시 v
  3) 스택 공백될 때까지 반복

```python
def dfs(s, v):
    visited = [0]*(v+1)
    stack = []
    i = s # 현재 방문한 정점 i
    visited[i] = 1
    print(node[i])
    while i!=0:
        for w in range(1, v+1):
            if adj[i][w] == 1 and visited[w] == 0: 
                stack.append(i) # 방문 경로 저장
                i = w 			# 새 방문지 이동
                visited[w] = 1
                break
            else:
                if stack:
                    i = stack.pop()
               	else:
                    i = 0
    
```

