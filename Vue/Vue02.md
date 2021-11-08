# Vue 02

#### SFC (Single File Component)

- 컴포넌트 : CS에서는 다시 사용할 수 있는 범용성을 위해 개발된 소프트웨어 구성요소 (기본 HTML 엘리먼트 확장)
  - 유지보수, 재사용성
  - vue 컴포넌트 === vue 인스턴스 === .vue 파일
  - 각 기능 별로 파일 나눠 개발
  - Vue 컴포넌트는 const app = new Vue({}) 의 app을 의미

#### Vue CLI

- vue.js 개발을 위한 표준 도구
- node.js : 자바스크립트를 브라우저가 아닌 환경에서도 구동할 수 있도록 하는 자바스크립트 런타임 환경
- 설치 `npm install -g @vue/cli`
- 프로젝트 생성 `vue create my-first-app`
- 디렉토리 이동 `cd my-first-app`
- 서버실행 `npm run serve`

#### Babel

- JS compiler
- ECMAScript 2015+ 코드를 이전 버전으로 번역/변환해주는 도구

#### Webpack

- static module bundler
- 모듈간의 의존성 문제 해결하기 위한 도구
- 프로젝트에 필요한 모든 모듈 매핑하고 내부적으로 종속성 그래프 빌드
- 모듈은 파일 하나 의미
- 모듈 의존성 문제 해결해주는 작업 Bundling
- 여러 모듈 하나로 묶어줌

#### Vue 프로젝트 구조

- node_modules : 노드.js 환경의 여러 의존성 모듈
- public/index.html : vue앱의 뼈대가 되는 파일
- src/assets : webpack에 의해 빌드 된 정적 파일
- src/components : 하위 컴포넌트들이 위치
- src/App.vue : 최상위 컴포넌트
- src/main.js : entry point, DOM과 data연결과 동일한 작업 이루어지는곳, 전역모듈 등록
- package.json : 프로젝트 종속성 목록과 지원되는 브라우저에 대한 구성 옵션
- package-lock.json : 노드 모듈 의존성 설정 및 관리, 종속성 설치 보장, 패키지 버전 고정, 의존성 패키지 충돌 방지

- 컴포넌트 작성 : 부모- 자식
  - 부모는 자식에게 데이터 전달(Pass props), 자식은 자신에게 일어난 일 부모에게 알림(Emit event)
  - props는 아래로 , events는 위로
- 컴포넌트 등록
  - 불러오기 / 등록하기 / 보여주기
- props : 상위 컴포넌트의 정보를 전달하기 위한 사용자 지정 특성
  - 자식 컴포넌트의 템플릿에서 상위 데이터 직접 참조 불가
  - 단방향 바인딩

#### Vue Router

- 라우트에 컴포넌트를 매핑한 후, 어떤 주소에서 렌더링할 지 알려줌 (라우터:위치 최적경로지정)
- 
