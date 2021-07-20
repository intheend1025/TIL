# Data type

### 1. string Interpolation

``` python
# %-formatting
print('hello, %s' % name)
# str.format()
print('hello, {}'.format(name))
#f-strings
print(f'hello, {name}')
```



### 2. 논리 연산자

- and 연산에서 첫번째 값이 False인 경우 무조건 False이므로 첫번째 값 반환
- or 연산에서 첫번째 값이 True인 경우 무조건 True이므로 첫번째 값 반환



### 3. print

- print( , end = '\n')) 띄어쓰기가 기본
- 띄어쓰기 외에 end=' ' 옵션으로 설정가능



### 4. divmod

```python
print(divmod(5, 2)) # (몫, 나머지) (2, 1)
```



# Container



### 1. 시퀀스형 - 순서가 있는 데이터

- 리스트(list) , 튜플(tuple), 레인지(range), 문자형(string), 바이너리(binary)

### 2. 비시퀀스형  - 순서가 없는 데이터

- 세트(set), 딕셔너리(dictionary)

### 3.  변경 불가능한 데이터 (immutable)

- 리터럴 - 숫자, 문자열, 참거짓(bool)
- range
- tuple
- b = a를 하면 같은 값이 공유되며 b = 10을 통해 재할당발생

### 4. 변경 가능한 데이터 (mutable)

- list
- set
- dictionary
- num2 = num1를 하는 경우 동일한 리스트(객체)의 주소를 참조하고 있어
- num2[0] = 100으로 변경하면 num1도 같이 변경됨

### 5. Range

- range(start, end, [step, ])

### 6. Set

- 순서 및 중복된 값이 없음

```python
my_list = [1, 2, 3, 1, 1, 2]
set(my_list)
list(set(my_list)) #중복된 값 제거하기
```

### 7. Dictionary

```python
{Key1:Value1, Key2:Value2, Key3:Value3, ...}
```

- dictionary에는 중복된 key 존재할 수 없음
- key는 변경 불가능한 데이터만 가능 (string, integer, float, boolean, tuple, range)

```python
#형변환
d = {'name': 'ssafy', 'year': 2020}
print(str(d)) #{'name': 'ssafy', 'year': 2020}
print(list(d)) #['name', 'year']
print(tuple(d)) #('name', 'year')
print(set(d)) #{'name', 'year'}
# range(d)
```

