<h1> HTML, CSS </h1>
태그 정리
```html
<textarea rows="4" cols="50"></textarea> : 여러 줄의 텍스트 입력을 받음
```

>head : 페이지의 속성 정보
>body : 페이지의 내용

>상위 요소(부모)의 속성을 바꾸면 하위 요소(자식)의 속성도 바뀐다

>태그 > 클래스 > 아이디

**html 문서 안에서 css 사용법**
```html
<head> ~ </html> <style> ~ </style>을 만들어 작성
// red-font라는 클래스 만들 때 .red-font{...}라고 써줘야 함
```

**선택자 지정법**
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


>div 전체 정렬하는 법 : 요소 전체를 감싸는 div를 만들어 width를 주고, margin: auto를 사용하면 된다.

>css에 background-image만 넣으면 안되고 width랑 height도 지정해줘야 한다

<h4>background size 속성</h4>
![](Pasted%20image%2020240427184239.png)

|   |   |
|---|---|
|**속성**|**설명**|
|**auto**|원래 배경 이미지 크기만큼 표시(기본 값)|
|**contain**|지정한 요소 안에 배경 이미지가 다 들어오도록 이미지를 확대/축소|
|**cover**|지정한 요소를 다 덮도록 배경이미지를 확대/축소|
|**크기 값**|너비 값과 높이 값을 지정|
|**백분율**|지정한 요소를 기준으로 백분율 값을 지정|

**반응형 웹 디자인**
```html
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
```

`width=device-width` : 웹 페이지의 너비를 장치 화면의 너비에 맞추도록 지정
`initial-scale=1` : 웹 페이지의 초기 줌 레벨을 100%로 설정
`shrink-to-fit=no` : iOS 9 이상에서 웹 페이지가 화면에 맞추어 렌더링되는 것을 방지

**입력 예시**
```html
<input placeholder="비밀번호 입력">
```


<hr>

<h1>Javasciprt</h1>

특정 문자를 다른 문자로 바꾸기
```Javascript
let txt = '서울시-마포구-망원동' 
let names = txt.split('-'); // ['서울시','마포구','망원동'] 
let result = names.join('>'); // '서울시>마포구>망원동'
```

for문
```javascript
for i in range(len(fruits))
	fruit = fruits[i]
	print(fruit)
```

리스트와 딕셔너리 선언
```Javascript
let a_list = [1,2,'hey',3] // 다른 자료형 섞기 가능
let b_list = [1, 4, 2, [3, 1]] // 리스트 안에 리스트 넣기 가능

let a_dict = {'name':'Bob','age':21} // 딕셔너리 선언 예시

names = [{'name':'bob','age':20},{'name':'carry','age':38}]
// 딕셔너리들을 요소로 갖는 리스트도 만들 수 있음
```

>CSS에서 선택자로 class를 주로 사용한다면,
>jQuery에서는 고유한 하나의 요소를 가리키는 id를 주로 사용한다.


**jQuery 값 인출, 입력, 삭제**
```javascript
let url = $('#post-url').val(); 
// id post-url인 곳을 가리키고, val()로 값을 가져온다

let btn_next = $('#btn-posting-box').text();
// text()로 텍스트를 가져온다.

$('#post-url').val("새 글입니다");
// val()에 뭐 넣으면 값을 입력한다

$('...').empty(); // 삭제
```

**jQuery div 숨기기, 보이기**
```javascript
$('#post-box').hide();
$('#post-box').show();
```

**백틱 = 템플릿 리터럴(Template Literals)이란?**
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

**페이지 로딩이 완료되면 실행하기**
```javascript
<script>

#(document).ready(function(){
	alert('페이지가 로딩되었습니다')
});

</script>
```

**API 기초**
```
? : 여기서부터 전달할 데이터가 작성된다는 의미
& : 전달할 데이터가 더 있다는 뜻

예시) google.com/search?q=아이폰&sourceid=chrome&ie=UTF-8
```

**Ajax 기본 골격**
```javascript
$.ajax({
  type: "GET", // GET 방식으로 요청한다.
  url: "여기에 URL 입력", // 서버 상의 특정 엔드포인트('memo') 가리킴
  data: {}, // 요청하면서 함께 줄 데이터 (GET 요청시엔 비운다)
  success: function(response){ // 서버에서 준 결과를 response라는 변수에 담음
    console.log(response) // 서버에서 준 결과를 이용해서 나머지 코드를 작성
  }
})
```

**개발자 도구 콘솔에 도봉구 미세먼지 값 찍어보기**
``` javascript
// $.ajax 메서드를 사용하여 AJAX 요청을 설정합니다.
$.ajax({
  type: "GET", // 요청의 타입을 GET으로 설정합니다. 
  // GET은 서버로부터 정보를 조회할 때 사용합니다.
  
  url: "http://openapi.seoul.go.kr:8088/6d4d776b466c656533356a4b4b5872/json/RealtimeCityAir/1/99", // 요청을 보낼 URL입니다. 이 URL은 서울시 대기질 정보 API.
  
  data: {}, // 요청과 함께 서버로 보낼 데이터입니다. 
  // 이 경우, 별도의 데이터를 보내지 않으므로 빈 객체를 사용합니다.

  success: function(response) { 
    // 서버로부터 응답을 성공적으로 받았을 때 실행될 함수입니다.
    // response 객체에서 도봉구의 대기 질 정보를 가져옵니다. 
    let dobong = response["RealtimeCityAir"]["row"][11]; 
    // 'row' 배열의 12번째(인덱스는 11) 요소가 도봉구의 데이터입니다.
    let gu_name = dobong['MSRSTE_NM']; 
    // 'MSRSTE_NM' 키를 통해 구 이름을 가져옵니다.
    let gu_mise = dobong['IDEX_MVL']; 
    // 'IDEX_MVL' 키를 통해 미세먼지 수치를 가져옵니다.
    console.log(gu_name, gu_mise); 
    // 콘솔에 구 이름과 미세먼지 수치를 출력합니다.
  }
})

```

```javascript
$("#img-cat").attr("src", imgurl);
// id가 img-cat인 개체의 src 속성을 imgurl로 바꾼다
```


<hr>
<h1>Python</h1>

>VSCode에서 대화형 인터프리터 열기 : Shift + Enter

```python
sentence = 'He said, "Hello!"'
# 문자열에 따옴표가 포함될 경우, 다른 종류의 따옴표를 써서 문자열 정의

a = "3" b = "5" 
a + 5 # 파이썬에서는 문자열과 숫자형은 더할 수 없다 
a * 5 # 33333 a*5는 a+a+a+a+a과 같으므로 "3"이 5번 반복되는 문자열이 반환된다.

result = myemail.split('@') # 특정 문자열 기준 나누기
result = txt.replace('-', '>') # 특정 문자를 다른 문자로 나누기
```

```python
x = True # 참 
y = False # 거짓
# 소문자로 쓰면 자료형으로 인식하지 않고 변수명이라 생각해 에러가 난다. 
z = true # name 'true' is not defined
```

```python
a_list = [] 
a_list.append(1) # 리스트에 값을 넣는다 
a_list.append([2,3]) # 리스트에 [2,3]이라는 리스트를 다시 넣는다

len(a_list) # 2 리스트의 길이
```

```python
a_dict = {}
a_dict = {'name':'bob','age':21}
a_dict['height'] = 178
# a_dict의 값은? {'name':'bob','age':21, 'height':178}

people = [{'name':'bob','age':20},{'name':'carry','age':38}]
# people[0]['name']의 값은? 'bob'
```

```python
# 파이썬에서 함수 선언 방법
def f(x):
    return 2*x+3   # 중괄호 대신에 들여쓰기로 각 블록의 범위를 표시한다.
```

>[!bug] 
powershell에서 디렉토리를 변경할 때 경로에 공백이 포함되어 있으면 오류가 발생함
'cd 'C:\Users\bioma\OneDrive\바탕 화면\Jungle' 이렇게 따옴표로 감싸야 한다

**파이썬 가상환경**
```
vscode에서 terminal 종류를 cmd로 바꿀 것

python -m venv (가상환경이름) //cd로 루트 디렉토리로 설정하고 새 가상환경 만들기

(가상환경이름)\Scripts\activate //가상환경 활성화
```

>[!bug] Bug1
>보안 문제로 활성화가 실패하면 PowerShell에서 다음 명령어 실행
>Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

>[!bug] Bug2
>PowerShell에서는 activate 대신 .\activate 라고 해야 가상환경 실행됨

>[!bug] Bug3
>cmd에서는 .venv만 하지 말고 전체 경로를 복붙해야됨

>[!Success]
>Ctrl+Shift+P → Python: Select Interpreter
>하면 Ctrl+F5로 바로 가상환경에서 실행 가능

**리스트 컴프리헨션**
```python
numbers = [2*x for x in range(10)]
# 1부터 10까지의 숫자를 2배 한 숫자의 리스트를 생성한다.

(year, month, day) = [int(element) for element in date.split('.')]
# date.split()으로 쪼개진 년, 월, 일을 리스트 컴프리헨션으로 리스트화하고
# year, month, day 변수에 삽입한다.

viewers = int(''.join([c for c in viewers if c.isdigit()]))
# viewers에서 숫자 데이터만 가져온다
# ''.join은 리스트의 요소 사이에 아무런 문자도 추가하지 않고 그대로 연결한다는 뜻
```

>if __name__ == “__main__”의 의미
>: 해당 모듈이 임포트된 경우가 아니라 인터프리터에서 직접 실행한 경우에만 실행해라.

<hr>
<h1> Python: BeautifulSoup </h1>
데이터 가져오기
```python
headers = {'User-Agent' : 'Mozilla/5.0 (Windows NT 10.0; Win64; x64)AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.86 Safari/537.36'}
# HTTP 요청 헤더를 딕셔너리 형태로 추가한다. 웹 서버는 이 헤더 정보를 사용하여 사용자에게 응답한다.
# User-Agent 헤더는 요청을 보내는 클라이언트의 유형을 식별하는데 사용한다

data = requests.get('https://serieson.naver.com/v3/movie/ranking/realtime', headers=headers)
# 타겟 URL을 읽어서 HTML을 받아온다

soup = BeautifulSoup(data.text, 'html.parser')
print(soup)
# 받아온 HTML을 BeautifulSoup라는 라이브러리로 검색하기 용이한 상태로 만듦
# soup라는 변수에 "파싱 용이해진 html"이 담긴 상태가 됨
```

**Select**
```python
#select를 이용해서, li들을 불러오기
# select()는 조건을 만족하는 모든 요소를 리스트에 담아 반환
# select_one()은 첫번째로 나오는 요소를 반환
movies = soup.select('.RankingList_ranking_list__N4QsH > li')
title = movie.select_one('.Title_title__s9o0D')


# 선택자를 사용하는 방법 (copy selector)
soup.select('태그명')
soup.select('.클래스명')
soup.select('#아이디명')
soup.select('상위태그명 > 하위태그명 > 하위태그명')
soup.select('상위태그명.클래스명 > 하위태그명.클래스명')
soup.select('.클래스명:nth-child(자식의순서)')
soup.select('태그명[속성="값"]')
```

출력 예시
```python
movies = soup.select('.RankingList_ranking_list__N4QsH > li')

for movie in movies:
  title = movie.select_one('.Title_title__s9o0D')
  RentOrBuy = movie.select_one('.Price_text__pRk_f')
  print(f"{title.text} {RentOrBuy.text}")
```

findChild 메서드
```python
tag_element = movie.select_one('.txt_info > .info_txt:nth-child(2)')
viewers = tag_element.findChild(string=True, recursive=False)

# findChild : BeautifulSoup의 메서드이다. 주어진 요소의 자식들 중에서 특정 조건에 맞는 첫번째 요소를 찾는다.

# string=True : 찾고자 하는 자식이 문자열 노드(즉, 태그 사이의 텍스트)일 때 사용
# HTML 태그가 아닌, 순수한 텍스트 내용을 찾는다.

# recursive=False : 검색을 현재 요소의 바로 아래 직계 자식에만 한정짓는다.
# True로 설정하면(기본값), 요소의 모든 하위 자식들을 재귀적으로 검색한다.
```

<hr>
<h1> MongoDB </h1>

Database의 종류
1. RDBMS(SQL)
    - 행/열의 생김새가 정해져 있다.
    - 열 중간에 데이터를 삽입하는 것은 어렵다.
    - 정형화되어 있어 데이터가 일관적이고 분석에 용이하다.
2. NoSQL(NotOnlySQL)
	- 딕셔너리 형태로 데이터를 저장한다.
	- 데이터 하나하나마다 같은 필드 값을 가질 필요가 없다.
	- 자유로운 형태의 데이터 적재에 유리하다.
	- 일관성이 부족하다.


<hr>
<h1>pymongo</h1>

**1. Setting up**
```python
from pymongo import MongoClient
client = MongoClient('localhost', 27017) # mongoDB는 27017 포트를 사용한다
db = client.jungle # 'jungle'이라는 이름의 db를 만든다.
```

**2. Inserting data
```python
# 'users'라는 collection에 {'name':'bobby','age':21}를 넣는다. db.users.insert_one({'name':'bobby','age':21})
```

**3. 데이터 조회
```python
all_users = list(db.users.find({})) # 데이터 모두 보기 

same_ages = list(db.users.find({'age':21})) # 특정 조건 데이터 보기

user = db.users.find_one({'name':'bobby'},{'_id':False})
# 특정 결과 값 뽑아 보기 (그 중 id는 빼고 보기)
```

**4. 데이터 수정
```python
db.people.update_many(찾을조건,{ '$set': 어떻게바꿀지 })
# people이라는 collection에서 특정 조건에 해당하는 모든 문서들의 데이터를 수정
# '$set'은 MongoDB의 업데이트 연산자로, 지정된 필드의 값을 새로운 값으로 변경한다.

db.users.update_one({'name':'bobby'},{'$set':{'age':19}})
# users 컬렉션에서 name 필드가 bobby인 문서를 찾아서 age 필드를 19로 설정한다

db.users.delete_one({'name':'bobby'})
# 삭제하기
``` 

**list 붙이는 이유**
```python
movies = list(db.movies.find({'open_month':target_month}))

# pymongo의 find 메서드는 Cursor 객체를 반환한다.
# Cursor는 데이터베이스에서 실제로 데이터를 가져오기 전까지는 데이터가 없다.

# list 함수를 사용하여 Cursor를 리스트로 변환하면, 데이터가 메모리로 로드된다.
# 이렇게 하면 데이터베이스로의 추가적인 요청 없이도 데이터를 사용할 수 있다.
```

**제외할 필드 설정**
```python
result = list(db.articles.find({}, {'_id': 0}))
```
MongoDB에서는 조회하는 동안 특정 필드를 포함/제외 할 수 있다. 이를 프로젝션이라 한다.
프로젝션은 쿼리의 2번째 인자로 전달되며, 포함할 필드는 '1', 제외할 필드는 '0'을 지정한다.



<hr>
<h1>Flask</h1>

>[!note] 라우팅이란?
>
>쉬운 말 : `/about` 페이지를 요청하면 "About" 페이지에 대한 정보를, 
>`/contact` 페이지를 요청하면 "Contact" 페이지에 대한 정보를 제공하게 하는 것. 
>
>어려운 말 : 서버가 올바른 요청 핸들러나 컨트롤러에 HTTP 요청을 전달하는 과정

flask 서버 만들 때 기본적으로 만들 것
1.  templates 폴더 : HTML 파일을 저장해놓음
2. static 폴더 : css, 이미지 파일 등을 저장해놓음
3. app.py : 통상적으로 flask 서버를 돌리는 파일은 app.py로 이름짓는다.


일반 HTML에서 img를 불러올 때 
```html
<img src="../static/rome.jpg"/>

// ..는 해당 html 파일이 있는 폴더의 상위 폴더를 의미함
```

flask에서 불러올 때 
```HTML
<img src="{{ url_for('static', filename='rome.jpg') }}"/>
```

> GET
> - 보통 데이터 조회(Read)를 요청할 때 사용
> - 데이터 전달 : URL 뒤에 물음표를 붙여 key=vaule로 전달

> POST
> - 보통 데이터 생성(Create), 변경(Update), 삭제(Delete) 요청할 때 사용
> - 데이터 전달 : 바로 보이지 않는 HTML body에 key:value 형태로 전달


**request.form** : 클라이언트가 POST 요청으로 전송한 폼 데이터에 접근할 수 있는 딕셔너리 객체

예를 들어, 클라이언트 측 HTML 폼이 다음과 같다면,
```HTML 
<form action="/memo" method="post">
    <input type="text" name="url_give" value="https://example.com">
    <button type="submit">Submit</button>
</form>
```

이 폼을 사용자가 서버에 제출하면, 입력한 URL이 '/memo' 경로의 POST 메서드로 전송된다. 그것을
```Python
url_receive = request.form['url_give']  # 클라이언트로부터 url을 받는 부분
```
로 선언하여 클라이언트가 'url_give'라는 이름으로 보낸 데이터를 추출할 수 있다.
