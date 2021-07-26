# data_structures

### 1. 순서가 있는 데이터 구조



#### 문자열 immutable 

- 문자열.find(x) - x의 위치 없으면 -1

- .index(x) - x의 위치 없으면 Value Error

- .replace(old, new, [count]) - 바꿀 글자를 새로운 글자로 바꿔서 반환 (복사본 반환), count 지정하면 해당 개수만큼 시행

- .strip([chars]) 특정문자 지정하면 양쪽, 혹은 왼쪽(lstrip)이나 오른쪽(rstrip) 제거 (기본값은 공백제거)

- .split 특정단위로 나눠 리스트로 반환

- (separator).join separator로 합쳐 문자열 반환 

  ex) '!'.join('ssafy') - 's!s!a!f!y'

- .capitalize() - 첫문자 대문자, 나머지 소문자

- .title() - '나공백이후 단어 첫문자를 대문자

- .upper() - 모두 대문자

- .lower() - 모두 소문자

- .swapcase() - 대<->소문자

- .isalpha() 알파벳 문자 여부

- .isupper() 대문자 여부

- .islower() 소문자 여부

- .istitle() 타이틀 형식 여부



#### 리스트

- .extend(iterable) 항목 추가
- .insert(i, x) 정해진 위치 i에 값 x 추가
- .remove(x) 첫번째 x 삭제
- .pop(i) 정해진 위치 i 값삭제 후 반환 (i지정안하면 마지막값)
- .clear() 모든항목삭제
- .index(x) 첫번째 x의 인덱스값반환
- .count(x) x의 개수 반환
- .sort() 원본 리스트 정렬
- .sorted 정렬된 복사본 반환
- .reverse() 원본 순서 뒤집어서
- 리스트는 복사하면 원본이랑 같이 변경됨(같은주소)
- 리스트 슬라이싱하면 다른 주소로 생성
- copy.deepcopy 리스트 복사 
- [<expression> for <변수> in <iterable> if<조건식>]
- map(function, iterable) 반복가능데이터구조의 모든 요소에 함수 적용하고 map object로 반환

```python
# i = input() 1 2 3 4 5
# number_str = i.sprit(' ') '1', '2', '3', '4', '5'
result = []
result = map(int, input().sprit(' '))
print(list(result))
```



- filter(function, iterable) True인 것들만 filter object로 반환
- zip(*iterables) 복수iterable을 모아 튜플을 원소로 하는 zip object 반환



### 2. 순서가 없는 데이터 구조



#### 세트 (비시퀀스) 중복허용x

- .add 추가 (순서x)
- .update(*others) 여러값 추가
- .remove(elem) 삭제 없으면 에러발생
- .discard(elem) 삭제 없어도 에러발생x
- .pop() 임의의 원소 제거해 반환



#### 딕셔너리

- .get(key, [default]) key 대응 value 가져옴 없어도 키에러 발생x (None 돌려줌)
- dict[key] key 없으면 에러발생
- .pop(key, [default]) 키제거 후 해당 값 반환  키값없는데 default 설정안하면 에러 발생
- .update() key, value 갱신
- 반복문하면 기본적으로 key 순회
- .keys() 키값 반환
- .values() 값 반환
- .items() 키와값 튜플형태로 반환
- Create - a['서울'] = 02 / Read - a.get() / Update - a.update() / Delete - a.pop()

```python
result = {}
for key, value in dusts.items():
if value > 70:
result[key] = value

{key: value for key, value in dusts.items() if values > 70}
```

