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