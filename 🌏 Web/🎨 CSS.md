- [[#General|General]]
- [[#맨 처음 선언할만한 스타일|맨 처음 선언할만한 스타일]]
- [[#CSS 선택자|CSS 선택자]]
- [[#테이블 테두리 둥글게 만들기|테이블 테두리 둥글게 만들기]]
- [[#CSS 변수 선언|CSS 변수 선언]]
- [[#배경 관련 속성|배경 관련 속성]]
- [[#CSS 상대 단위|CSS 상대 단위]]
- [[#중앙 정렬하는 방법|중앙 정렬하는 방법]]
- [[#속성|속성]]
	- [[#속성#inline, block, inline-block의 차이|inline, block, inline-block의 차이]]
	- [[#속성#vertical-align|vertical-align]]
	- [[#속성#background-size|background-size]]
	- [[#속성#margin|margin]]
	- [[#속성#Position|Position]]
	- [[#속성#::before와 ::after|::before와 ::after]]
- [[#Flexbox|Flexbox]]
	- [[#Flexbox#justify-content : 요소를 가로선 상에서 정렬|justify-content : 요소를 가로선 상에서 정렬]]
	- [[#Flexbox#align-items : 요소를 세로선 상에서 정렬|align-items : 요소를 세로선 상에서 정렬]]
	- [[#Flexbox#flex-direction : 정렬 방향 지정|flex-direction : 정렬 방향 지정]]
	- [[#Flexbox#flex-wrap : 몇 줄에 걸쳐 정렬할지 지정|flex-wrap : 몇 줄에 걸쳐 정렬할지 지정]]
	- [[#Flexbox#align-content : 여러 줄 사이의 간격 지정|align-content : 여러 줄 사이의 간격 지정]]
	- [[#Flexbox#flex-grow : flexbox 내에서 차지하는 크기 지정|flex-grow : flexbox 내에서 차지하는 크기 지정]]
	- [[#Flexbox#flex-shrink : flexbox 내에서 상대적으로 작아짐|flex-shrink : flexbox 내에서 상대적으로 작아짐]]
- [[#부트스트랩|부트스트랩]]
	- [[#부트스트랩#`container` 클래스의 주요 기능과 효과|`container` 클래스의 주요 기능과 효과]]
	- [[#부트스트랩#색상 (Colors)|색상 (Colors)]]
	- [[#부트스트랩#여백과 패딩 (Spacing)|여백과 패딩 (Spacing)]]
	- [[#부트스트랩#여백 (Margin)|여백 (Margin)]]
	- [[#부트스트랩#패딩 (Padding)|패딩 (Padding)]]
	- [[#부트스트랩#디스플레이 (Display)|디스플레이 (Display)]]
	- [[#부트스트랩#Flexbox|Flexbox]]
	- [[#부트스트랩#텍스트 (Text)|텍스트 (Text)]]
	- [[#부트스트랩#배경 (Background)|배경 (Background)]]
	- [[#부트스트랩#테두리 (Borders)|테두리 (Borders)]]
	- [[#부트스트랩#크기 (Sizing)|크기 (Sizing)]]
	- [[#부트스트랩#섀도우 (Shadows)|섀도우 (Shadows)]]
	- [[#부트스트랩#가시성 (Visibility)|가시성 (Visibility)]]
	- [[#부트스트랩#포지션 (Position)|포지션 (Position)]]
- [[#Bugs|Bugs]]
	- [[#Bugs#css stylesheet 추가할 때 슬래시|css stylesheet 추가할 때 슬래시]]
	- [[#Bugs#margin collapse 현상|margin collapse 현상]]
	- [[#Bugs#z-index 붙여도 가려짐|z-index 붙여도 가려짐]]
	- [[#Bugs#border로 이미지 가리는 애니메이션 줄 때 테두리 어색함|border로 이미지 가리는 애니메이션 줄 때 테두리 어색함]]
	- [[#Bugs#부트스트랩 col 사이에 gap이 안 주어짐|부트스트랩 col 사이에 gap이 안 주어짐]]
	- [[#Bugs#transform: scale 주면 텍스트가 도망감|transform: scale 주면 텍스트가 도망감]]


## General
<hr>

-  img 태그는 style 생략하고 `width="100%"` 이런 식으로 넣어도 된다
-  화면 꽉 채우는 방법 : `min-height: 100vh`
- ul 스타일
```css
ul {
  list-style-type: none; /* 리스트 스타일 없애기 */
  padding-left: 0; /* 기본 패딩 제거 */
}
```

## 맨 처음 선언할만한 스타일
<hr>

```css
table {
  border-collapse: collapse; /* 테이블 틈 없애기 */
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
```

반응형 웹 디자인 관련
```html
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
```

`width=device-width` : 웹 페이지의 너비를 장치 화면의 너비에 맞추도록 지정
`initial-scale=1` : 웹 페이지의 초기 줌 레벨을 100%로 설정
`shrink-to-fit=no` : iOS 9 이상에서 웹 페이지가 화면에 맞추어 렌더링되는 것을 방지

## CSS 선택자
<hr>

```CSS
/* 모든 태그에 적용하고 싶을 때 */
* {
    속성: 선택지;
}

/* 특정 태그를 지칭할 때 */
태그 {
    속성1: 선택지1;
    속성2: 선택지2;
}

/* 클래스 이름 앞에는 .을 찍는다. */
.클래스 {
    속성: 선택지;
}

/* 아이디 앞에는 #을 붙인다. */
#아이디 {
    속성: 선택지;
}

/* 특정 클래스를 갖는 특정 태그를 지칭할 때는 클래스를 뒤에 붙여 쓴다 */
태그.클래스 {
    속성: 선택지;
}

/* 자식 선택자는 > 뒤에 적는다 */
/* 즉, 아래는 '아이디'라는 아이디를 갖는 요소 바로 안의 '태그' 태그를 선택한 것이다 */
#아이디 > 태그 {
    속성: 선택지;
}

/* 자손 선택자는 띄어쓰기로 구분한다. */
/* 즉, 아래는 '클래스'라는 클래스를 갖는 '태그1' 태그 안에 있는 모든 '태그2'를 선택한 것이다 */
태그1.클래스 태그2 {
    속성: 선택지;
}

/* 속성 선택자 기본 형식 */ 
태그[속성명="값"] { 
	속성: 선택지; 
}

/* 여러 태그에 함께 적용 */
/* 태그1 태그1_1, 태그1_2 로 하면 {태그1 태그1_1}과 {태그1_2}가 선택되므로, 엄격하게 태그1 태그1_1, 태그1 태그1_2 이렇게 지정해주자 */
태그1, 태그2, .클래스 {
	속성: 선택지;
}

/* 특정 순서에 있는 요소만 선택 */
/* even, odd 넣으면 짝수, 홀수에만, 3n+0 넣으면 3의 배수에만 */
태그:nth-childe(3) {
	속성: 선택지;
}

```





## 테이블 테두리 둥글게 만들기
<hr>

**방법 1.** separate 방식

```css
border-collapse: separate;
border-spacing: 0; /* 셀 간의 간격 없애기 */
border-radius: 15px;
```

셀 간의 공간을 없애는 `border-collapse: collapse;`을 적용하면 border-radius와 충돌하여 둥근 테두리가 적용되지 않는다. 

**방법 2.** collapse 방식

```css
table {
  border-collapse : collapse;
  border-spacing : 0;
}

(왼쪽위에있는 td) {
  border-top-left-radius : 5px;
}
```

**방법 3.** box-shadow로 가짜 테두리 만들기

```css
table {
  border-collapse : collapse;
  border-radius : 7px;
  border-style : hidden;
  box-shadow : 0 0 0 1px #666;
}
```


## CSS 변수 선언
<hr>

```css
:root {
	--main-font-color: #000f22;  /* CSS 전역 변수 선언 */
}

div {
	left: calc(var(--left) * 1%);   /* CSS 변수 사용 */
}
```
변수 맨 앞에 `--`를 붙이면 변수 선언 된다. 변수 호출할 땐 var(변수명) 으로 사용한다.


## 배경 관련 속성
<hr>

```css
background-image: url(../img/shoes.jpg);
background-size: cover;  /* 이미지 크기에 맞게 조절 */
background-repeat: no-repeat; /* 이미지 반복 없음 */
background-position: center; /* 이미지 중앙에 위치 */
background-attachment: fixed; /* 스크롤 시 이미지 고정 */
filter: brightness(70%); /* 이미지 어둡게 */
```
`background-size: cover` 빈 공간 없이 배경으로 꽉 채워라
`background-size: contain` 배경 짤리면 안된다


## CSS 상대 단위
<hr>

<h4> vh, vw, vmin : 화면 전체 상대 길이</h4>
`vh` : viewport height (100이 최대)
`vw` : viewport width
`vmin` : viewport minimum, 뷰포트의 높이와 너비 중 더 작은 길이
(%는 부모 요소의 길이에 연관됨)

<h4>em, rem : font-size 기준 크기</h4>
[정리글](https://www.daleseo.com/css-em-rem/)

<h4>계산 방식</h4>
1em = 16 px x 1 = 16px
2em = 16 px x 2 = 32px

`em` : 해당 단위가 사용되고 있는 요소의 font-size 값 기준 (font-size는 부모에게 상속받을 수 있음)
`rem` : 루트 요소 `<html>` 의 font-size 기준


## 중앙 정렬하는 방법
<hr>

1.
``` CSS
display:block; // div,p, h 등은 block 속성을 이미 갖고 있어서 생략 가능
translate(-50%, -50%)는 요소를 그의 X축과 Y축 위치에서 각각 50% 만큼 이동시킴.
position: absolute와 함께 사용하면 부모 컨테이너 내 중앙에 정확히 위치시킬 수 있음.
해당 개체 크기의 절반을 의미하는 것이기 때문. translateX(50%)를 사용하면 x축 위치만 변경.
```


2.
``` CSS
margin-left: auto; 
margin-right: auto; 
```

3.
```css
text-align: center;
display: flex;
justify-content: center;
align-items: center;
flex-direction: column;
```

버튼 안에 있는 텍스트 수직 정렬
```css
.orange-button{
	display: flex;
	align-items: center;
}
```


## 속성

### inline, block, inline-block의 차이
<hr>

**display: inline**
- 다른 요소와 나란히 배치
- width, height 무시
- `<span>`, `<a>`,`<em>` 

**display: block**
- 혼자서 한 줄 차지
- width, height, margin 등 모두 반영됨
- `<div>`, `<p>`, `<h1>`

**display: inline-block**
- 다른 요소와 나란히 배치
- width, height, margin 등 모두 반영됨
- `<button>`, `<input>`, `<select>`

### vertical-align
<hr>

vertical-align: top/middle/bottom : 상중하 정렬 
vertical-align: super/sub : 위첨자 아래첨자

![](Pasted%20image%2020240516213933.png)
1. inline/inline-block 요소 간의 세로 정렬할 때 사용 

2. `<table>` 태그의 `<th>`,`<td>`,`<tr>` 텍스트 정렬 (top, middle, bottom만 됨)


### background-size
<hr>
![](Pasted%20image%2020240427184239.png)

| **속성**      | **설명**                               |
| ----------- | ------------------------------------ |
| **auto**    | 원래 배경 이미지 크기만큼 표시(기본 값)              |
| **contain** | 지정한 요소 안에 배경 이미지가 다 들어오도록 이미지를 확대/축소 |
| **cover**   | 지정한 요소를 다 덮도록 배경이미지를 확대/축소           |
| **크기 값**    | 너비 값과 높이 값을 지정                       |
| **백분율**     | 지정한 요소를 기준으로 백분율 값을 지정               |


### margin
<hr>

[정리글](https://developer.mozilla.org/ko/docs/Web/CSS/margin)

> margin은 요소의 주위에 빈 공간을 추가하고,
> padding은 요소의 내부에 빈 공간을 만든다.

- **한 개의 값**은 모든 면의 여백을 설정.
- **두 개의 값**을 지정하면 첫 번째는 **위와 아래**, 두 번째는 **왼쪽과 오른쪽** 여백을 설정.
- **세 개의 값**을 지정하면 첫 번째는 **위**, 두 번째는 **왼쪽과 오른쪽,** 세 번째 값은 **아래** 여백을 설정.
- **네 개의 값**을 지정하면 각각 **상, 우, 하, 좌** 순서로 여백을 지정. (시계방향)

``` css
margin: 5%; /* 모두 5% */

margin: 10px; /* 모두 10px */

margin: 1.6em 20px;
/* 상하: 1.6em */
/* 좌우: 20px  */

margin: 10px 3% -1em;
/* 상: 10px */
/* 좌우: 3% */
/* 하: -1em */

margin: 10px 3px 30px 5px;
/* 상: 10px */
/* 우:  3px */
/* 하: 30px */
/* 좌:  5px */

margin: 2em auto;
/* 상하: 2em */
/* 수평 중앙정렬 */

margin: auto;
/* 상하: 0 */
/* 수평 중앙정렬 */
```

```CSS
margin-top: -25px;
margin-right: 10px;
margin-bottom: 30px;
margin-left: 100px;
```


### Position
<hr>

[정리글](https://creamilk88.tistory.com/197)

```css
.world {
	position : absolute; 
	// 문서 흐름에서 제거하여 가장 가까운 위치에 있는 조상 요소를 기준으로 배치
}
```

```css
.button {
  position: relative;
  top: 100px;
}
```

| 데이터 유형   | 설명                                           |
| -------- | -------------------------------------------- |
| static   | 기준 없음 (배치 불가능 / 기본값)                         |
| relative | 요소 자기 자신을 기준으로 배치                            |
| absolute | position: relative를 가진<br>부모(조상) 요소를 기준으로 배치 |
| fixed    | 뷰포트 기준으로 배치                                  |
| sticky   | 스크롤 영역 기준으로 배치                               |

| CSS 속성 | 설명                                    |
| ------ | ------------------------------------- |
| top    | 요소의 position 기준에 맞는 위쪽에서의 거리(위치)를 설정  |
| bottom | 요소의 position 기준에 맞는 아래쪽에서의 거리(위치)를 설정 |
| left   | 요소의 position 기준에 맞는 왼쪽에서의 거리(위치)를 설정  |
| right  | 요소의 position 기준에 맞는 오른쪽에서의 거리(위치)를 설정 |


### ::before와 ::after
<hr>

::before : 실제 내용 바로 앞에서 생성되는 자식요소  
::after : 실제 내용 바로 뒤에서 생성되는 자식요소​

::before와 ::after을 쓸 땐 content라는 속성이 필요함

| 속성      | 사용                            |
| ------- | ----------------------------- |
| normal  | 아무것도 표시하지 않는 기본값              |
| string  | 문자열 생성                        |
| image   | 이미지나 비디오를 불러올 수 있음. 크기 조절 불가능 |
| counter | 순서를 매길 수 있음.                  |
| none    | 아무것도 표시하지 않음                  |
| attr    | 해당속성의 속성값 표시                  |


## Flexbox
<hr>

[정리글](https://studiomeal.com/archives/197)

### justify-content : 요소를 가로선 상에서 정렬

| 속성            | 효과            |
| ------------- | ------------- |
| flex-start    | 왼쪽 정렬         |
| flex-end      | 오른쪽 정렬        |
| center        | 가운데로 정렬       |
| space-between | 요소 사이에 동일한 간격 |
| space-around  | 요소 주위에 동일한 간격 |

### align-items : 요소를 세로선 상에서 정렬

| 속성         | 효과                |
| ---------- | ----------------- |
| flex-start | 꼭대기로 정렬           |
| flex-end   | 바닥으로 정렬           |
| center     | 세로선 상의 가운데로 정렬    |
| baseline   | 시작 위치에 정렬         |
| stretch    | 요소들을 컨테이너에 맞도록 늘림 |

### flex-direction : 정렬 방향 지정

| 속성             | 효과               |
| -------------- | ---------------- |
| row            | 텍스트의 방향과 동일하게 정렬 |
| row-reverse    | 텍스트의 반대 방향으로 정렬  |
| column         | 위에서 아래로 정렬       |
| column-reverse | 아래에서 위로 정렬       |

### flex-wrap : 몇 줄에 걸쳐 정렬할지 지정

| 속성           | 효과                   |
| ------------ | -------------------- |
| nowrap       | 모든 요소들을 한 줄에 정렬      |
| wrap         | 요소들을 여러 줄에 걸쳐 정렬     |
| wrap-reverse | 요소들을 여러 줄에 걸쳐 반대로 정렬 |

> [!NOTE]
> `flex-flow`은 `flex-direction`과 `flex-wrap`을 묶어서 사용 가능
> 
> 예를 들어, `flex-flow: row wrap` 사용 가능



![](Pasted%20image%2020240529145814.png)

### align-content : 여러 줄 사이의 간격 지정

| 속성            | 효과                  |
| ------------- | ------------------- |
| flex-start    | 꼭대기에 정렬             |
| flex-end      | 컨테이너의 바닥에 정렬        |
| center        | 세로선 상의 가운데에 정렬      |
| space-between | 여러 줄들 사이에 동일한 간격    |
| space-around  | 여러 줄들 주위에 동일한 간격    |
| stretch       | 여러 줄들을 컨테이너에 맞도록 늘림 |

>[!bug]
>부모 요소가 `display: flex`라면 `<button>`의 높이가 부모 요소와 같아지는 현상 발생.
>`<button>`에 `align-self: center` 적용시켜주면 정상화.

### flex-grow : flexbox 내에서 차지하는 크기 지정
![](Pasted%20image%2020240529144202.png)

### flex-shrink : flexbox 내에서 상대적으로 작아짐
![](Pasted%20image%2020240529144214.png)

[정리글](https://apost.dev/863/)


## 부트스트랩
<hr>

### container 클래스의 주요 기능과 효과

1. **중앙 정렬**:
    
    - `container` 클래스는 페이지의 콘텐츠를 브라우저의 중앙에 정렬합니다.
2. **패딩 적용**:
    
    - `container` 클래스는 좌우에 기본 패딩을 적용하여 콘텐츠가 화면 가장자리에 바로 닿지 않도록 합니다.
3. **반응형 레이아웃**:
    
    - `container` 클래스는 미디어 쿼리를 사용하여 다양한 디바이스 크기에 맞게 너비가 자동으로 조정됩니다. 이를 통해 모바일, 태블릿, 데스크탑 등 다양한 화면 크기에서 적절한 레이아웃을 유지할 수 있습니다.

### 컨테이너 (Container)

- `.container`: 고정 폭의 중앙 정렬된 컨테이너
- `.container-fluid`: 100% 너비의 컨테이너
- `.container-{breakpoint}`: 특정 뷰포트 너비에서 고정 폭 중앙 정렬된 컨테이너 (예: `.container-sm`, `.container-md` 등)

### 행 (Row)

- `.row`: 그리드 시스템의 기본 행 클래스

### 열 (Column)

- `.col`: 자동 크기 열
- `.col-{number}`: 고정 크기 열 (예: `.col-1` ~ `.col-12`)
- `.col-{breakpoint}-{number}`: 특정 뷰포트 크기에서 고정 크기 열 (예: `.col-sm-1` ~ `.col-sm-12`, `.col-md-1` ~ `.col-md-12` 등)
- `.col-{breakpoint}-auto`: 특정 뷰포트 크기에서 자동 크기 열 (예: `.col-sm-auto`, `.col-md-auto` 등)

### 색상 (Colors)

- **배경색**: `.bg-primary`, `.bg-secondary`, `.bg-success`, `.bg-danger`, `.bg-warning`, `.bg-info`, `.bg-light`, `.bg-dark`, `.bg-white`, `.bg-transparent`
- **텍스트 색상**: `.text-primary`, `.text-secondary`, `.text-success`, `.text-danger`, `.text-warning`, `.text-info`, `.text-light`, `.text-dark`, `.text-white`, `.text-muted`, `.text-black-50`, `.text-white-50`

### 여백과 패딩 (Spacing)

### 여백 (Margin)

- `.m-0`, `.m-1`, `.m-2`, `.m-3`, `.m-4`, `.m-5`: 모든 방향에 여백
- `.mt-0`, `.mt-1`, `.mt-2`, `.mt-3`, `.mt-4`, `.mt-5`: 상단 여백
- `.mb-0`, `.mb-1`, `.mb-2`, `.mb-3`, `.mb-4`, `.mb-5`: 하단 여백
- `.ms-0`, `.ms-1`, `.ms-2`, `.ms-3`, `.ms-4`, `.ms-5`: 왼쪽 여백
- `.me-0`, `.me-1`, `.me-2`, `.me-3`, `.me-4`, `.me-5`: 오른쪽 여백
- `.mx-0`, `.mx-1`, `.mx-2`, `.mx-3`, `.mx-4`, `.mx-5`: 좌우 여백
- `.my-0`, `.my-1`, `.my-2`, `.my-3`, `.my-4`, `.my-5`: 상하 여백

### 패딩 (Padding)

- `.p-0`, `.p-1`, `.p-2`, `.p-3`, `.p-4`, `.p-5`: 모든 방향에 패딩
- `.pt-0`, `.pt-1`, `.pt-2`, `.pt-3`, `.pt-4`, `.pt-5`: 상단 패딩
- `.pb-0`, `.pb-1`, `.pb-2`, `.pb-3`, `.pb-4`, `.pb-5`: 하단 패딩
- `.ps-0`, `.ps-1`, `.ps-2`, `.ps-3`, `.ps-4`, `.ps-5`: 왼쪽 패딩
- `.pe-0`, `.pe-1`, `.pe-2`, `.pe-3`, `.pe-4`, `.pe-5`: 오른쪽 패딩
- `.px-0`, `.px-1`, `.px-2`, `.px-3`, `.px-4`, `.px-5`: 좌우 패딩
- `.py-0`, `.py-1`, `.py-2`, `.py-3`, `.py-4`, `.py-5`: 상하 패딩

### 디스플레이 (Display)

- `.d-none`, `.d-inline`, `.d-inline-block`, `.d-block`, `.d-table`, `.d-table-row`, `.d-table-cell`, `.d-flex`, `.d-inline-flex`

### Flexbox

- **정렬**:
    
    - `.align-items-start`, `.align-items-end`, `.align-items-center`, `.align-items-baseline`, `.align-items-stretch`
    - `.align-content-start`, `.align-content-end`, `.align-content-center`, `.align-content-between`, `.align-content-around`, `.align-content-stretch`
    - `.align-self-auto`, `.align-self-start`, `.align-self-end`, `.align-self-center`, `.align-self-baseline`, `.align-self-stretch`
- **정렬**:
    
    - `.justify-content-start`, `.justify-content-end`, `.justify-content-center`, `.justify-content-between`, `.justify-content-around`, `.justify-content-evenly`
- **Flex 방향**:
    
    - `.flex-row`, `.flex-row-reverse`, `.flex-column`, `.flex-column-reverse`
- **Flex 래핑**:
    
    - `.flex-wrap`, `.flex-nowrap`, `.flex-wrap-reverse`
- **Flex 크기**:
    
    - `.flex-fill`, `.flex-grow-0`, `.flex-grow-1`, `.flex-shrink-0`, `.flex-shrink-1`
- **순서**:
    
    - `.order-0`, `.order-1`, `.order-2`, `.order-3`, `.order-4`, `.order-5`, `.order-first`, `.order-last`

### 텍스트 (Text)

- `.text-left`, `.text-center`, `.text-right`, `.text-justify`, `.text-nowrap`
- `.text-lowercase`, `.text-uppercase`, `.text-capitalize`
- `.font-weight-light`, `.font-weight-normal`, `.font-weight-bold`, `.font-italic`
- `.text-decoration-none`, `.text-decoration-underline`, `.text-decoration-line-through`

### 배경 (Background)

- `.bg-primary`, `.bg-secondary`, `.bg-success`, `.bg-danger`, `.bg-warning`, `.bg-info`, `.bg-light`, `.bg-dark`, `.bg-white`, `.bg-transparent`

### 테두리 (Borders)

- `.border`, `.border-top`, `.border-end`, `.border-bottom`, `.border-start`, `.border-0`, `.border-top-0`, `.border-end-0`, `.border-bottom-0`, `.border-start-0`
- `.border-primary`, `.border-secondary`, `.border-success`, `.border-danger`, `.border-warning`, `.border-info`, `.border-light`, `.border-dark`, `.border-white`
- `.rounded`, `.rounded-top`, `.rounded-right`, `.rounded-bottom`, `.rounded-left`, `.rounded-circle`, `.rounded-pill`, `.rounded-0`
- `.border-radius-0`, `.border-radius-1`, `.border-radius-2`, `.border-radius-3`

### 크기 (Sizing)

- `.w-25`, `.w-50`, `.w-75`, `.w-100`, `.w-auto`
- `.h-25`, `.h-50`, `.h-75`, `.h-100`, `.h-auto`

### 섀도우 (Shadows)

- `.shadow-none`, `.shadow-sm`, `.shadow`, `.shadow-lg`

### 가시성 (Visibility)

- `.visible`, `.invisible`

### 포지션 (Position)

- `.position-static`, `.position-relative`, `.position-absolute`, `.position-fixed`, `.position-sticky`
- `.top-0`, `.top-50`, `.top-100`, `.bottom-0`, `.bottom-50`, `.bottom-100`, `.start-0`, `.start-50`, `.start-100`, `.end-0`, `.end-50`, `.end-100`
- `.translate-middle`, `.translate-middle-x`, `.translate-middle-y`


## Bugs
<hr>

### css stylesheet 추가할 때 슬래시
>[!bug]
> `<link href="/css/main.css" rel="stylesheet">` 이러면 오류 생긴다
> `<link href="css/main.css" rel="stylesheet">` 슬래시 빼줘야 함
### margin collapse 현상
>[!bug]
>박스 2개 위쪽 테두리가 겹쳐지면 margin도 합쳐져서 설정 하나만 바꿔도 다른거 따라감.
>해결책 : 부모 박스에 padding 조금 주면 된다

### z-index 붙여도 가려짐
>[!bug] 
>position 속성 안 붙어있으면 같은 stacking context가 아니라서 z-index 효과 없음

### border로 이미지 가리는 애니메이션 줄 때 테두리 어색함
>[!bug] 
>:hover 이전 원래 속성에 border: 0px; 넣어놓기

### 부트스트랩 col 사이에 gap이 안 주어짐
```html
<div class="row">
  <div class="works col-4 bg-primary">
	<h1>WORKS</h1>
  </div>

  <div class="about col-8 bg-primary">
	<h1>about</h1>
  </div>
</div>
```

![](Pasted%20image%2020240603125259.png)

이유는 모르겠는데 이렇게 하면 gap이 안 생김

```html
<div class="row">
	<div class="col-md-3">
	  <div class="blue-box">왼쪽박스</div>
	</div>
	<div class="col-md-6">
	  <div class="blue-box">가운데박스</div>
	</div>
	<div class="col-md-3">
	  <div class="blue-box">오른쪽박스</div>
	</div>
</div>
```

![](Pasted%20image%2020240603125433.png)

div 안에 또 div를 넣은 후에 글씨를 써야 함

### transform: scale 주면 텍스트가 도망감
>[!bug]
>.ani-text {
  display: inline-block;
  transform: scale(2);
  transform-origin: center;
} 