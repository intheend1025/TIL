# Tree

### 트리

- 노드 중 최상위 노드를 루트
- 형제노드 - 같은부모의 자식노드들
- 조상노드 - 간선따라 루트까지 이르는 경로에 모든 노드
- 서브트리 부모와 연결된 간선을 끊었을 때 생성되는 트리
- 자손노드 서브 트리에 있는 하위레벨 노드



### 이진트리

- 모든 노드들이 최대 2개의 서브트리를 갖는 트리

- 높이 h 인 트리 노드의 최소개수는 (h+1), 최대 개수 (2**(h+1)-1)

- 포화 이진 트리 - 꽉찬 이진트리 (최대 노드수 가진)

- 완전 이진 트리 - 높이 h, 노드 n 일때 n번까지 빈자리가 없는 이진트리

- 편향 이진 트리 - 한쪽 방향 자식 노드만 가진 이진 트리

- 순회(traversal) (V루트, L왼, R 오른)

  - 전위순회 VLR 

    ```python
    def pre_order_traverse(T):
        if T:
            visit(T)
            preorder_traverse(T.left)
            preorder_traverse(T.right)
    ```

    
  
  - 중위순회 LVR
  
    ```python
    def in_order_traverse(T):
        if T:
            preorder_traverse(T.left)
            visit(T)
            preorder_traverse(T.right)
    ```
  
    
  
  - 후위순회 LRV
  
    ```python
    def post_order_traverse(T):
        if T:
            preorder_traverse(T.left)
            preorder_traverse(T.right)
            visit(T)
    ```
  
    

### 이진탐색 트리

- 평균 : O(log n)

- 최악의 경우 : O(n)

  ```python
  def dfsbyPreOrder(c):
      print(nodes[c])
      # 왼쪽 자식 노드 방문
      if c*2 <= lastIndex:
          dfsbyPreOrder(c*2)
      # 오른쪽 자식 노드 방문
      if c*2+1 <= lastIndex:
          dfsbyPreOrder(c*2+1)
  ```

  



### 힙

- 완전 이진 트리에 있는 노드 중 키값이 가장 큰 노드나 키 값이 가장 작은 노드를 찾기 위해 만든 자료구조
- 일단 이진트리로 구성한 후 최대힙경우 부모노드키값이 자식노드보다 크도록 이동 (최소힙의 경우 반대)
- O(log n )  10억개여도 약 30번만에 구할 수 있음(2**30) 최대최소값은 O(1)만에 구할 수 있음

```python
import heapq
# 리스트를 힙큐로 바꾸기
heapq.heapify(list)

# 힙큐에서 최소값 구하기
s1 = heapq.heappop(list)
# 힙큐에 새로운 원소 s1 넣기
heapq.heappush(list, s1)
```

