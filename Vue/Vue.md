# Vue 01

- SPA(Single Page Application) 지원
  - 현재 페이지 동적으로 렌더링함으로써 사용자와 소통
  - 단일페이지로 구성, 서버로부터 최초에만 페이지 다운로드,  이후 동적으로 필요한 부분만 DOM구성
  - 동작 원리 일부가 CSR(Client side Rendering)의 구조를 따름
    - 서버에서 화면을 구성하는 SSR(server side)방식과 달리 클라이언트에서 화면 구성
      - SSR 장점 : 초기 구동 속도 빠름 / SEO에 적합
      - 단점 : 모든 요청마다 새로운 페이지 구성하여 전달 (트래픽 많아)
    - 처음엔 뼈대만 받고 브라우저에서 동적으로 DOM그림
    - 장점 : 서버와 클라이언트 간 트래픽 감소 / 사용자 경험 향상
    - 단점 : SSR에 비해 전체 페이지 렌더링 시점 느림 / SEO(검색 엔진 최적화)에 어려움
      - SEO (Search Engine Optimization) 검색 결과 상위에 노출될 수 있도록 
      - SEO 대응위한 별도 프레임워크 Nuxt.js / Next.js
  - 과거엔 MPA(매번 새로운 페이지 응답하는 방식) 이었음
- MVVM Pattern
  - Model : javaScript object , data로 사용
  - View : DOM(HTML) 데이터 변화에 바뀜
  - View Model : Vue instance data와 DOM 관련 처리 (data처리해서 어떻게 보여줄것인지(DOM))
  - 48p
