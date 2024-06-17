- [[#문법|문법]]
	- [[#문법#for문|for문]]
	- [[#문법#문자열 조작|문자열 조작]]
	- [[#문법#Arrow function 문법|Arrow function 문법]]
- [[#Web|Web]]
	- [[#Web#링크 기호|링크 기호]]
	- [[#Web#Ajax|Ajax]]
	- [[#Web#window.location|window.location]]
	- [[#Web#페이지 이동, 새로고침|페이지 이동, 새로고침]]
- [[#jQuery|jQuery]]
	- [[#jQuery#이벤트 메서드|이벤트 메서드]]
	- [[#jQuery#값 인출, 입력, 삭제|값 인출, 입력, 삭제]]
	- [[#jQuery#요소 숨기기, 보이기|요소 숨기기, 보이기]]
	- [[#jQuery#객체 속성 바꾸기|객체 속성 바꾸기]]


## 문법

### for문
<h4>for</h4>
```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

<h4>for ... of</h4>
```js
let array = [1, 2, 3, 4, 5];
for (let value of array) {
  console.log(value);
}
// 출력: 1, 2, 3, 4, 5
```
배열 순회할 때 사용 (배열, 문자열, Map, Set)

<h4>for ... in</h4>
```js
let obj = { a: 1, b: 2, c: 3 };
for (let key in obj) {
  console.log(key + ": " + obj[key]);
}
// 출력: // a: 1 // b: 2 // c: 3
```
객체 순회할 때 사용

<h4>forEach</h4>
```js
let array = [1, 2, 3];
array.forEach(function(value, index) {
  console.log(index + ": " + value);
});
// 출력:
// 0: 1
// 1: 2
// 2: 3
```

### 문자열 조작
```Javascript
let txt = '서울시-마포구-망원동' 
let names = txt.split('-'); // ['서울시','마포구','망원동'] 
let result = names.join('>'); // '서울시>마포구>망원동'
```
split : 쪼개기
join : 쪼개져 있는거 붙이

### 화살표 함수
```js
const add = (a,b) => {
    return a + b;
}

//매개변수가 1개라면 소괄호도 생략할수있다.
const square = x => { return x*x };

//한줄로 작성 가능한 경우 중괄호와 return 키워드도 생략 가능하다.
const square = x => x*x;
const add = (a,b) => a+b;
```

<h4> 화살표 함수 객체 반환 방법</h4>
1\. 명시적 return 사용
```js
const getObject = () => {
  return { value: 1 }; // 객체를 반환하기 위해 return을 사용
};
```

2\. 소괄호 사용
```js
const getObject = () => ({ value: 1 }); // 소괄호로 객체를 감싸서 반환
```

소괄호 안 쓰고 객체 반환하면 함수로 잘못 해석됨.

## Web

### 링크 기호
```
예시) google.com/search?q=아이폰&sourceid=chrome&ie=UTF-8

? : 여기서부터 전달할 데이터가 작성된다는 의미
& : 전달할 데이터가 더 있다는 뜻
```

### Ajax
```javascript
$.ajax({
  type: "GET", // GET 방식으로 요청
  url: "URL 입력", // 서버의 특정 엔드포인트 가리킴
  data: {}, // 서버에 보낼 데이터 (GET 요청시엔 비움)
  success: function(response){ 
    console.log(response) // 서버에서 준 결과
  }
})
```

### window.location

window : 브라우저 창이나 탭 자체를 의미.  팝업 열기, 창 크기 조절, URL 변경 등 가능.

| 속성         |                                                      |
| ---------- | ---------------------------------------------------- |
| `href`     | 전체 URL. 지정된 URL로 페이지를 이동.                            |
| `protocol` | 현재 URL의 프로토콜 (예: `http:` 또는 `https:`).               |
| `host`     | 호스트 이름과 포트 번호를 포함한 URL의 일부 (예: `example.com:80`).    |
| `hostname` | 도메인 이름 (예: `example.com`).                           |
| `port`     | URL에서 사용된 포트 번호                                      |
| `pathname` | 호스트 뒤의 URL 경로 (예: `/path/index.html`).               |
| `search`   | URL의 쿼리 문자열. 첫 번째 `?` 문자 뒤의 모든 것. (예: `?key=value`). |
| `hash`     | URL의 앵커 부분. 첫 번째 `#` 문자 뒤의 모든 것. (예: `#section1`).   |

### 페이지 이동, 새로고침

**location.href**
```js
location.href = 'https://www.example.com';
```
현재 페이지를 다른 URL로 변경함.
브라우저의 히스토리에 현재 페이지가 기록됨.

**location.replace**
```js
location.replace('https://www.example.com');
```
현재 페이지를 다른 URL로 변경함.
브라우저의 히스토리에 현재 페이지 기록 안됨.
(뒤로가기 버튼 눌러도 못 돌아감)

**window.open**
```js
window.open('https://www.example.com');
window.open('https://www.example.com', 'newwindow', 'width=800,height=600');
```
새 브라우저 창이나 탭을 염. 옵션 설정 가능.

**window.location.reload(forceGet)**
```js
window.location.reload(true);
```
페이지 새로고침. 
forceGet이 true면 서버에서 페이지 다시 가져옴.
false면 캐시에서 다시 로드함.

## jQuery

### 이벤트 메서드

```js
$('#element').click(function() {});
```
요소 클릭할 때 실행

```js
$('#input').focus(function() {});
```
요소 포커스 받을 때 실행

```js
$('#input').blur(function() {});
```
요소 포커스 읽을 때 실행

```js
$('#input').scroll(function() {});
```
사용자가 스크롤할 때 실행

```js
$('form').submit(function(event) {
  event.preventDefault(); // 폼 제출을 막음
  // 폼 제출 시 실행할 코드
});
```
폼이 제출될 때 실행

```js
$('#input').change(function() {});
```
폼 요소가 변경될 때 실행

### 값 인출, 입력, 삭제
```javascript
let url = $('#post-url').val(); 
// val()로 값을 가져온다

let btn_next = $('#btn-posting-box').text();
// text()로 텍스트를 가져온다.

$('#post-url').val("새 글입니다");
// val()에 뭐 넣으면 값을 입력한다

$('...').empty(); // 삭제
```

### 요소 숨기기, 보이기
```javascript
$('#post-box').hide();
$('#post-box').show();
```

### 객체 속성 바꾸기
```javascript
$("#img-cat").attr("src", imgurl);
```
