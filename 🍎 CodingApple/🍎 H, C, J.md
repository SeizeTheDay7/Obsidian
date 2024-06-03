이미지 가운데 정렬하는 방법
```html
display:block; // div,p, h 등은 block 속성을 이미 갖고 있어서 생략 가능
margin-left: auto; 
margin-right: auto;
```

**vw** : 현재 창 크기에 비례한 크기
**%** : 부모 사이즈에 비례한 크기

자주 사용하는 글자 스타일들
```html
font-size : 20px; 
font-family : 'gulim'; 
color : black; 
letter-spacing : -1px; 
text-align : center; 
font-weight : 600;
```

style은 클래스로 선언하고,
id는 javascript를 위해 사용한다.

**스타일 겹칠 때 우선순위** : 태그에 style > id > class > tag

**display: block** : 가로 행을 전부 차지하게 해주셈

> [!NOTE]
> 레이아웃 전체를 감싸는 박스를 만들어두면 유용하다. 
> class="container"인 박스 하나로 감싸고 시작하자. 
> 이를 wrapper 박스, container 박스라고 한다.

**width: 100%;** : 부모 태그 width의 100%를 의미

**div 가로로 정렬하는 방법**
``` css
float: left; // 왼쪽으로 정렬해주셈. 
// 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지의 왼쪽이나 오른쪽으로 이동함.
float : none; 또는 clear: both;  // float 다음 요소에 주면 float로 발생하는 버그 해결
```
간격 조절하고 싶으면 `<div>`하나 넣고 거기에 `clear: both` 넣어주면 된다.

```html
display: inline-block; 스타일에 주고

<div class="a"></div><div class="b"></div> 줄바꿈 없이 태그 작성하면 잘 정렬됨

<div class="a"></div><!--
--><div class="b"></div> 중간에 주석 넣고 엔터키 쳐도 되긴 함

안에 글씨 쓰면 이상해짐. vertical-align: top; 넣으면 해결되긴 함.
```
**display: inline-block** : 내 크기만큼 차지하게 해주셈

**display: flex;** 는 하위 요소에 상속이 안된다.

PC 레이아웃을 만들 때 항상 전체를 감싸는 container 또는 wrap 박스를 만들어 놓는게 좋다.
그리고 그 박스엔 항상 width를 지정해놓는게 좋다. 그래야 나중에 브라우저 화면이 축소돼도 내부 div 박스들이 찌그러지지 않는다.

li에 display: inline-block 주면 가로로 정렬 가능

>[!bug]
> `<link href="/css/main.css" rel="stylesheet">` 이러면 오류 생긴다
> `<link href="css/main.css" rel="stylesheet">` 슬래시 빼줘야 함

**background-size: cover** 빈 공간 없이 배경으로 꽉 채워라
**background-size: contain** 배경 짤리면 안된다

>[!bug] magin collapse 현상
>박스 2개가 위쪽 테두리가 겹쳐지면 margin도 합쳐져서 설정 하나만 바꿔도 다른거 따라감.
>해결책 : 부모 박스에 padding 조금 주면 된다

position 움직이기
```CSS
position: relative;
top: 100px;
```

position: absolute 붙은 요소 가운데 정렬
```css
  position: absolute;
  left: 0;
  right: 0;
  margin: auto;
  width: 200px;
```

>[!bug] z-index 붙여도 가려짐
>position 속성 안 붙어있으면 같은 stacking context가 아니라서 z-index 효과 없음
>

**max-width의 쓰임새**
반응형 웹페이지 만들 때 단위에 % 넣곤 하는데, 이때 PC 화면에서는 너무 커보이니까 max-width를 설정한다. min/max - width/height 다 가능하다. 

max 설정해놨어도 padding 넣으면 더 커질 수 있다. width는 content의 크기를 의미하므로 border, padding 같은 것과는 관계가 없기 때문이다.

이럴 땐 box-sizing: border-box로 설정하면 된다. box-sizing: content-box 설정하면 원래대로 content 최대 크기만 설정 가능.

>[!note] 시작할 때 선언해놓으면 좋은 것들
>div { box-sizing : border-box; } 
>body { margin : 0; } 
>html { line-height : 1.15; }

호환성 이슈 해결책부터 첨부하기도 함. 검색 키워드 : normalize.css
css 파일에 복붙하거나 다운 받아서 link 태그로 첨부하기.

class 재활용해서 css 중복 안되게 하면 고수

```html
<input id="sub" type="checkbox">
<label for="sub"> Subscribe</label>
```
이렇게 하면 "Subscribe" 누르면 체크박스도 같이 체크됨

input에 box-sizing: border-box 줘야 폭이 padding을 포함해서 조금 커질 수 있다.
콤마 찍어서 div, textarea, input 등 태그에 box-sizing 주자.

글씨간의 세로정렬할 때 vertical-align 사용한다.

display: inline : 항상 옆으로 채워지는 **폭과 너비가 없는 요소** (옆에 쓰는대로 옆으로 채워짐)

div에 style="display: table"을 넣으면 table이랑 비슷하게 동작
display: table-row 넣으면 tr 됨
display: table-cell 넣으면 td 됨

`<button>`에 cursor: pointer; css 주면 마우스 갖다대면 커서 바뀜
마우스 올릴 때 스타일은 :hover (이를 pseudo-class라 부름)
클릭 중 스타일은 :active
커서 찍혀있을 때 스타일은 :focus
```css
.btn:hover{
	background-color: chocolate;
}
```

스타일 설정할 때 :hover → :focus → :active 순서대로 적어야 한다

a 태그에 text-decoration: none; 적용하면 링크 아래에 있는 밑줄제거
방문 전 링크 스타일링은 :link
방문 후 링크 스타일링은 :visited
어차피 외워도 다 까먹으니까 필요할 때 찾아쓰자

뼈대 클래스와 살점 클래스(background-color 등)로 나눠서 묶기
font-size같은거 utility class로 선언해두기

class 작명할 때 BEM(Block__Element--Modifier) 룰 따라보기
class="덩어리이름__역할--세부특징"
```html
<div class="profile">
  <img class="profile__img">
  <h4 class="profile__h4">이름</h4>
  <p class="profile__content">소개글</p>
  <button class="profile__button--red">빨간버튼</button>
  <button class="profile__button--blue">파란버튼</button>
</div>
```
리액트나 vue같은 거에선 필요 없음. 알아두기만 하자.


**사용자의 컴퓨터에 설치되지 않은 폰트를 사이트에서 이용하려면**
```css
@font-face {
  font-family : '이쁜폰트';
  src : url(./font/NanumSquareR.woff);
}
@font-face {
  font-family : '이쁜폰트';
  font-weight : 800;
  src : url(./font/NanumSquareB.woff);
}
```
css 파일 최상단에 @font-face 라는 명령어를 넣고, url() 안에 적용할 폰트의 경로와 이름 적기.
클래스에서 font-family: '이쁜폰트' 사용하면 해당 폰트 적용해줌.
'이쁜폰트' 쓸 때 font-weight 800 주면 굵은 폰트 따로 적용됨.

용량 줄이려면 .woff 쓰셈

```css
p, h3, h3, h2, h1, span {
	transform : rotate(0.03deg);
} 
```
폰트 부드럽게 처리하려면 회전시켜보셈


1. css/main.css
2. /css/main.css
1번은 현재 HTML파일과 같은 경로에 있는 css라는 폴더 내의 main.css 파일을 의미하고
2번은 현재 사이트의 메인경로 (codingapple.com)부터 시작해서 codingapple.com/css/main.css 파일을 첨부해라 라는 뜻입니다.
슬래쉬 기호가 첨부터 붙어있으면 사이트 메인경로부터 시작해라~ 라는 의미입니다.


**header에 넣는 태그들**

여러가지 meta 태그
```html
<head>
  <meta charset="UTF-8">
  <meta name="description" content="html 잘하는 코딩애플입니다.">
  <meta name="keywords" content="HTML,CSS,JavaScript,자바스크립트,코딩">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

1. 사이트 인코딩 형식 지정 : charset="UTF-8"
2. 사이트 검색 결과 화면에 뜨는 문구
	- description : 구글 검색 시 파란 제목으로 뜨는 글귀
	- keywords : 검색에 도움을 주는 키워드
3. 사이트 초기  zoom 레벨이나 폭 지정 : name="viewport"
	- width=device-width : 모바일 기기의 실제 폭으로 렌더링. 반응형 웹에 필요
	- initial-scale : 접속 시의 화면 줌 레벨

open graph
```html
<head>
  <meta property="og:image" content="/이미지경로.jpg">
  <meta property="og:description" content="사이트설명">
  <meta property="og:title" content="사이트제목">
</head>
```
링크 공유할 때 썸네일 설정

favicon
```
<head> <link rel="icon" href="아이콘경로.ico" type="image/x-icon"> </head>
```
웹사이트 제목 옆에 뜨는 아이콘 커스터마이징
- ico 대신 png 파일 가능. ico가 호환성은 가장 좋다. 
- 32 x 32 사이즈로 제작하면 됨
- 바탕화면 바로가기 아이콘 수정 : rel="apple-touch-icon-precomposed" 등 OS 별로 요구하는 속성이 다른데 favicon generator 검색해보면 OS별로 알아서 만들어줌

media query 문법 (css 파일 맨 아래에 적어주자)
```css
@media screen and (max-width: 1200px){
  .main-title {
    font-size: 20px;
  }
}
```
1200 이하로 작아지면 글씨 크기 작아지게 하는 방법
여러개 쓰면 크기 구간 별 설정 가능

(참고) breakpoint 기준 px값은 다른사람 따라하는 걸 권장
1200px / 992px / 768px / 576px 단위들을 많이 사용함
1200px 이하는 태블릿, 768px 이하는 모바일


인터넷 익스플로러 호환성 확인하려면 인터넷 익스플로러에서 F12 - 에뮬레이션
IE 호환성 잡으려면 css 파일 따로 또 적용시켜줄 수 있음

awesomefont라는 라이브러리 쓰면 아이콘 쓸 수 있음
```html
<i class="fa-solid fa-star fa-3x"></i>
```
이런 거 복붙하면 됨

```css
.flex-test i {
  background-color: burlywood;
  width: 100px;
  height: 100px;
  border-radius: 50px;
  padding-top: 25px;
  box-sizing: border-box;
  color: white;
}
```
이렇게 스타일 주면 원형 배경에 색깔도 줄 수 있는데, 가운데로 안 들어가면 부모 요소의 text-align 속성 center로 주면 됨. (그냥 flex로 가운데 맞춰버리기)

**호버 시 까매지는 애니메이션**
img 위에 div 하나 추가하고 부모 요소에는 style="position: relative" 추가, 
까매질 div(width: 100%)에는 position: absolute 추가. 이렇게 하면 일단 덮긴 한다. 
원래 img랑 크기 살짝 차이나는데 이건 img에 display: block; 주면 된다. 
이제 div에 opacity: 0.5 추가하거나 rgba(0,0,0,0.5) 추가(이렇게 하면 opacity는 0부터 1까지로)
div클래스명:hover에 opacity: 1 추가하면 마우스 올릴 때 까매짐
아직까진 애니메이션이 아니니까 div에 transition: all 1s; 추가하면 "뭐 변하면 1초에 걸쳐 변경"
div에 transition-timing-function 추가하면 바뀌는 속도 조절할 수 있음 

one-way 애니메이션 만드는 step
1. 시작 스타일 만들기
2. 최종스타일 만들기
3. 언제 최종스타일로 변하는지
4. transition으로 애니메이션

overflow : hidden은 넘치는 부분을 잘라 없애주고
overflow : visible은 넘치는 부분을 그대로 보여주고
overflow : scroll은 넘치는 요소를 보기 위한 스크롤바 생김

transition 세부 속성
```css
.box {
  transition-delay: 1s; /* 시작 전 딜레이 */
  transition-duration: 0.5s; /* transition 작동 속도 */
  transition-property: opacity; /* 어떤 속성에 transition 입힐건지 */
  transition-timing-function: ease-in; /* 동작 속도 그래프조정 */
}
```

크롬 F12 점 세개 More tools - animation 누르면 다른 사이트에서 보이는 애니메이션을 분석할 수 있다

**부트스트랩**
부트스트랩은 편하게 반응형을 디자인할 수 있다
.row 안에 .col 사용하면 균일하게 쪼개기 가능
가로로 쪼개고 싶으면 col-차지할칸크기
.col은 내부를 12칸으로 쪼개주는 class명
이렇게 쪼갠걸 반응형으로 만드려면 -조건문 더하면 된다.
col-md-6 < md 사이즈 이상에서만 적용해라


order-first 부착해서 div 순서 재배치도 가능


css 덮어쓰기 하려면
1. 그냥 같은 클래스명 하단에 쓰기
2. 우선순위 높이기 (class는 10점, id는 100점, 인라인 style=""은 1000점, !important 붙은건 무조건 10000점) (비추)
3. specificity 높이기 (.class1 .class1-1는 20점, div.class1 class1-1은 21점)