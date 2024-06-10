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
3. specificity 높이기 (.class1 .class1-1는 20점, div.class1 class1-1은 21점) (셀렉터 길게 특정하면 미래에 덮어쓰기 힘드니 짧게 쓰면 좋은듯)

좋은 코드의 원칙
1. 나중에 수정/관리가 쉬움
2. 확장성이 좋으면 좋음

```
.main-button:hover {
	color: red;
}
```
pseudo-class는 특정 요소가 다른 상태일 때 스타일 줄 수 있게 도와줌

```
.pseudo::first-letter {
	color: red;
}
```
```
.pseudo::after {
	content: '안녕';
	color: red;
	font-size: 30px;
}
```
pseudo-element는 내부의 일부분만 스타일 줄 때 (::before, ::after 내부 맨 뒤, 앞에 뭔가 추가할 때 사용)

input같은 일부 요소 스타일링할 때 pseudo-element 사용 가능

```
.input-file::file-selector-button {
  background-color: aquamarine;
}

<input type="file" class="input-file">
```
pseudo-element는 약간 쓸모 없다


크롬 설정에서 'Show user agent shadow DOM' 체크하고 html 확인하면 숨겨져있던게 보인다.
거기 붙어있는 속성 중에 pseudo="-webkit-file-upload-button" 이런거 있는데 
```
input[type="file"]::-webkit-file-upload-button {
  display: none;
}
```
이렇게 스타일을 주면 된다. 참고로 -webkit-은 크롬에서만 적용되는 스타일이라는 뜻.

```
<label for="fileInput">안녕</label>
<input type="file" id="fileInput" class="input-file">
```
input은 display:none; 해놓고 label에 스타일 주기도 함

input type="range"같은건 개발자 도구로 검사해봐도 뭐 안 나오는데 그럴 땐 아래에 있는 user agent stylesheet(브라우저 기본 css) 찾아보면 나온다. 따로 스타일 적용하고 싶으면 apperance: none; 전부 다 줘야됨


Sass 활용법
```scss
$메인칼라 : #2a4cb2;
$서브칼라 : #eeeeee;
$기본사이즈 : 16px;

.background {
  background-color: $메인칼라;
  font-size: ($기본사이즈 - 2px);
}
```
1. 변수문법 : 어려운 단어, 숫자 기억

css에서도 var 쓰면 변수문법 가능하고 calc 쓰면 사칙연산 가능하긴 함. (css에선 scss와 다르게 %랑 +- 섞어 써도 알아서 잘 해줌)

.scss와 .sass 파일의 차이 : .sass는 괄호 없어도 Indent 넣으면 됨

```scss
.main-bg h4 {

}

.main-bg {
  h4 {

  }
  button {
    
  }
}
```
2. nesting 문법 : 관련있는 class들 묶을 때 사용  (두 개 이상 중첩 굳이 ㄴㄴ)

```scss
%btn {
  width: 100px;
  height: 100px;
  padding: 10px;
}

.btn-green {
  @extend %btn;
  color: green;
}
```
3. @extend 문법 : 중복된 스타일들을 묶어서 %임시클래스명 만듬  (% 빼도 되긴 한데 임시 클래스는 extend 안되면 단독으로 컴파일되지 않음

```scss
@mixin 작명($구멍, $구멍2, $구멍3) {
	font-size: $구멍;
	letter-spacing: $구멍2;
	#{ $구멍3 }: -1px;
}

h2 {
	@include 폰트스타일(40px, 1px, width)
}
```
4. @mixin 문법 : 긴 코드를 짧은 단어로 축약할 때 씀
4. @mixin 문법의 $파라미터 : 긴 코드를 가변적으로 만들 때 씀
4. 글자 중간에 $변수나 $파라미터 넣을 땐 #{ $변수명 }

```scss
@use 'reset'; /* reset.scss에 있는 코드들 적용 */
```
5. @use '파일경로' : 다른 파일에 있는 내용 가져오고 싶을 때 (종속된 scss 파일은 파일명에 언더바 `_` 붙여야 컴파일 안함.)
5. 다른 파일의 @mixin 쓰려면 @include 파일명.mixin이름 (혹은 변수명)


비디오 넣는 방법들
```html
<video src="bridge.mp4" controls></video>

/* 호환성 챙길 수 있음 (첫번째거 재생 안되면 두번째거 재생) */
<video controls autoplay muted preload="none">
  <source src="bridge.mp4" type="video/mp4">
  <source src="birdge-m.webm" type="video/mp4">
</video>
```
 controls : 재생됨 
 autoplay muted : 자동 재생
 poster="경로" : 썸네일 이미지
 loop : 무한반복

preload="none" 미리다운X
preload="auto" 미리다운O
preload="metadata" 미리다운 적당히


오디오 넣는 방법
```html
<audio src="bass.mp3" controls></audio>
```
muted : 음소거 상태로 시작
autoplay : 자동재생인데 javascript 만져야 가능 
preload : video와 동일


애니메이션 관련 속성들
```css
.ani-text {
	transform: rotate(10deg);
	transform: translateX(100px);
}
```
rotate : 요소 회전
translateX : x축 좌표 이동 (애니메이션 줄 때 margin보다 부드럽고 성능좋게 이동)


```css
@keyframes 왔다갔다 {
  0% {
    transform: translateX(0);
  }
  50% {
    transform: translateX(100px);
  }
  100% {
    transform: translateX(0);
  }
}

.ani-text:hover {
  animation: 왔다갔다 1s infinite;
}
```
@keyframe으로 복잡한 애니메이션 정의 가능

infinite : 애니메이션 계속 반복
forwards : 애니메이션 결과 유지

```
.box:hover {
  animation-name : 움찔움찔;
  animation-duration : 1s;
  animation-timing-function : linear; /*베지어 주기*/
  animation-delay : 1s; /*시작 전 딜레이*/
  animation-iteration-count : 3; /*몇회 반복할것인가*/
  animation-play-state : paused;  /*애니메이션을 멈추고 싶은 경우 자바스크립트로 이거 조정*/
  animation-fill-mode: forwards;  /*애니메이션 끝난 후에 원상복구 하지말고 정지*/
}
```
애니메이션 세부 속성


**성능 잡을 수 있는 여러 방법1. will-change 쓰면 됩니다.**

```
.box {
  will-change: transform;
} 
```

애니메이션을 주는 .box가 약간 느리게 동작한다면 

will-change : 애니메이션줄속성;

이걸 써놓으면 성능개선이 가능합니다. 바뀔 내용을 미리 렌더링해주는 속성이라 그렇습니다.
뭔가 이상하게 버벅일 때만 쓰시고 애니메이션이 스무스하게 잘 된다면 쓸 이유는 없습니다.
이상하게 많이 쓰면 브라우저 자체가 더 느려질 수 있습니다.

[https://dev.opera.com/articles/ko/css-will-change-property/](https://dev.opera.com/articles/ko/css-will-change-property/)


**성능 잡을 수 있는 여러 방법2. 하드웨어 가속**

애니메이션이 너무 많아 CPU만으로 전부 연산이 불가능하다면
GPU의 도움을 받을 수도 있습니다.

```
.box {
  transform: translate3d(0, 0, 0);
}
```

transform : translate3d를 쓰면 3D 이동도 가능한데
이 속성의 경우 GPU를 사용해서 연산하게 됩니다.
그래서 translate3d(0, 0, 0) 이런 식으로 아무데도 움직이지 않는 3D 이동명령을 주고
뒤에 필요한 transform을 더 적용한다면 
GPU를 이용해서 .box가 가진 transform 속성들을 연산할 수 있습니다. 
꼭 써야하는건 아니고 뭔가 느리게 동작한다면 써볼 수 있는 것들입니다.



```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 100px 100px;
  grid-gap: 10px;
}
.grid-container div {
  border: 1px solid black;
}

<div class="grid-container">
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
</div>
```
그리드 만들기 예제
- fr 써서 프레임 단위로 폭 지정 가능하다 (rows는 height가 있어야 fr으로 지정 가능)
- grid-gap으로 격자 사이 간격 지정 

```css
.grid-nav {
  grid-column: 1/5;
}

<div class="grid-container">
	<div class="grid-nav"></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
</div>
```
레이아웃 만드는 법 1. 내부 박스에 gird-column/row 옵션 주기
grid-column : 세로선 1 ~ 4 만큼 차지해주세요
gird-row : 가로선을 차지해주세요

레이아웃 만드는 법 2. 그리드 area
```css
.grid-container {
  display: grid;
  grid-template-columns: 100px 100px 100px 100px;
  grid-template-rows: 100px 100px 100px;
  grid-template-areas :
	"헤더 헤더 헤더 헤더"
	"사이드 . . . "
	"사이드 . . . "
}
.grid-nav {
  grid-area: 헤더;
}
.grid-sidebar {
  grid-area: 사이드;
}

<div class="grid-container">
	<div class="grid-nav"></div>
	<div class="grid-sidebar"></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
</div>
```

그리드 안에 들어가있는거 안 빠져나오게 하려면
```css
.grid-container2 img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

position : sticky는 조건부로 poisition : fixed가 됨.
스크롤하다가 만났을 때 부모 요소 끝날때까지 고정됨.