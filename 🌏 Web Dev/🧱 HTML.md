- [[#`<div>`류 태그들|`<div>`류 태그들]]
- [[#목록 태그|목록 태그]]




## `<div>`류 태그들
<hr>

`<nav>` : 네비게이션 바
`<section>` : 테마나 목적이 같은 컨텐츠 그룹화
`<footer>` : 페이지 맨 마지막
`<article>` : 독립적으로 의미가 완전한 컨텐츠


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


### `<form>` 태그
<hr>

```html
<form action="http://naver.com"> // 데이터를 네이버로 보낸다
</form>
```

태그 안에 감싸져 있는 `<input>`, `<select>`, `<textarea>` 안의 데이터를 서버로 보낸다.

#### `<input>` 태그

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

#### `<select>` 태그

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


