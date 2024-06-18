- [[#General|General]]
	- [[#General#용어 설명|용어 설명]]
- [[#문법|문법]]
	- [[#문법#let, const, var 차이점|let, const, var 차이점]]
	- [[#문법#배열 복사|배열 복사]]
	- [[#문법#for문|for문]]
	- [[#문법#배열 조작|배열 조작]]
		- [[#배열 조작#split, join|split, join]]
		- [[#배열 조작#sort|sort]]
		- [[#배열 조작#filter|filter]]
		- [[#배열 조작#map|map]]
	- [[#문법#클래스 토글|클래스 토글]]
	- [[#문법#화살표 함수|화살표 함수]]
	- [[#문법#타이머 함수|타이머 함수]]
	- [[#문법#문자열 조건 확인|문자열 조건 확인]]
	- [[#문법#배열 조건 확인|배열 조건 확인]]
	- [[#문법#정규식|정규식]]
- [[#Web|Web]]
	- [[#Web#Tip|Tip]]
		- [[#Tip#요소 만들고 내용 넣기|요소 만들고 내용 넣기]]
		- [[#Tip#문서 로딩 다 되면 실행하는 코드|문서 로딩 다 되면 실행하는 코드]]
		- [[#Tip#문서 로딩 이후에 추가된 요소에 이벤트 적용|문서 로딩 이후에 추가된 요소에 이벤트 적용]]
	- [[#Web#링크 기호|링크 기호]]
	- [[#Web#이벤트 리스너|이벤트 리스너]]
		- [[#이벤트 리스너#이벤트 속성, 함수|이벤트 속성, 함수]]
		- [[#이벤트 리스너#이벤트 목록|이벤트 목록]]
	- [[#Web#스크롤 관련|스크롤 관련]]
	- [[#Web#드래그 & 드랍 이벤트|드래그 & 드랍 이벤트]]
	- [[#Web#fetch|fetch]]
	- [[#Web#window.location|window.location]]
	- [[#Web#페이지 이동, 새로고침|페이지 이동, 새로고침]]
	- [[#Web#브라우저 저장 공간|브라우저 저장 공간]]
- [[#jQuery|jQuery]]
	- [[#jQuery#기본 메서드|기본 메서드]]
	- [[#jQuery#값 인출, 입력, 삭제|값 인출, 입력, 삭제]]
	- [[#jQuery#요소 숨기기, 보이기|요소 숨기기, 보이기]]
	- [[#jQuery#이벤트 메서드|이벤트 메서드]]
	- [[#jQuery#HTTP 요청|HTTP 요청]]
	- [[#jQuery#조건 확인 선택자|조건 확인 선택자]]
	- [[#jQuery#요소 비교할 때 주의|요소 비교할 때 주의]]
- [[#Bugs|Bugs]]
	- [[#Bugs#Bootstrap 쓸 때 scrollTo가 smooth하게 움직임|Bootstrap 쓸 때 scrollTo가 smooth하게 움직임]]

## General

<h4>UI 만드는 step</h4>
1. HTML/CSS로 미리 디자인
2. 필요할 때 보여달라고 코드짬 (자바스크립트로)

<h4>JS 코드 위치</h4>
JS코드 위치 : body 태그 끝나기 전.
JS 라이브러리 위치 : JS 코드 앞, body 태그 끝나기 전
이유 : DOM 만들어져야 그걸 조작할 수 있음

<h4>jquery 요소 순회</h4>
jquery 요소 순회는 foreach가 아니라 each로 해줘야 함


### 용어 설명

- 이벤트 위임 : 자식 요소를 클릭해도 부모 요소까지 클릭 이벤트가 전파됨
- 콜백함수 : 파라미터 자리에 들어가는 함수
- 서버 사이드 렌더링 : 완성품 html을 서버가 줌 (서버가 힘듬)
- 클라이언트 사이드 렌더링 : 빈 html이랑 데이터 주면 유저가 완성 (서버가 편함)
- DOM : js가 HTML에 대한 정보들을 객체로 정리한것


## 문법

**문자 중간에 변수 넣는 법**
```js
`문자${a}문자`
```

**null 나오면 다른 값 뱉어내는 법**
```js
var test = A || B;
```
A가 falsy (거짓 같은 값, 즉, null, undefined, 0, '' 등) 이면 B 반환

### let, const, var 차이점
<hr>

|       | 재선언 | 재할당 | 범위                |
| ----- | --- | --- | ----------------- |
| let   | 불가능 | 가능  | 블록 스코프 `{}`       |
| const | 불가능 | 불가능 | 블록 스코프 `{}`       |
| var   | 가능  | 가능  | 함수 스코프 `function` |

### 배열 복사
<hr>

```js
let arr2 = arr1; // 얕은 복사
let arr2 = [...arr1]; // 얕은 복사 + 깊은 복사
let arr2 = JSON.parse(JSON.stringify(arr1)); // 깊은 복사
```

### for문
<hr>
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
let array = ['해삼', '멍게', '말미잘'];
array.forEach(function(value, index) {
  console.log(index + ": " + value);
});
// 출력:
// 0: '해삼'
// 1: '멍게'
// 2: '말미잘'
```


### 배열 조작
<hr>

#### split, join
```Javascript
let txt = '서울시-마포구-망원동' 
let names = txt.split('-'); // ['서울시','마포구','망원동'] 
let result = names.join('>'); // '서울시>마포구>망원동'
```
split : 쪼개기
join : 쪼개져 있는거 붙임

#### sort
```js
array.sort(); // 문자 정렬
arr.sort((a, b) => b.localeCompare(a)); // 문자 내림차순 정렬
array.sort((a,b) => a-b); // 숫자 배열 정렬
```

#### filter
```js
var newArray = array.filter(a => a < 4);
```
주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열을 만듬. 
원본 배열은 변경되지 않음. 따로 변수에 담아야 됨.

#### map
```js
var newArray = array.map(a => a * 2);
```
배열 안의 데이터를 일괄 변경. 원본 배열 변경 안됨.


### 클래스 토글
<hr>

```js
document.querySelector('.list-group').classList.toggle('d-none');
```
classList.toggle('클래스명')은 해당 클래스가 있으면 제거하고, 없으면 추가
jquery로는 toggleClass('클래스명')

### 화살표 함수
<hr>

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

### 타이머 함수
<hr>

```js
setTimeout(function(){ 실행할코드 }, ms) // 지정한 시간이 지난 후에 한 번 실행됨
clearTimeout(timeoutID) // setTimeout 취소

setInterval(function(){ 실행할코드 }, ms) // 지정한 시간 간격마다 반복해서 실행됨
clearInterval(intervalID) // setInterval 취소
```
취소하려면 var 타이머 setTimeOut(어쩌구); 이렇게 변수에 저장해야됨

### 문자열 조건 확인
<hr>

```javascript
let str = "Hello, world!";
str.includes("world"); // true, 특정 문자열이 포함되어 있는지 확인
str.indexOf("world"); // 7, 특정 문자열의 첫 번째 인덱스를 반환, 없으면 -1
str.startsWith("Hello"); // true, 문자열이 특정 문자열로 시작하는지 확인
str.endsWith("world!"); // true, 문자열이 특정 문자열로 끝나는지 확인
```

### 배열 조건 확인
<hr>

```js
let arr = [1, 2, 3, 4, 5];
arr.includes(3); // true, 배열에 특정 값이 포함되어 있는지 확인
arr.indexOf(3); // 2, 배열에서 특정 값의 첫 번째 인덱스를 반환, 없으면 -1
arr.some(num => num > 3); // true, 배열의 일부 요소가 특정 조건을 만족하는지 확인
arr.every(num => num > 0); // true, 배열의 모든 요소가 특정 조건을 만족하는지 확인
```

### 정규식
<hr>

```js
/찾을단어/.test('문자'); // 문자 안에 단어 있는지 확인좀

/[a-z]/.test('문자'); // a에서 z까지 문자를 전부 
/[ㄱ-ㅎ가-힣]/.test('문자') // 한글 들어있나요
/\S/.test('문자') // 아무 문자 1개 들어 있나요
/^a/.test('문자') // a로 시작하냐
/a$/.test('문자') // a로 끝나냐
/a|b/.test('문자') // a 또는 b가 들어있냐
/a+/.test('문자') // 뒤에 오는 글자도 a와 일치하면 쭉 찾아라
/\S+t/.test('문자') // 모든 문자 여러 개 다음에 t라는 글자가 있냐
```



## Web

### Tip
<hr>

#### 요소 만들고 내용 넣기
```js
var a = document.createElement('p');
var b = $('<p></p>');
a.innerHTML = '안녕';
b.html('안녕');
```

#### 문서 로딩 다 되면 실행하는 코드
```js
$(document).ready(function(){ 실행할 코드 }) // jquery
document.addEventListener('DOMContentLoaded', function() { 실행할 코드 })
```
"이 코드는 HTML 전부 다 읽고 실행해주세요"라는 뜻. 둘 중 하나 쓰면 됨.
(요즘은 자바스크립트를 `<body>`태그 끝나기 전에 전부 작성하긴 함)

#### 문서 로딩 이후에 추가된 요소에 이벤트 적용
```js
$(document).on('click', '.dynamic-button', function() {
    alert('Button clicked!');
});
```
jQuery의 `$(document).on('event', 'selector', handler)` 메서드는 이벤트 위임(event delegation)이라는 기법을 사용하여 동적으로 추가된 요소에도 이벤트를 바인딩.

### 링크 기호
<hr>

```
예시) google.com/search?q=아이폰&sourceid=chrome&ie=UTF-8

? : 여기서부터 전달할 데이터가 작성된다는 의미
& : 전달할 데이터가 더 있다는 뜻
```

### 이벤트 리스너
<hr>

```js
var element = document.querySelector(요소);
element.addEventListener('이벤트', function(e) {});
```
jquery는 더 간편하게 등록 가능.

#### 이벤트 속성, 함수

이벤트 리스너 콜백함수에 파라미터 (보통 e) 달고 사용

**e.target** : 실제 클릭한 요소 알려줌 (이벤트 발생한 곳)
**e.currentTarget** : 이벤트 리스너가 달린 곳 알려줌 (참고로 this라고 써도 똑같음)
**e.preventDefault()** : 실행하면 이벤트 기본 동작을 막아줌
**e.stopPropagation()** : 실행하면 내 상위요소로의 이벤트 버블링을 중단해줌

**e.clientX**: 이벤트가 발생한 가로 좌표를 반환합니다 (뷰포트 기준).
**e.clientY**: 이벤트가 발생한 세로 좌표를 반환합니다 (뷰포트 기준).
**e.pageX**: 이벤트가 발생한 가로 좌표를 반환합니다 (문서 기준).
**e.pageY**: 이벤트가 발생한 세로 좌표를 반환합니다 (문서 기준).
**e.screenX**: 이벤트가 발생한 가로 좌표를 반환합니다 (스크린 기준).
**e.screenY**: 이벤트가 발생한 세로 좌표를 반환합니다 (스크린 기준).
**e.offsetX**: 이벤트가 발생한 요소의 경계에서의 가로 좌표를 반환합니다.
**e.offsetY**: 이벤트가 발생한 요소의 경계에서의 세로 좌표를 반환합니다.
**e.button**: 클릭된 마우스 버튼을 반환합니다 (0: 왼쪽, 1: 휠 버튼, 2: 오른쪽).

#### 이벤트 목록

- **click**: 요소를 클릭할 때.
- **dblclick**: 요소를 더블 클릭할 때.  
- **focus**: 요소가 포커스를 받을 때.
- **blur**: 요소가 포커스를 잃을 때.
- **change**: 입력 필드의 값이 변경될 때.
- **input**: 입력 필드에 입력할 때마다.
- **submit**: 폼이 제출될 때.
- **resize**: 창의 크기가 변경될 때.
- **scroll**: 스크롤할 때.
- **select**: 텍스트를 선택할 때.
- **load**: 요소가 로딩됐을 때.

- **keydown**: 키를 누를 때.
- **keypress**: 키를 눌렀을 때.
- **keyup**: 누른 키를 뗄 때.

- **mousedown**: 마우스 버튼을 누를 때.
- **mouseup**: 마우스 버튼을 뗄 때.
- **mouseenter**: 마우스가 요소 위로 들어올 때.
- **mouseleave**: 마우스가 요소를 벗어날 때.
- **mousemove**: 마우스가 요소 위에서 움직일 때.
- **mouseover**: 마우스가 요소 위로 올라올 때.
- **mouseout**: 마우스가 요소를 벗어날 때.
- **contextmenu**: 요소에서 오른쪽 마우스 버튼을 클릭할 때.

(모바일에선 mouse를 touch로 바꿔야됨.)

- **touchstart**: 터치가 시작될 때.
- **touchend**: 터치가 끝날 때.
- **touchmove**: 터치가 움직일 때.
- **touchcancel**: 터치가 취소될 때.

### 스크롤 속성, 메소드
<hr>

window.scrollY : 현재 스크롤 얼마나 내렸는지
window.scrollTo(x,y) : 강제로 스크롤하기
window.scrollTop() : 현재 스크롤바 위치 출력 (jquery에선 숫자 넣으면 이동도 함)
window.scrollHeight : 요소 스크롤 높이

```js
var 실제높이 = $('.lorem').prop('scrollHeight');
var 스크롤양 = $('.lorem').scrollTop();
var 높이 = $('.lorem').height();
```
- (실제높이 - 박스높이) = 전체 스크롤양
- 스크롤 다 봤는지 조건문 걸때 여유 오차 좀 줘야 함
- body 태그 끝나기 전에 측정해야 정확하게 나옴


### 드래그 & 드랍 이벤트
<hr>

[참고](inpa.tistory.com/entry/드래그-앤-드롭-Drag-Drop-기능)

jquery 쓰면 event 객체 쓸 때 originalEvent 붙여야 해서 오히려 불편하다.
평범하게 adEventListener로 붙이는게 나은듯.

html 요소에 draggable = "true" 줘야 드래그가 된다.

| **이벤트 순서 ↓** | **설명**                                                                             |
| ------------ | ---------------------------------------------------------------------------------- |
| dragstart    | 1. 사용자가 객체(object)를 드래그하려고 시작할 때 발생함.                                              |
| drag         | 2. 대상 객체를 드래그하면서 마우스를 움직일 때 발생함.                                                   |
| dragenter    | 3. 마우스가 대상 객체의 위로 처음 진입할 때 발생함.                                                    |
| dragover     | 4. 드래그하면서 마우스가 대상 객체의 영역 위에 자리 잡고 있을 때 발생함.                                        |
| drop         | 5. 드래그가 끝나서 드래그하던 객체를 놓는 장소에 위치한 객체에서 발생함. <br>리스너는 드래그된 데이터를 가져와서 드롭 위치에 놓는 역할을 함 |
| dragleave    | 6. 드래그가 끝나서 마우스가 대상 객체의 위에서 벗어날 때 발생함.                                             |
| dragend      | 7. 대상 객체를 드래그하다가 마우스 버튼을 놓는 순간 발생함.                                                |

dragstart : 드래그가 시작될 때
```js
const dragItem = document.getElementById('drag1');
const dropZone = document.getElementById('dropzone');

dragItem.addEventListener('dragstart', (e) => {
  e.dataTransfer.setData('text/plain', e.target.id);
  e.dataTransfer.effectAllowed = 'move';
});
```

dragenter : 드래그 요소가 목표 영역에 들어왔을 때
```js
dropZone.addEventListener('dragenter', (e) => {
  e.preventDefault();
  dropZone.style.backgroundColor = 'lightgreen';
});
```

dragleave : 드래그 요소가 목표 영역을 떠났을 때
```js
dropZone.addEventListener('dragleave', (e) => {
  dropZone.style.backgroundColor = 'lightblue';
});
```

dragover : 드래그 요소가 목표 영역 위에 있을 때
```js
dropZone.addEventListener('dragover', (e) => {
  e.preventDefault();
  e.dataTransfer.dropEffect = 'move';
});
```

drop : 드래그 요소가 목표 영역에 놓였을 때
```js
dropZone.addEventListener('drop', (e) => {
  e.preventDefault();
  const id = e.dataTransfer.getData('text');
  const draggedElement = document.getElementById(id);
  dropZone.appendChild(draggedElement);
  dropZone.style.backgroundColor = 'lightblue';
});
```

>[!note] event.preventDefault 사용 이유
>기본적으로 HTML 요소는 다른 요소의 위에 위치할 수 없다. 따라서 다른 요소 위에 위치할 수 있도록 만들기 위해서는 놓일 장소에 있는 요소의 기본 동작을 막아야만 한다. 이 작업을 event.preventDefault 메소드를 호출하는 것만으로 간단히 설정할 수 있다.

<h4>dropEffect</h4>

dropEffect 속성은 드래그 앤 드롭 동작 동안 드롭할 때 발생할 동작을 설정. 이 속성은 드래그되는 동안 커서의 모양을 변경하여 사용자가 드롭이 어떻게 처리될지 시각적으로 알 수 있도록 함.

- **`none`**: 드롭이 허용되지 않습니다.
- **`copy`**: 드롭하면 데이터가 복사됩니다.
- **`move`**: 드롭하면 데이터가 이동됩니다.
- **`link`**: 드롭하면 데이터에 대한 링크가 생성됩니다.

<h4>dataTransfer</h4>

dataTransfer 객체는 드래그 앤 드롭 동작 동안 데이터를 전달하는 데 사용

- setData(format, data): 드래그하는 동안 전송할 데이터를 설정. 
- getData(format): 드롭 시 전달된 데이터를 가져옴. 

```javascript
e.dataTransfer.setData('text/plain', 'Hello World'); // 텍스트 전달
e.dataTransfer.setData('text/html', '<p>Hello World</p>'); // HTML 전달
e.dataTransfer.setData('text/uri-list', 'http://example.com'); // URL 전달
e.dataTransfer.setData('application/json', JSON.stringify({ key: 'value' })); 
// JSON 전달
e.dataTransfer.setData('application/xml', '<note><to>User</to><message>Hello</message></note>'); // XML 전달
var files = e.dataTransfer.files; // 파일 전달
e.dataTransfer.setData('application/x-my-custom-format', 'Custom Data'); // 기타
```


### fetch
<hr>

HTTP 요청 보내는 Web API

```js
fetch('url') // 기본적으론 GET 요청 수행
  .then(response => { // 응답 처리
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => { // json으로 파싱된 데이터 사용
    console.log(data);
  })
  .catch(error => { // 네트워크 오류, 프로미스 체인 내의 다른 오류 처리
    console.error('There was a problem with the fetch operation:', error);
  });
```
fetch는 HTTP response 객체를 래핑한 Promise 객체를 반환.
프로미스의 후속 처리 메서드인 then을 사용하여 resolve한 객체를 전달받을 수 있다.


```js
fetch('https://api.example.com/data', {
  method: 'POST', // 요청 메서드
  headers: {
    'Content-Type': 'application/json' // 요청 헤더
  },
  body: JSON.stringify({
    key1: 'value1',
    key2: 'value2'
  }) // 요청 본문
})
.then(response => {
  if (!response.ok) {
    throw new Error('Network response was not ok');
  }
  return response.json();
})
.then(data => {
  console.log(data);
})
.catch(error => {
  console.error('파일을 로드하는 데 실패했습니다:', error);
});
```
fetch는 post도 할 수 있고 다재다능 ([참고](velog.io/@eunjin/JavaScript-fetch-함수-쓰는-법-fetch-함수로-HTTP-요청하는-법))

### window.location
<hr>

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
<hr>

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


### 브라우저 저장 공간
<hr>

>[!note] 브라우저 저장 공간
Local Storage / Session Storage (key : value 형태로 문자, 숫자 데이터 저장가능)
Indexed DB (크고 많은 구조화된 데이터를 DB처럼 저장가능, 문법더러움)
Cookies (유저 로그인정보 저장공간)
Cache Storage (html css js img 파일 저장해두는 공간)

Local Storage : 브라우저 재접속해도 영구적으로 남아있음
Session Storage : 브라우저 끄면 날아감

**Local Storage 사용법**
```js
localStorage.setItem('이름', 'kim') //자료저장하는법
localStorage.getItem('이름') //자료꺼내는법
localStorage.removeItem('이름') //자료삭제하는법
```

**Local Storage에 배열, 객체 저장**
```js
localStorage.setItem('num',[1,2,3]); // '1,2,3'

var arr = [1,2,3];
var newArr = JSON.stringify(arr);
localStorage.setItem('num',newArr); // '[1,2,3]'

var getData = localStorage.getItem('num'); // '[1,2,3]'
var reArr = JSON.parse(getData); // [1,2,3]
```
원래는 배열, 객체도 텍스트로 뭉개는데 
JSON으로 바꾼 다음 넣고 뺄 때는 JSON.parse()로 풀어서 쓰면 배열, 객체 다시 됨.
Local Storage에 넣었던거 수정하려면 {자료 꺼냄 → 꺼낸거 수정 → 다시 넣음}

## jQuery

### 기본 메서드
<hr>

```js
$('.hello').html('바보');
$('.hello').css('color', 'red');
$('.hello').addClass('d-none');
$('.hello').removeClass('d-none');
$('.hello').toggleClass('d-none');
$("#img-cat").attr("src", imgurl);
```

### 값 인출, 입력, 삭제
<hr>

```javascript
let url = $('#post-url').val(); 
// val()로 값을 가져온다

$('#post-url').val("새 글입니다");
// val()에 뭐 넣으면 값을 입력한다

let btn_next = $('#btn-posting-box').text();
// text()로 텍스트를 가져온다.

$('...').empty(); // 삭제
```

### 요소 숨기기, 보이기
<hr>

```javascript
$('#post-box').hide();
$('#post-box').show();
```
요소를 즉시 숨기거나, 지정된 시간 동안 애니메이션을 통해 서서히 숨김

```js
$('#post-box').fadeOut();
$('#post-box').fadeIn();
```
요소를 지정된 시간 동안 서서히 숨김. 기본적으로 400ms.

```js
$('#post-box').slideUp();
$('#post-box').slideDown();
```
요소를 지정된 시간 동안 위로 슬라이드하여 숨김. 기본적으로 400ms.

### 이벤트 메서드
<hr>

```js
$(요소).on(이벤트,function() {})
```

```js
$(요소).이벤트메서드(function() {})
```
이벤트들은 on 생략하고 메서드로 바로 사용할 수도 있다.
생략하면 [차이점](https://lazyartisan.tistory.com/9)은 있다.


### HTTP 요청
<hr>

<h4>ajax</h4>
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

<h4>get</h4>
```js
$.get('url~~~')
	.done(function(data) {
		console.log(data); // 받아온 데이터 출력
	})
	.fail(function() {
		// ajax 실패했을 때
	})
```
fetch와 다르게 json을 객체로 바로 변환해줌

```js
$(document).ready(function() {
  $.get('store.json')
    .done(function(data) {
      data.products.forEach((p)=> {
        var title = p.title;
        var price = p.price;
      })    
    })
})
```
로컬 json파일 불러오는 예시

<h4>post</h4>
```js
$.post('url', { key: 'value' })
  .done(function(data) {
    console.log(data);
  })
  .fail(function() {
    console.error('Error');
  });
```

### 조건 확인 선택자
<hr>

**:contains**: 선택한 요소가 특정 텍스트를 포함하는지 확인.
```javascript
if ($('.element:contains("text")').length > 0) {
 // 요소가 "text"를 포함함
}
```

**:has**: 선택한 요소가 특정 자식 요소를 포함하는지 확인.
```javascript
if ($('.element:has(.child)').length > 0) {
 // .element가 .child를 포함함
}
```

**:not**: 선택한 요소가 특정 조건을 만족하지 않는지 확인.
```javascript
$('.element:not(.excluded)').doSomething();
```

**:empty**: 선택한 요소가 자식 요소를 포함하지 않는지 확인.
```javascript
if ($('.element:empty').length > 0) {
 // 요소가 비어 있음
}
```

### 요소 비교할 때 주의
<hr>

- jQuery 객체는 일반적으로 배열과 유사한 형태로 여러 요소를 포함할 수 있으며, 바닐라 자바스크립트의 DOM 요소와는 다릅니다.
- 그래서 jQuery 객체와 바닐라 자바스크립트 DOM 요소를 직접 비교하면 원하는 결과를 얻지 못할 수 있습니다.
- jQuery에서는 `.is()` 메서드를 사용하여 jQuery 객체끼리 또는 jQuery 객체와 DOM 요소를 비교하는 것이 안전합니다.
- 바닐라 자바스크립트에서는 `===` 연산자를 사용하여 DOM 요소끼리 비교할 수 있습니다.

## Bugs

### Bootstrap 쓸 때 scrollTo가 smooth하게 움직임
<hr>

>[!bug]
>css에 이거 추가해주면 됨
	:root {
	  scroll-behavior: auto;
	}

