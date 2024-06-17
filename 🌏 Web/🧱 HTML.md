- [[#외부 라이브러리 링크|외부 라이브러리 링크]]
- [[#Semantic Tag|Semantic Tag]]
- [[#div류 태그|div류 태그]]
- [[#table|table]]
- [[#목록 태그|목록 태그]]
- [[#form|form]]
	- [[#form#input|input]]
	- [[#form#select|select]]

## 외부 라이브러리 링크

Bootstrap
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
```

jQuery
```html
<script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
```


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


## div와 비슷한
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


