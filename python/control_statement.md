# control statement

### 1. 홀짝 여부

```python
if num % 2:
    print('홀수')
else:
    print('짝수')
```

### 2. 조건 표현식

- <true인 경우 값> if <experession>  else <false인 경우 값>

```python
#절대값
value = num if num >=0 else -num
```

### 3. enumerate

- 내장함수 enumerate의 경우 (index, value) 형태의 tuple로 구성된 열거 객체를 반환

```python
members = ['민수', '영희', '철수']
for idx, member in enumerate(members):
    print(idx, member)
    
# 0 민수
# 1 영희
# 2 철수
```



### 4. break, continue

- break는 반복문 종료
- continue는 아래 실행하지않고 반복문으로 다시 되돌아감



### 5. while

```python
#나머지를 이용하여 일의자리부터 출력
n = int(input())

while n > 0:
    print(n % 10) 
    n = n // 10
#185 input -> 5 8 1
```



### 6. 반복제어 (break, continue, for  - else)

```python
#for-else
for num in numbers:
    if num == 4:
        print(True)
        break
else:
    print(False)

# False
```



ex) 연습하기

```python
#N의 약수구하기
N = int(input())

for i in range(1, N+1):
    if N % i == 0:
        print(i, end=' ')
```

### 

```python
#계단 만들기
number = int(input())
        
for i in range(1, number+1):
    for j in range(1, i+1):
        print(j, end='')
    print()
        
```



