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