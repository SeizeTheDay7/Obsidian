UI 만드는 step
1. HTML/CSS로 미리 디자인
2. 필요할 때 보여달라고 코드짬 (자바스크립트로)

JS코드는 밑에 짜야 한다. body 태그 끝나기 직전에 넣어주자.
DOM 만들어놔야 그걸 조작하니까 그렇다.
jquery같은 외부 js 라이브러리도 역시 body 태그 끝에 넣자. (대신 작성한 js 코드보다는 위에)

addEventListener를 쓰면 onclick으로 함수 할당 안해도 알아서 script가 클릭한거 인식해줌 

```js
<div id="alert" class="alert-box"><button id="close">X</button></div>

document.getElementById('alert').addEventListener('click', function() {
      document.getElementById('alert').style.display = none;
});
```
이벤트 위임 : 자식 요소를 클릭해도 부모 요소까지 클릭 이벤트가 전파됨. 

콜백함수 : 파라미터 자리에 들어가는 함수를 콜백함수

```js
document.querySelector('.list-group').classList.toggle('d-none');
```
toggle('클래스명')은 해당 클래스가 있으면 제거하고, 없으면 추가

jquery
$('.classname') : 요소 선택
on('event', function() {}) : addEventListener

```js
$('.hello').html('바보');
$('.hello').css('color', 'red');
$('.hello').addClass('d-none');
$('.hello').removeClass('d-none');
$('.hello').toggleClass('d-none');

$('test-btn').on('click', function(){
  // 코드
})
```
요소 하나씩 선택되는게 아니라 한꺼번에 선택된다 (querySelectorAll 처럼)

숨기려고 할 때 : $(요소).hide(), $(요소).fadeOut(), slideUp() 등 있음

UI에 애니메이션 추가할 때 JS 쓰면 성능 느려지니 가급적 CSS만으로 처리하는게 좋음

애니메이션 줄 땐 `display: none`보다는 `visibility: hidden` 쓰는게 좋다

```css
.black-bg {
  width: 100%;
  height: 100%;
  position: fixed;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 5;
  visibility: hidden;
  opacity: 0;
  transition: all 0.5s;
}
.show-modal {
  visibility : visible;
  opacity : 1;
}

$('#login').on('click', function(){
  $('.black-bg').toggleClass('show-modal');
})
$('#close').on('click', function(){
  $('.black-bg').removeClass('show-modal');
})
```
모달창 서서히 등장하는거 구현하는법


```js
$('#loginForm').on('submit', function(){
  if($('#loginForm input[type="text"]').val().trim()=='') {
	alert('안돼');
	event.preventDefault();
  }
})
```
입력란이 공백이면 제출 안되게

on('input', function(){}) :  input 태그에 있는 값이 변할 때 작동
on('change', function(){}) : input 태그에 있는 값을 바꾸고 focus 잃으면 (다른 곳 누르면) 작동


|            | 재선언                 | 재할당                | 범위                  |
|------------|------------------------|-----------------------|-----------------------|
| let        | 불가능                 | 가능                  | 블록 스코프 `{}`       |
| const      | 불가능                 | 불가능                | 블록 스코프 `{}`       |
| var        | 가능                   | 가능                  | 함수 스코프 `function`  |

```js
setTimeout(function() {
  $('.alert').fadeOut(1000);
}, 1000)

setInterval(함수, 1000)

function 함수() {
  console.log('1초 경과');
}
```

setTimeout(function(){실행할코드}, ms) : N초 후 코드 실행
setInterval(function(){실행할코드}, ms) : N초 마다 코드 실행

setTimeout삭제하려면 var 타이머 = setTimeout(어쩌구); 이렇게 변수에 저장해두고 clearTimeout(타이머) 실행하면 됨. Interval은 clearInterval하면 됨.

문자 검사하는 방법
```js
'문자'.includes('찾을단어');
```
이렇게 간단하게 할 수도 있지만

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
정규식으로 검사하면 여러 문법 사용 가능

```js
$('.slide-1').click(function() {
  $('.slide-container').css('transform', 'translateX(0)');
})
```
on('click',function (){}) 대신 click(function(){})으로 바로 가능한듯


window.scrollY : 현재 스크롤 얼마나 내렸는지
window.scrollTo(x,y) : 강제로 스크롤하기
window.scrollTop() : 현재 스크롤바 위치 출력 (숫자 넣으면 이동도 함)
window.scrollHeight : 요소 스크롤 높이

jquery 버전
$(window).scrollTop()

**jQuery**
```js
var 스크롤양 = $('.lorem').scrollTop(); // 가져오기
$('.lorem').scrollTop(100); // 설정하기
```
**순수 JavaScript**:
```js
var loremElement = document.querySelector('.lorem');
var 스크롤양 = loremElement.scrollTop; // 가져오기
loremElement.scrollTop = 100; // 설정하기
```
두 방법 모두 수직 스크롤 위치를 가져오거나 설정하는 데 사용되지만, jQuery에서는 메서드 체이닝을 통해 더 간단하게 사용할 수 있고, 순수 JavaScript에서는 속성에 직접 접근해야 합니다.

>[!bug]
>Bootstrap 쓰면 scrollTo가 smooth하게 움직이는데 
```css
:root {
  scroll-behavior: auto;
}
```
css에 이거 추가해주면 됨


```js
var 실제높이 = $('.lorem').prop('scrollHeight');
var 스크롤양 = $('.lorem').scrollTop();
var 높이 = $('.lorem').height();
```
실제높이랑 스크롤양 찍어보면 다름.
스크롤양은 박스가 보이는 높이는 포함 안하기때문.
그래서 실제높이에서 박스높이 빼줘야 전체 스크롤양 됨.
- 스크롤 다 봤는지 조건문 걸때 여유 오차 좀 줘야 함
- body 태그 끝나기 전에 측정해야 정확하게 나옴


```js
$(this).addClass('orange').siblings().removeClass('orange');
```
이벤트 받은 요소에만 클래스 추가하고 나머지 형제 요소들에서는 클래스 제거

```js
$('.tab-button').click(function() {
  var index = $(this).index();
  $(this).addClass('orange').siblings().removeClass('orange');
  $('.tab-content').eq(index).addClass('show').siblings('.tab-content').removeClass('show');
});
```
클릭한 요소가 형제 요소들 중 몇 번째인지 가져온 뒤 
바꾸고 싶은 다른 요소도 같은 순서에서 클래스 변화

```js
$('.tab-button').click(function() {
  var index = $(this).index();
  $('.tab-button').removeClass('orange');
  $(this).addClass('orange');
  $('.tab-content').removeClass('show');
  $('.tab-content').eq(index).addClass('show')
});
```
이해하기는 이게 더 쉬울수도


모든 브라우저는 이벤트 버블링이 일어남
(이벤트가 상위 html로 퍼지는 현상)

이벤트리스너의 콜백함수에 파라미터 아무거나 추가하면 
이벤트관련 유용한 함수들을 사용 가능. 
파라미터 이름은 아무렇게나 작명. 보통 e라고 함.

**e.target**은 실제 클릭한 요소 알려줌 (이벤트 발생한 곳)
**e.currentTarget**은 이벤트 리스너가 달린 곳 알려줌 (참고로 this라고 써도 똑같음)
**e.preventDefault()** 실행하면 이벤트 기본 동작을 막아줌
**e.stopPropagation()** 실행하면 내 상위요소로의 이벤트 버블링을 중단해줌

$('.black-bg')를 queryselector랑 비교하면 조금 다르니까
```
$(어쩌구).is($(어쩌구))
```
jquery는 이렇게 비교하는게 안전


html 태그에 몰래 정보 숨기기 가능 
```html
<button data-자료이름="값"></button>
```
숨겼던 자료 출력은
```js
e.target.dataset.자료이름 // 바닐라 js
e.target.data('자료이름') // jqeury
```

자료형
```js
var car = ['소나타', 50000, 'white']; // array
var car2 = {name : '소나타', price : 50000} // object
car2['price'] // object 자료 호출법 
car2.price // 이렇게 하면 변수는 못 넣음
```

서버 사이드 렌더링 : 완성품 html을 서버가 줌 (서버가 힘듬)
클라이언트 사이드 렌더링 : 빈 html이랑 데이터 주면 유저가 완성 (서버가 편함)


문자 중간에 변수 넣는 법
```js
var a = '안녕';
`문자${a}문자`
```

요소 만들고 내용 넣기
```js
var a = document.createElement('p');
var b = $('<p></p>');
a.innerHTML = '안녕';
b.html('안녕');
```

foreach 반복문
```js
array.forEach(function(item,i) { //item만 써도 
  console.log(123)
})
```
function 안의 파라미터
- 1번째 : array 안의 데이터
- 2번째 : 0부터 1씩 증가하는 정수

object 자료 반복
```js
var obj = {name : 'kim', age : 20}

for (var key in obj) {
  console.log(key);
}
```

get 요청 날리기 (jquery)
```js
$.get('url~~~')
	.done(function(data) {
		console.log(data); // 받아온 데이터 출력
	})
	.fail(function() {
		// ajax 실패했을 때
	})
```
jquery 안 쓸거면 fetch('url~') 이런 것도 있음 ($.get은 자동으로 json을 객체로 변환해주는데 fetch는 따로 변환해줘야됨)

문자 정렬은 array.sort();
숫자 정렬은
```js
array.sort((a,b) => a-b);
```
원리
1. a, b는 array 안의 자료
2. return이 양수면 a를 오른쪽으로
3. return이 음수면 b를 오른쪽으로
4. 그걸 전부 다 해봄

문자 내림차순 정렬은
```js
arr.sort(function(a, b) {
  if(a < b) return 1;
  if(a > b) return -1;
  if(a === b) return 0;
});
```
간략하게는
```js
// 내림차순 정렬
arr.sort((a, b) => b.localeCompare(a));
// 오름차순 정렬
arr.sort((a, b) => a.localeCompare(b));
```


얕은 복사 : 객체의 주소만 복사. 복사본 변경하면 원본도 변경됨. 역도 마찬가지.
깊은 복사 : 새롭게 메모리 차지하는 복사. 서로 영향 안 미침.

스프레드 연산자 : 배열이나 객체 펼쳐서 개별 요소나 속성으로 나열. 얕은 복사임.
```js
let originalArray = [1, 2, 3];
let copiedArray = [...originalArray];
```

filter
```js
var newArray = array.filter(a => a < 4);
```
sort는 원본을 변형시키는데 filter는 따로 담아야 됨.

map
```js
var newArray = array.map(a => a * 2);
```
배열 안의 데이터를 일괄 변경

```js
$(document).ready(function(){ 실행할 코드 })
document.addEventListener('DOMContentLoaded', function() { 실행할 코드 })
```
"이 코드는 HTML 전부 다 읽고 실행해주세요"라는 뜻. 둘 중 하나 쓰면 됨.
(요즘은 자바스크립트를 `<body>`태그 끝나기 전에 전부 작성하긴 함)

load 이벤트리스너
```js
셀렉터로찾은이미지.addEventListener('load', function(){
  //이미지 로드되면 실행할 코드 
})
```
DOM 생성뿐만 아니라 이미지, css, js 파일이 로드됐는지도 체크 가능
(근데 외부 자바스크립트 파일에 적으면 그 js파일보다 이미지가 먼저 로드될수도 있음)

```js
$(window).on('load', function(){
  //document 안의 이미지, js 파일 포함 전부 로드가 되었을 경우 실행할 코드 
});

window.addEventListener('load', function(){
  //document 안의 이미지, js 파일 포함 전부 로드가 되었을 경우 실행할 코드
})
```
윈도우에 붙일수도 있음. 모든 파일과 이미지의 로드를 체크함.
(다 로딩되면 사이트 보여주세요~ 라고 코드 짜면 로딩 너무 느려짐)\

>[!note] 브라우저 저장 공간
Local Storage / Session Storage (key : value 형태로 문자, 숫자 데이터 저장가능)
Indexed DB (크고 많은 구조화된 데이터를 DB처럼 저장가능, 문법더러움)
Cookies (유저 로그인정보 저장공간)
Cache Storage (html css js img 파일 저장해두는 공간)

Local Storage : 브라우저 재접속해도 영구적으로 남아있음
Session Storage : 브라우저 끄면 날아감

Local Storage 사용법
```js
localStorage.setItem('이름', 'kim') //자료저장하는법
localStorage.getItem('이름') //자료꺼내는법
localStorage.removeItem('이름') //자료삭제하는법
```

Local Storage에 배열, 객체 저장
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

Local Storage에 넣었던거 수정하려면
1. 자료 꺼냄
2. 꺼낸거 수정
3. 다시 넣음

null 무시하는 문법
```js
var test = A || B;
```
A가 falsy (거짓 같은 값, 즉, null, undefined, 0, '' 등) 이면 B 반환

마우스 관련 이벤트 : onclick 또는 on에 넣는다
mousedown (어떤 요소에 마우스버튼 눌렀을 때) 
mouseup (어떤 요소에 마우스버튼 뗐을 때)
mousemove (어떤 요소위에서 마우스 이동할 때)

모바일에선 touch로 바꿔야 됨
touchstart
touchmove
touchend

이벤트 변수 달면 좌표도 알 수 잇다
```js
$('.slide-box').eq(0).on('mousemove', function(e) {
  console.log(e.clientX);
})
```

드래그 구현 방법
```js
$('.slide-box').eq(0).on('mousedown', function(e) {
  시작좌표 = e.clientX;
})
$('.slide-box').eq(0).on('mousemove', function(e) {
  console.log(e.clientX - 시작좌표);
})
```
img에 draggable = "false" 줘야된다.

json파일 불러오기
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


## 드래그 & 드랍 이벤트

[참고](inpa.tistory.com/entry/드래그-앤-드롭-Drag-Drop-기능)

jquery 쓰면 event 객체 쓸 때 originalEvent 붙여야 해서 오히려 불편하다.
평범하게 adEventListener로 붙이는게 나은듯.

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

### dataTransfer

dataTransfer 객체는 드래그 앤 드롭 동작 동안 데이터를 전달하는 데 사용

- **setData(format, data)**: 드래그하는 동안 전송할 데이터를 설정. `format`은 데이터 형식을 지정하고, `data`는 전송할 실제 데이터를 지정. 예를 들어, `e.dataTransfer.setData('text/plain', 'Hello, World!')`는 텍스트 형식의 데이터를 설정.
- **getData(format)**: 드롭 시 전달된 데이터를 가져옴. `format`은 데이터를 설정할 때 사용된 형식을 지정. 예를 들어, `e.dataTransfer.getData('text/plain')`은 설정된 텍스트 데이터를 가져옴.

**text/plain**: 텍스트 형식. 순수 텍스트 데이터를 전달할 때 사용합니다.
```javascript
e.dataTransfer.setData('text/plain', 'Hello World');
```

**text/html**: HTML 형식. HTML 문자열을 전달할 때 사용합니다.
```js
e.dataTransfer.setData('text/html', '<p>Hello World</p>');
```

**text/uri-list**: URI 목록 형식. URI 목록을 전달할 때 사용합니다.
```js
e.dataTransfer.setData('text/uri-list', 'http://example.com');
```

**application/json**: JSON 형식. JSON 데이터를 전달할 때 사용합니다.
```js
e.dataTransfer.setData('application/json', JSON.stringify({ key: 'value' }));
```

**application/xml**: XML 형식. XML 데이터를 전달할 때 사용합니다.
```js
e.dataTransfer.setData('application/xml', '<note><to>User</to><message>Hello</message></note>');
```

**Files**: 파일 형식. 파일을 드래그 앤 드롭할 때 사용합니다. 파일 형식은 `setData`로 설정하지 않지만, `dataTransfer` 객체의 `files` 속성을 통해 액세스할 수 있습니다.
```js
var files = e.dataTransfer.files;
```

**Custom Formats**: 사용자 지정 형식. 커스텀 데이터를 전달할 때 사용합니다.
```js
e.dataTransfer.setData('application/x-my-custom-format', 'Custom Data');
```

### dropEffect

dropEffect 속성은 드래그 앤 드롭 동작 동안 드롭할 때 발생할 동작을 설정. 이 속성은 드래그되는 동안 커서의 모양을 변경하여 사용자가 드롭이 어떻게 처리될지 시각적으로 알 수 있도록 함.

- **`none`**: 드롭이 허용되지 않습니다.
- **`copy`**: 드롭하면 데이터가 복사됩니다.
- **`move`**: 드롭하면 데이터가 이동됩니다.
- **`link`**: 드롭하면 데이터에 대한 링크가 생성됩니다.


jQuery의 `$(document).on('event', 'selector', handler)` 메서드는 이벤트 위임(event delegation)이라는 기법을 사용하여 동적으로 추가된 요소에도 이벤트를 바인딩할 수 있게 해줍니다. 이를 통해 페이지 로드 이후에 추가되거나 변경된 요소에도 동일한 이벤트를 적용할 수 있습니다.

```js
$(document).on('click', '.dynamic-button', function() {
    alert('Button clicked!');
});
```

위 코드에서는 `.dynamic-button` 클래스를 가진 버튼 요소에 클릭 이벤트를 바인딩하고 있습니다. 이 방식의 장점은 `.dynamic-button` 요소가 나중에 동적으로 추가되더라도 클릭 이벤트가 정상적으로 동작한다는 것입니다.



include
```js
let str = "Hello, world!";
if (str.includes("world")) {
  // "world"가 str에 포함되어 있는 경우 실행할 코드
}

let arr = [1, 2, 3, 4, 5];
if (arr.includes(3)) {
  // 3이 arr에 포함되어 있는 경우 실행할 코드
}
```
배열이나 문자열에 특정값이 포함되어 있는지를 확인

contains(jquery)
```js
const titleSelector = `.card-title:contains("${data.title}")`;
if ($(titleSelector).length > 0) {
 // 특정 제목을 가진 카드가 존재한다면 실행할 코드
}
```
특정 텍스트를 포함하는 요소를 선택할 때 사용함.
텍스트가 요소 내 어디에 있든 관계없이 선택됨.


jquery 요소 순회는 foreach가 아니라 each로 해줘야 함