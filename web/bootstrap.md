# Flexbox

1. Float : 한 요소가 정상 흐름으로부터 빠져 텍스트 및 인라인 요소가 그 주위를 감싸 요소의 좌우측을 따라 배치되어야 함을 지정 (텍스트를 둘러싸는 레이아웃을 위해 도입)
2. Flexbox : 아이템간 공간배분과 정렬기능 제공하기 윈한 1차원 레이아웃 모델로 설계
   - 요소 : Flex container(부모요소), Flex Item(자식요소)
   - 축 : main axis (메인축), cross axis(교차축)
   - 배치 방향설정 : flex-direction
   - 메인축방향 정렬 : justify-content
   - 교차축 방향 정렬 : align-items, align-self, align-content (content여러줄, items한줄, self 개별요소)
3. flex선언시 기본값 : item 행으로 나열, 메인축 시작부터 정렬, 교차축 크기채우기위해 늘어남, nowrap

# Bootstrap

wappalyzer

CDN 이용하여 quickstart

1. Grid system - 12개 column 6개의 grid breakpoints



- `justify-content`
- `align-items`
- `flex-direction`
- `order`
- `align-self`
- `flex-wrap`
- `flex-flow`
- `align-content`



<project>

### 1. nav_footer

```html
<button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
</button>
```

- viewport가 768px 미만일 경우 md 사이즈로 옵션을 주어 햄버거 버튼으로 변경될 수 있도록 하였다. 햄버거버튼이 navbar-toggler-icon인 듯 한데 정확히 내부적으로 어떻게 작동하는 것인지는 좀 더 공부가 필요할 것 같다.

```html
<ul class="navbar-nav ms-auto py-4 py-lg-0">
    <li class="nav-item">
        <a class="nav-link" aria-current="page" href="02_home.html">Home</a>
    </li>
    <li class="nav-item">
        <a class="nav-link active" href="03_community.html">Community</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" data-bs-toggle="modal" data-bs-target="#exampleModal">Login</a>
    </li>
</ul>
```

- 기본 navbar 설정은 왼쪽으로 정렬되고 있었다. 이 때문에 처음엔 d-flex로 정렬을 시도했지만 적용되지않았고 ms-auto를 통해 오른쪽으로 네비게이션 리스트를 붙일 수 있었다. 마진이 왼쪽으로 들어갈 수 있도록 설정해주는 값인듯 하다.

```html
<a class="nav-link" data-bs-toggle="modal" data-bs-target="#exampleModal">Login</a>
```

- 모달의 경우 modal-body에 로그인을 위한 form을 붙이고 togle과 target을 nav에 붙였다. toggle은 모달을 불러오는 것이고 target은 모달중에서도 어떤 것을 불러올 지 설정하는 듯 하다.



### 2. home

```html
<section class="d-flex flex-column justify-content-center flex-sm-row flex-sm-wrap">
```

- d-flex를 사용하여 너비에 따라 카드 수가 바뀌는 반응형 웹을 구성할 수 있었다.
- d-flex는 블록 요소를 inline으로 바꾸어 활용할 수 있도록 하는 것이다.  container와 개념이 헷갈리긴하는데 container는 큰블록을 만들어 해당 블록내에서 조절하는 듯하다. d-flex와 비슷한 것 같긴한데... 복습해야겠다.. 



### 3. community

```html
<table class="d-none d-lg-table table table-striped table-hover">
```

- 이번에는 viewport에 따라 크기가 달라지는 것이 아닌 아예 다른 태그가 작동하게 해야했다. 이 때문에 크기 조절이 아닌 d-none(display)을 통해 태그가 뜨고 안뜨고를 설정할 수 있었다.

