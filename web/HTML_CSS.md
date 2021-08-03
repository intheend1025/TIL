# HTML

```html
<!DOCTYPE html>
<html lang='ko'>  <!--최상위 요소, 문서의 root-->
<head>  <!--문서제목, 인코딩과 같이 해당 문서 정보 (브라우저에 나타나지 않음)-->
    <meta charset="UTF-8">
    <title>Document</title>
           
</head>
<body> <!--브라우저 화면에 나타나는 정보 -->
    <a href="https://google.com"></a> <!--공백no, 쌍따옴표 사용 -->
        
</body>
</html>
```

1. Open Graph Protocol 메타데이터를 표현하는 새로운 규약 (메타정보에 해당하는 제목 설명 쓸 수 있도록 정의)
2. DOM(document object model) 트리 : 문서의 구조화된 표현을 제공, 동일한 문서 표현 저장 조작하는 방법 제공
3. MDN이 공식 표준 (검색할때 붙여서)
4. 대표적인 태그들
   - header : 머릿말
   - nav : 내비게이션
   - aside : 사이드 공간
   - section : 컨텐츠의 그룹
   - article : 문서 안 독립적으로 구분되는 영역
   - footer : 마지막 부분
   - div 
5. 시맨틱 웹 : 웹에 메타데이터 부여, 거대한 데이터베이스로 구축
6. --<form> 서버에서 처리될 데이터를 제공하는 역할
7. --<input> 사용자의 입력값 받기    
8.  ! tab -> 기본구조 완성



# CSS

스타일, 레이아웃 통해 문서 표시방법 지정하는 언어

```css
h1{ 선택자
    color: blue; 선언
    font-size: 15px; 속성:값
}

<style>
/* 전체 선택자 */
*{
    color: red;
}
/* 요소 선택자 */
h2 {
    color: orange;
}
/* 클래스 선택자 */
.green {
    color: green;
}
/* id 선택자 */
#purple{
    color: purple;
}
/* 자식 결합자 - 바로 아래만 ( + 인접형제 결합자) */ 
.box > p {
    font-size: 30px;
}
/* 자손 결합자 - 아래 모두 ( ~ 일반형제 결합자) */ 
.box p {
    font-size: 30px;
}
```

1. 적용 우선순위 
   - !important(사용시 주의) > 인라인 > id선택자 > **class선택자**(젤많이씀) > 요소선택자 > 소스 순서
2. CSS 상속
   - 상속되는 것 : text관련 요소
   - 상속되지 않는 것 : box model position관련 요소
3. 크기단위
   - em : 상속영향받음 상대적인 사이즈
   - rem : 상속영향 안받음, html의 사이즈 기준으로 배수 단위 가짐
   - viewport : 유저에게 바로 보이게 되는 웹 영역
4. Box model
   - margin (외부여백) > border(테두리) > padding (테두리 안 내부 여백) > content
5. 블록레벨요소
   - div / ul, ol, li / p / hr /form
6. 인라인 요소 (너비, 높이 마진 지정 못함)
   - span / a / img / input, label / b, em, i, strong 등
7. display : none (공간까지 삭제) vs visibility : hidden (공간차지하나 안보이게)
8. CSS position
   - relative : 상대위치 (static위치 기준으로 이동, 자기자리 차지하고있음)
   - absolute : 절대위치 (static이 아닌 가장 가까이 부모/조상요소 기준으로 이동 - 없으면 body기준, 자리 차지하는 공간 없어짐)
   - fixed : 고정 위치 (viewport 기준으로 이동 - 스크롤시에도 같이이동)

```html
color: aliceblue; 폰트색
background-color: blanchedalmond; 배경색
text-align: center; 문자열 정렬
width: 100%; 해당 공간에 꽉차게 만들기
border: 1px solid black; 테두리
border-radius: 4px; 테두리 반경 (모서리 둥글게)
input>placeholder="아이디를 입력 해 주세요." input시 박스에 보이는 값
input>value="로그인" 제출시 누르는값 변경
```

