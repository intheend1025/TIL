# Django 06

### Rest API

#### HTTP

- HyperText Transfer Protocol
- 웹 상에서 컨텐츠 전송하기 위한 약속
- HTML 문서 같은 리소스 가져올 수 있도록 하는 프로토콜 (규칙, 약속)
- 요청(request : 클라이언트에 의해 전송되는 메시지) / 응답(response : 서버에서 응답으로 전송되는 메시지)
- stateless, connectless - > 쿠키와 세션 통해 서버 상태를 요청과 연결하도록 함
- url 구조
  - scheme(protocol) 
  - Host(domain name) 
  - Port (gate) 
  - Path(웹서버상 리소스 경로) 
  - Query(Identifier) 
  - Fragment(Anchor 북마크)



### API

- 다른 서비스에 요청을 보내고 응답 받기 위해 정의된 명세
- REST : API 서버를 개발하기 위한 일종의 소프트웨어 설계 방법론
  - 자원 : URI
  - 행위 : HTTP Method (GET, POST, PUT, DELETE)
  - 표현 : JSON으로 표현된 데이터 제공
- JSON (Javascript object notation) : 자바스크립트 표기법을 따른 단순 문자열
  - 사람이 읽거나 쓰기 쉽고 기계가 파싱(해석,분석)하고 만들어내기 쉬움
  - key-value형태의 구조
- Serialization
  - 직렬화
  - 데이터구조나 객체 상태를 동일하거나 다른 컴퓨터 환경에 저장하고 나중에 재구성할 수 있는 포맷으로 변환하는 과정 

