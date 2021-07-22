# Function

함수는 정의 -> 호출

### 1. 매개변수 (parameter) vs 인자 (argument)

- 매개변수 : 함수에 입력으로 전달된 값을 받는 변수 / 이름  ex) def my_func(a, b)
- 인자 : 함수 호출할 때 함수에 전달하는 입력 값 / 값 ex) my_func(1, 2)
- 기본인자 값을 가지는 인자 다음에 기본 값이 없는 인자 정의할 수 없음 ex) add(x=3, 5) (x)

### 2.  가변 인자 리스트 

- 정해지지 않은 여러 개의 인자 처리
- 매개변수에 *을 붙여 표현
- *args, *objects
- ex) my_info(x, y, *args, **kwargs) 순서 주의! 가변은 뒤쪽에 인자받아야
- unpacking - 인자에 *쓰면 리스트 풀어서 각각 인자에 넣어줌

### 3. 가변 키워드 인자

- 인자들은 딕셔너리로 묶여 처리되며 매개변수에 **을 붙여 표현
- **kwargs

```python
def my_url(**kwargs):
    base_url = 'https://api.go.kr?'
    
    for key, value in kwargs.items():
        base_url += f'{key}={value}&'
        
    return base_url

print(my_url(sidoname='서울', key='asdf'))
#https://api.go.kr?sidoname=서울&key=asdf&
```

### 4. 함수 스코프

- 전역스코프 (global scope) : 코드 어디에서든 참조 가능 
- 지역 스코프(local scope) : 

### 5. LEGB rule

- local > Enclosed > Global > Built-in scope 순서로 이름 찾아 나감
- 이름 검색 규칙
- 로컬에서 global 선언으로 변수 scope 변경 가능 (but, 사용 제한 - 선언 전 사용불가, 매개변수 for루프 클래스/함수 정의되지 않아야)
- nonlocal



### 6. 실습

```python
# 리스트 내에서 반복문 돌리면 리스트 내의 요소들을 각각 출력함

def all_list_sum(a):
    total = 0
  
    for i in a:
        for j in i:
            total += j
    
    return total


print(all_list_sum([[1], [2, 3], [4, 5, 6], [7, 8, 9, 10]]))
```

- tuple 도 인덱싱 가능!

```python

def my_abs(x):
    if type(x) == complex:
        #복소수값 나누기 x.real, x.imag
        return (x.real ** 2 + x.imag ** 2) ** (1 / 2)
    
    else:
        if x == 0:
            return x ** 2 #-0.0일경우를 대비하여 제곱
        
        if x < 0:
            return x *(-1)
        else:
            return x
    
```

- int를 container처럼 사용하고 싶으면 str으로 형변환하면 됨

