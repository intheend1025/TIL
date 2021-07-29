# OOP

### 객체 - 클래스의 인스턴스

- 설계도 기반(클래스) 실제 물체 (객체)

- ex) my_lower('Hi') -> 함수가 데이터(객체)를 처리 vs  'hi'.lower() 데이터(객체)가 매서드 호출 (주도적)

- 객체는 특정 타입의 인스턴스다.



#### 특징

- 클래스 : 객체들의 분류 
  - 선언(ex, 청소기) : 정의(설계도) - 정보[속성](어떤상태(데이터) - 크기, 전압, 색), 기능[메서드](어떤 행위(함수) - 먼지흡입) 
  - 클래스는 대문자표기법(pascal case) ex)BeautifulSoup
  - 클래스 정의 class MyClass:
  - 인스턴스 생성 my_instance = MyClass()
  - 메서드 호출 my_instance.my_method()
  - 속성 my_instance.my_attribute
- 인스턴스 : 하나하나의 실체
- 사용 : 인스턴스화 (실제 청소기)
- '1' -> str의 인스턴스
- 속성엔 ()가 없음 (ex 복소수 나누기)
- 매서드는 특정 객체에 적용될 수 있는 행위
- isinstance 함수
  - isinstance(object, classinfo) : classinfo의 instance거나 subclass일 경우 True
- self : 인스턴스 자기자신 (매개변수 이름으로)

 

#### 객체지향 프로그래밍

- 명령형 프로그래밍
- 객체들의 모임, 현실세계를 프로그램설계에 반영(추상화)
- 데이터와 기능(매서드) 분리, 추상화된 구조 (인터페이스)



#### 매서드의 종류

- 인스턴스 매서드
  - 첫번째 인자로 self 전달
  - 인스턴스 호출 활용
  - 인스턴스는 클래스, 스태틱 메서드 호출 가능 (권장x)
- 클래스 매서드
  - @classmethod 데코레이터 사용하여 정의
  - 첫번째 인자로 클래스 전달
  - 클래스 호출 활용
- 스태틱 매서드
  - @staticmethod 데코 사용 정의
  - 어떤 인자도 전달되지 않음

- 클래스 변수
  - 클래스 정의 안에 (인스턴스 밖) 선언
  - 특정 클래스 인스턴스에 묶여 있지 않음
  - 클래스 자체 내용 저장
  - 같은 클래스에서 생성된 모든 객체는 동일한 클래스 변수 공유
- 인스턴스 변수
  - 항상 특정 인스턴스에 묶여있음
  - 클래스에 저장x 개별 객체에 저장
  - 인스턴스마다 독립적이므로 변수 값 수정하면 해당 객체에만 영향
- == : 객체 내용이 같은 경우
- is  : 동일한 객체 가리킴



#### 상속

상속을 통한 메서드 재사용

- issubclass(class, classinfo) - ex) issubclass(bool, int) bool은 int의 서브클래스냐?
- super() : 자식클래스에서 부모클래스 속성 사용하고 싶을 때
- 매서드 오버라이딩 : 상속받은 매서드를 재정의
- 인스턴스 자식 부모 클래스 순으로 탐색
- 다중 상속 : 상속순서에 따라 찾는 순서 달라짐 (앞에있는거 먼저)



#### 실습

```python
#리스트내에서 랜덤으로 뽑아서 각각의 그룹만들어주기
#내풀이
import random

class ClassHelper:

    
    def __init__(self, namelist):
        self.namelist = namelist
        
    def pick(self, num):

        result = random.sample(self.namelist, num)
        return result
    
    def match_pair(self):
        result = []
        l = len(self.namelist)
        for i in range(l//2):
            result += [self.pick(2)]
            self.namelist = [x for x in self.namelist if x not in result[i]] 
        if self.namelist != 0:
            result[-1] += self.namelist
        return result
    
#shuffle, pop 활용 풀이
import random 

class ClassHelper:

    
    def __init__(self, namelist):
        self.namelist = namelist
        
    def pick(self, num):

        result = random.sample(self.namelist, num)
        return result
    
    def match_pair(self): 
        random.shuffle(self.namelist) #shuffle 내부 리스트 섞어주기
        pair = []
        pair_count = len(self.namelist)
        
        if pair_count % 2: #홀수
            temp = self.namelist.pop()
            
            while self.namelist:
                s1 = self.namelist.pop()
                s2 = self.namelist.pop()
                pair.append([s1, s2])
            pair[-1].append(temp)
            
        else: #짝수
            while self.namelist:
                s1 = self.namelist.pop()
                s2 = self.namelist.pop()
                pair.append([s1, s2])
        return pair
    
#세 번째 풀이
import random

class ClassHelper:

    
    def __init__(self, namelist):
        self.namelist = namelist
        
    def pick(self, num):

        result = random.sample(self.namelist, num)
        return result
    
    def match_pair(self): 
        random.shuffle(self.namelist) #shuffle 내부 리스트 섞어주기
        pair = []
        pair_count = len(self.namelist) // 2
        
        for idx in range(pair_count):
            
            #맨 마지막 반복문인지 확인 (마지막이면 그냥 끝까지 다묶자)
            if idx == pair_count - 1:
                temp = self.namelist[idx * 2 : ]
                pair.append(temp)
                return pair
			# 두 개씩 묶어서 보내기
            temp = self.namelist[idx * 2 : idx * 2 + 2]
            pair.append(temp)

```

