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