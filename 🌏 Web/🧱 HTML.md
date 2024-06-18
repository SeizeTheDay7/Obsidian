- [[#외부 라이브러리 링크|외부 라이브러리 링크]]
- [[#header에 넣는 태그들|header에 넣는 태그들]]
	- [[#header에 넣는 태그들#meta 태그|meta 태그]]
	- [[#header에 넣는 태그들#open graph|open graph]]
	- [[#header에 넣는 태그들#favicon|favicon]]
- [[#Awesomefont 아이콘|Awesomefont 아이콘]]
- [[#Semantic Tag|Semantic Tag]]
- [[#div와 비슷한 태그들|div와 비슷한 태그들]]
- [[#table|table]]
- [[#목록 태그|목록 태그]]
- [[#form|form]]
	- [[#form#input|input]]
	- [[#form#select|select]]
- [[#태그에 데이터 숨기기|태그에 데이터 숨기기]]
- [[#비디오 넣기|비디오 넣기]]
- [[#오디오 넣기|오디오 넣기]]



## 외부 라이브러리 링크

Bootstrap
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
```

jQuery
```html
<script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
```


## header에 넣는 태그들

### meta 태그
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

### open graph
```html
<head>
  <meta property="og:image" content="/이미지경로.jpg">
  <meta property="og:description" content="사이트설명">
  <meta property="og:title" content="사이트제목">
</head>
```
링크 공유할 때 썸네일 설정

### favicon
```
<head> <link rel="icon" href="아이콘경로.ico" type="image/x-icon"> </head>
```
웹사이트 제목 옆에 뜨는 아이콘 커스터마이징
- ico 대신 png 파일 가능. ico가 호환성은 가장 좋다. 
- 32 x 32 사이즈로 제작하면 됨
- 바탕화면 바로가기 아이콘 수정 : rel="apple-touch-icon-precomposed" 등 OS 별로 요구하는 속성이 다른데 favicon generator 검색해보면 OS별로 알아서 만들어줌


## Awesomefont 아이콘

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

## Semantic Tag
![[Pasted image 20240615192622.png]]
[출처](https://pozafly.github.io/html/semantic-web/)

- `<header>` : 웹 페이지 도입부. 주로 페이지 상단에 웹 사이트 로고와 네비게이션 링크를 감싸는 것에 사용.
- `<nav>` : 사이트 내 링크를 모아둔 네비게이션을 만드는 태그. 웹 사이트의 동선을 생성해 준다. 또한 상위 페이지에서 하위 페이지로 유도하는 역할.
- `<main>` : 웹 사이트의 본문을 뜻함. 메인 콘텐츠를 크게 감싸주는 역할로, 한 HTML 내에서 1개만 존재해야 함.
- `<section>` : 페이지 내에서 각 영역의 제목을 나타내는 `header` 와 콘텐츠를 감싸줌. 각 콘텐츠의 영역을 구획하는 것에 주로 사용.
- `<article>` : 뉴스나 블로그 글과 같이 독립적으로 콘텐츠 그 자체가 될 수 있는 콘텐츠.
- `<aside>` : 사이드 메뉴 등 main 이외의 콘텐츠. 메인 콘텐츠가 아닌 부가 정보, 해설을 담고 있기도 함.
- `<footer>` : 웹 페이지의 가장 하단에 있다. 웹 사이트 하단에 회사 정보나 약관 정보, 사이트 맵, 소셜 미디어 링크 등의 콘텐츠를 표시하는 것에 사용.


## div와 비슷한 태그들
<hr>

`<nav>` : 네비게이션 바
`<section>` : 테마나 목적이 같은 컨텐츠 그룹화
`<footer>` : 페이지 맨 마지막
`<article>` : 독립적으로 의미가 완전한 컨텐츠


## table
<hr>

```html
<table>
  <tr>
    <td></td>
  <tr>
</table>
```

테이블은 td 하나의 크기만 바꿔도 해당하는 열의 크기가 다 바뀐다.

`<table>` : 표 만들 때 사용 
- border-collapse: collapse : 셀 간의 간격 없애기 

`<thead>` : 최상단 제목 행 (기능상 차이는 없다)
`<tbody>` : 일반 행 (기능상 차이는 없다)

`<tr>` : 가로 행 (table row)
`<th>` : 제목용 세로 열 (table header)
`<td>` : 세로 열 (table data)
- vertical-align: top/middle/bottom : 셀 안의 요소 상하정렬
- colspan, rowspan : 셀 몇칸을 차지할지 설정

## 목록 태그
<hr>

[정리글](https://juheeexx.tistory.com/13)

`<ul>` : 순서가 중요하지 않은 목록; *unordered list*
`<ol>` : 순서가 중요한 목록; *ordered list*
	`<li>` : (위 2개의) 목록 안의 항목; *list item*


``` html
<dl> 
	<dt>복숭아</dt> 
	<dd>복사나무의 열매.시고 단 맛이 있으며 담홍색으로 익는다.</dd> 
</dl>
```

`<dl>` : 용어 목록; *description list*
	`<dt>` : 용어 태그; *description term*
	`<dd>` : 용어 정의 태그; *description details*


``` html
<p> 
	<dfn>복숭아</dfn>는 복사나무의 열매이다. 시고 단 맛이 있으며 담홍색으로 익는다. 
</p>
```

`<dfn>` : 현재 정의하고 있는 용어; *definition*


## form
<hr>

```html
<form action="http://naver.com"> // 데이터를 네이버로 보낸다
</form>
```

태그 안에 감싸져 있는 `<input>`, `<select>`, `<textarea>` 안의 데이터를 서버로 보낸다.

### input

`<form>` 태그로 서버에 데이터를 보낼 때 `<input>` 태그로 입력 영역을 만들 수 있다.

```html
<input type="text" value="test value"> // 미리 입력되어 있는 값
<input type="text" placeholder="test value"> // 예시로 보여주는 값
<input type="text" name="age"> // 인풋 이름 입력
<input type="submit"> // 서버에 데이터 보낸다
```
`<input type="submit">`은 `<button type="submit">전송</button>`으로 대체 가능

```html
<input id="sub" type="checkbox">
<label for="sub"> Subscribe</label>
```
이렇게 하면 "Subscribe" 누르면 체크박스도 같이 체크됨

| type 속성  |                                                 |
| -------- | ----------------------------------------------- |
| text     | 기본값으로 한 줄의 텍스트 입력 칸을 만듭니다. (기본 너비 문자는 20입니다.)   |
| password | text 속성과 같지만, 입력 문자를 별표(*)로 대체해서 표시합니다.         |
| checkbox | 선택 항목 중 여러 개를 선택할 수 있는 체크박스를 만듭니다.              |
| radio    | 선택 항목 중 1가지만 선택 가능한 라디오 버튼을 만듭니다.               |
| button   | 누를 수 있는 기본 버튼을 만듭니다.                            |
| submit   | 전송 버튼을 만듭니다.                                    |
| reset    | 재설정 버튼을 만듭니다.                                   |
| file     | 파일 선택창을 여는 버튼을 만듭니다.                            |
| hidden   | 사용자에게 보이지 않는 숨김 창을 만듭니다.                        |
| image    | 이미지로 된 전송 버튼을 만듭니다. (src 속성을 통해 이미지 주소를 지정합니다.) |

| html5 이후       |                                                              |
| -------------- | ------------------------------------------------------------ |
| color          | 색상 선택 창을 만듭니다.                                               |
| date           | 년, 월, 일을 입력할 수 있는 날짜 입력 창을 만듭니다.                             |
| datetime       | 년, 월, 일, 시, 분, 초, 초의 분할까지 입력할 수 있는 표준시간날짜시간 입력 창을 만듭니다.      |
| datetime-local | 년, 월, 일, 시, 분, 초, 초의 분할까지 입력할 수 있는 표준시간이 아닌 날짜시간 입력 창을 만듭니다. |
| email          | 이메일 주소 창을 만듭니다.                                              |
| month          | 년, 월 입력 창을 만듭니다.                                             |
| number         | 숫자 입력을 위한 창을 만듭니다.                                           |
| range          | 슬라이더같은 정확한 값이 중요하지 않는 숫자를 입력하는 창을 만듭니다.                      |
| search         | 검색창을 만듭니다.                                                   |
| tel            | 전화번호 입력창을 만듭니다.                                              |
| time           | 표준시간이 아닌 시간 입력 창을 만듭니다.                                      |
| url            | 인터넷 주소 입력창을 만듭니다.                                            |
| week           | 표준시간이 아닌 년, 주 입력 창을 만듭니다.                                    |

### select

[정리글](https://thrillfighter.tistory.com/572)
[정리글2](https://batcave.tistory.com/69)

선택 목록을 만드는 태그. `<form>` 태그로 감싸주면 선택한 값을 전달할 수 있다.
`<option>` 태그로 선택지를 설정한다.

```html
<select name="web">
  <option value="js">JavaScript</option>
  <option value="ts">TypeScript</option>
  <option value="html">HTML</option>
</select>
```

## 태그에 데이터 숨기기

```html
<button data-자료이름="값"></button>
```

```js
e.target.dataset.자료이름 // 바닐라 js로 추출
e.target.data('자료이름') // jqeury로 추출
```


## 비디오 넣기

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


## 오디오 넣기

```html
<audio src="bass.mp3" controls></audio>
```

muted : 음소거 상태로 시작
autoplay : 자동재생인데 javascript 만져야 가능 
preload : video와 동일
