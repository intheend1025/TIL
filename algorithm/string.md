#### 고지식한 패턴

- O(MN)
- 처음부터 끝까지 순회하며 일일이 비교

```python
def BruteForce(p, t):
    i = 0
    j = 0
    while j < len(p) and i < len(t):
        if t[i] != p[j]:
            i = i - j
            j = -1
        i += 1
        j += 1
    if j == M: return i - M
    else: return -1
```



#### KMP 알고리즘

- 불일치가 발생한 앞 부분에 대해 다시 비교하지 않고 수행
- 패턴을 전처리하여 next[M]을 구해서 잘못된 시작 최소화
- 계속연속하면 연속한 숫자 계속 쓰고 아니면 0으로 되돌아갈 위치 알아내기
- O(M+N)

```python
next = [0] * M
cnt = 0 # 일치한 개수
i = 1
while i < M:
    if p[i] == p[cnt]
    cnt += 1
    next[i] = cnt
    i += 1
   	else:
        if cnt != 0:
        cnt = next[cnt-1]
        else:
            next[i] = 0
            i += 1
```



#### 보이어-무어 알고리즘

- 오른쪽에서 왼쪽으로 비교
- 오른쪽 끝 문자가 불일치하고 문자가 패턴내 존재할 경우 점프
- 최악 O(mn) 일반 O(n)보다 짧음