# Django02

### Model

- 단일한 데이터에 대한 정보를 가짐
- 모델을 통해 데이터에 접속하고 관리
- 각각의 model은 하나의 데이터베이스 테이블에 매핑 됨
- 웹 어플리케이션의 데이터를 구조화하고 조작하기 위한 도구

### Database

- 체계화된 데이터의 모임
- Query : 데이터를 조회/추출/조작하기 위한 명령어 
- 기본구조
  - 스키마 : 자료의구조, 표현방법, 관계 정의한 구조(structure)
  - 테이블: 열(column) : 필드, 속성 / 행(row) : 레코드, 튜플
  - PK(기본키) - Primary key : 각행의 고유값

### ORM

- object-relational-mapping
- 시스템간 데이터를 변환하는 기술 (Django - SQL)
- SQL 알지 못해도 DB조작가능 & 높은 생산성
- but 완전한 서비스 구현 어려움
- DB를 객체로 조작하기위해 ORM 사용

### CRUD

- Create, Read, Update, Delete
- `article = Article(title='second', content='django!!')`
- `article.title = 'first'`
- `article.content = 'django!'`
- `article.save()`
- `Article.objects.create(title='third', content='django!!!')`

articles/get = 게시글 목록 좀 줘

articles/post = 게시글 좀 작성해줘