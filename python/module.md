# Module

1. 모듈
   - 특정 기능을 파이썬 파일 단위로 작성한 것
2. 패키지
   - 특정 기능과 관련된 여러 모듈의 집합
   - 여러모듈/하위 패키지로 구조화
   - 모든 폴더에는 `__init`__.py 를 만들어 패키지로 인식
3. 라이브러리
   - 모듈<패키지<라이브러리
4. 명령어
   -  pip list
   - pip show SomePackage
   - pip install SomePackage
   - pip uninstall SomePackage
   - pip freeze  > requirements.txt (설치목록 파일생성)
   - pip install -r requirements.txt (위 목록대로 설치가능)
5. 가상환경 (venv) 
   - 특정 디렉토리에 가상 환경 만들고 고유한 패키지 집합 가질 수 있음
   - 프로젝트 최상단에 위치
   - 폴더개념으로 묶인거 아님 폴더이동해도 가상환경그대로 이동
   - python -m venv <폴더명>
   - source venv/Scripts/activate (가상환경 활성화)
   - deactivate (비활성화)
6. 사용법
   - import module
   - from module import var, function, class
   - from module import *(전체 불러오기 - but 권장x)
   - from package import module
   - from package.module import var, function, class

