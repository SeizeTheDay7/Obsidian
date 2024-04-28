탐색한 태그
```html
<b></b> 볼드체 텍스트
```



head : 페이지의 속성 정보
body : 페이지의 내용

상위 요소(부모)의 속성을 바꾸면 하위 요소(자식)의 속성도 바뀐다

html 문서 안에서 css 사용법
```html
<head> ~ </html> <style> ~ </style>을 만들어 작성
// red-font라는 클래스 만들 때 .red-font{...}라고 써줘야 함
```


태그 > 클래스 > 아이디

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
```


div 전체 정렬하는 법 : 요소 전체를 감싸는 div를 만들어 width를 주고, margin: auto를 사용하면 된다.

css에 background-image만 넣으면 안되고 width랑 height도 지정해줘야 한다

<h2>background size 속성</h2>
![](Pasted%20image%2020240427184239.png)

|   |   |
|---|---|
|**속성**|**설명**|
|**auto**|원래 배경 이미지 크기만큼 표시(기본 값)|
|**contain**|지정한 요소 안에 배경 이미지가 다 들어오도록 이미지를 확대/축소|
|**cover**|지정한 요소를 다 덮도록 배경이미지를 확대/축소|
|**크기 값**|너비 값과 높이 값을 지정|
|**백분율**|지정한 요소를 기준으로 백분율 값을 지정|

특정 문자를 다른 문자로 바꾸기
```Javascript
let txt = '서울시-마포구-망원동' 
let names = txt.split('-'); // ['서울시','마포구','망원동'] 
let result = names.join('>'); // '서울시>마포구>망원동'
```


리스트와 딕셔너리 선언
```Javascript
let a_list = [1,2,'hey',3] // 다른 자료형 섞기 가능
let b_list = [1, 4, 2, [3, 1]] // 리스트 안에 리스트 넣기 가능

let a_dict = {'name':'Bob','age':21} // 딕셔너리 선언 예시

names = [{'name':'bob','age':20},{'name':'carry','age':38}]
// 딕셔너리들을 요소로 갖는 리스트도 만들 수 있음
```

CSS에서 선택자로 class를 주로 사용한다면,
jQuery에서는 고유한 하나의 요소를 가리키는 id를 주로 사용한다.


jQuery 값 인출, 입력, 삭제
```javascript
let url = $('#post-url').val(); 
// id post-url인 곳을 가리키고, val()로 값을 가져온다

let btn_next = $('#btn-posting-box').text();
// text()로 텍스트를 가져온다.

$('#post-url').val("새 글입니다");
// val()에 뭐 넣으면 값을 입력한다

$('...').empty(); // 삭제
```

jQuery div 숨기기, 보이기
```javascript
$('#post-box').hide();
$('#post-box').show();
```

백틱 = 템플릿 리터럴(Template Literals)이란?
```javascript
// 일반 문자열을 쓸 때 // 백슬래시(\)로 문자열이 다음줄에 이어짐을 알려줘야한다. // 줄바꿈 이스케이프코드인 \n로 실제로 줄바꿈을 해주어야한다. 
let a_str = "abcdefg\n\ 
				hijklmn" 

// 템플릿 리터럴을 사용할 때 
let b_str = `abcdefg 
			hijklmn`

// 일반 문자열을 쓸 때, 문자열 더하기를 이용해 긴 문자열을 만든다. console.log("num is " + num + ".") 
// 템플릿 문자열을 쓸 때 ${}를 이용해 긴 문자열 중간에 값을 넣어줄 수 있다. console.log(`num is ${num}.`)

// 탬플릿 문자열에서는 따옴표 없이 직접 HTML 태그, Javascript 변수를 작성할 수 있다.
```

페이지 로딩이 완료되면 실행하기
```javascript
<script>

#(document).ready(function(){
	alert('페이지가 로딩되었습니다')
});

</script>
```

API 기초
```
? : 여기서부터 전달할 데이터가 작성된다는 의미
& : 전달할 데이터가 더 있다는 뜻

예시) google.com/search?q=아이폰&sourceid=chrome&ie=UTF-8
```

Ajax 기본 골격
```javascript
$.ajax({
  type: "GET", // GET 방식으로 요청한다.
  url: "http://openapi.seoul.go.kr:8088/6d4d776b466c656533356a4b4b5872/json/RealtimeCityAir/1/99",
  data: {}, // 요청하면서 함께 줄 데이터 (GET 요청시엔 비워두세요)
  success: function(response){ // 서버에서 준 결과를 response라는 변수에 담음
    console.log(response) // 서버에서 준 결과를 이용해서 나머지 코드를 작성
  }
})
```
