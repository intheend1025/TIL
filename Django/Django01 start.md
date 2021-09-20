# Django

- python web framework

- MVC Design Pattern (model - view - controller)

- Django는 MTV Pattern (model - template - view)

- HTTP Request -> URLS -> [View] (전체 컨트롤) <-data-> Model (데이터 처리)   => 최종 HTTP Response(HTML)

  ​												 <- template (보여지는 부분)



#### 준비사항

- 가상환경 생성 및 활성화
  - `python -m venv <name>`
  - `source <name> /Scripts/activate`
- django 설치 및 프로젝트 생성
  - `pip install django`
  - `django-admin startproject <name> . `( . 은 현재 위치 의미)
- django app 생성 (app설치 후 settings에 등록! )
  - `django manage.py startapp <name> `
- django server 실행
  - `django manage.py runserver`



#### 장고 구조

##### 프로젝트 구조

- init.py : 이 디렉토리를 하나의 패키지처럼
- asgi.py : 비동기식 웹서버와 연결 및 소통 도움
- settings.py : 모든 설정 포함
- urls.py : 사이트의 url과 views의 연결 지정
- wsgi.py : 웹서버와 연결 소통 도움

##### Application 구조

- admin.py 관리자용 페이지 설정
- apps.py 앱의 정보
- models.py 모델 정의하는 곳
- tests.py 테스트 코드 작성하는 곳
- views.py view함수 정의되는 곳



#### 요청과 응답

##### URLS 

- HTTP 요청(request)을 알맞은 view로 전달
  - `from articles import views`
  - `path('index/', views.index)`

##### View

- HTTP 요청 수신하고 응답을 반환하는 함수 작성
  - `def index(request): return render(request, 'index.html')`

##### Templates

- 실제 내용 보여주는 파일
- 파일 구조나 레이아웃 정의



#### DTL language

- variable
  - `{{ variable }}`
  - view에서 정의한 변수를 template 파일로 넘겨 사용
- filters
  - `{{ variable|filter }}`
  - 표시할 변수 수정할 때 사용\
- tags
  - `{% tag %}`
  - 출력 텍스트 만들거나, 반복 또는 논리 수행하여 제어 흐름 만드는 등
- comments
  - `{# #}`
  - 주석 표현