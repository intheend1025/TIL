# 큐

- 선입 선출
- 원형큐는 mod사용하여 처음과 끝이 연결된 구조 사용



### 우선순위 큐

- FIFO 순서가 아닌 우선순위가 높은 순서대로 나가도록
- 버퍼 : 데이터를 다른 한곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 메모리의 영역



### BFS(너비우선탐색 Breadth First Search)

- 인접한 정점 모두 방문 후 방문한 정점의 다시 인접한 정점 방문

```python
def BFS(G, v):
    visited = [0]*n
    queue = []
    queue.append(v) # 시작점 v 삽입
    while queue:
        t = queue.pop(0)
        if not visited[t]:
            visited[t] = True
            # visit(t)
        for i in G[t]:
            if not visited[i]:
                queue.append(i)
```

