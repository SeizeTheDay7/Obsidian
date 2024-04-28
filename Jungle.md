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


jQuery 값 인출, 입력
```javascript
let url = $('#post-url').val(); 
// id post-url인 곳을 가리키고, val()로 값을 가져온다

let btn_next = $('#btn-posting-box').text();
// text()로 텍스트를 가져온다.

#('#post-url').val("새 글입니다");
// val()에 뭐 넣으면 값을 입력한다
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


```