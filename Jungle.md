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

**입력 예시는 placeholder**
```html
<input placeholder="비밀번호 입력">
```

**정중앙 정렬**
```HTML
text-align: center;
display: flex;
justify-content: center;
align-items: center;
flex-direction: column;
```

**납치 안 당하고 얌전히 클릭만 하는 `<a>`태그**
```javascript
<a href="#" onclick="return false;">test</a>
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

**객체의 속성 바꾸기**
```javascript
$("#img-cat").attr("src", imgurl);
// id가 img-cat인 개체의 src 속성을 imgurl로 바꾼다
```

**창 새로고침 시키기**
```javascript
window.location.reload();
```


<h5>함수 자체를 할당하는 방법</h5>
```javascript
link.onclick = function() { link.onclick = seeTrash(); }
```

`link.onclick = seeTrash();`와 같은 구문은 
`seeTrash`나 `returnToList` 함수를 즉시 호출하고, 
그 결과를 `onclick` 이벤트 핸들러로 할당하려고 합니다. 

이 경우, `seeTrash`와 `returnToList` 함수가 아무런 값을 반환하지 않기 때문에, 
이벤트 핸들러는 `undefined`로 설정되어 더 이상 클릭 이벤트가 동작하지 않게 됩니다.

`link.onclick = seeTrash;`는 함수를 할당하는 올바른 방법입니다. 
이렇게 하면 함수가 즉시 호출되지 않고 사용자가 링크를 클릭했을 때 호출됩니다.

<h5>JavaScript DOM API와 jQuery 차이점</h5>
**JavaScript Only**
```javascript
let link = document.getElementById('trashbin');
link.textContent = '📺 리스트 돌아가기';
link.onclick = returnToList;
showArticles('like', true);
```

**jQuery**
```javascript
$('#trashbin').text('📺 리스트 돌아가기')  // 텍스트 변경
             .off('click')               // 기존 클릭 이벤트 핸들러 제거
             .on('click', returnToList); // 새 클릭 이벤트 핸들러 할당
showArticles('like', true);
```
이거 이론상 되야 하는건데 왜 안되는건지 몰겠;
<h3>window.location</h3>
window : 브라우저 창이나 탭 자체를 의미.  팝업 열기, 창 크기 조절, URL 변경 등 가능.

| 속성       | 설명                                                  |
|------------|-------------------------------------------------------|
| `href`     | 전체 URL을 나타내며, 지정된 URL로 페이지를 이동시킵니다.  |
| `protocol` | 현재 URL의 프로토콜을 나타냅니다 (예: `http:` 또는 `https:`). |
| `host`     | 호스트 이름과 포트 번호를 포함한 URL의 일부입니다 (예: `example.com:80`). |
| `hostname` | 도메인 이름을 나타냅니다 (예: `example.com`).          |
| `port`     | URL에서 사용된 포트 번호를 나타냅니다.                 |
| `pathname` | 호스트 뒤의 URL 경로를 나타냅니다 (예: `/path/index.html`). |
| `search`   | URL의 쿼리 문자열을 나타냅니다. 첫 번째 `?` 문자 뒤의 모든 것이 포함됩니다 (예: `?key=value`). |
| `hash`     | URL의 앵커 부분을 나타냅니다. 첫 번째 `#` 문자 뒤의 모든 것이 포함됩니다 (예: `#section1`). |

| 메소드      | 설명                                                                                     |
|-------------|------------------------------------------------------------------------------------------|
| `assign(url)` | 지정된 URL로 페이지를 로드합니다. `window.location.href`를 설정하는 것과 유사합니다.         |
| `reload()`    | 현재 페이지를 새로고침합니다. 선택적으로 `true` 값을 인자로 전달하여 캐시된 버전을 무시할 수 있습니다. |
| `replace(url)`| 현재 페이지를 새 URL로 교체합니다. `assign()` 메소드와 비슷하지만, 사용자의 브라우저 세션 기록에 현재 페이지가 남지 않아 뒤로 가기 사용이 불가능해집니다. |




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

>[!bug] Bug4
>가상환경 설정해놨던거 중간에 마음대로 이름 변경하거나 경로 바꾸면 에러 파티남

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

**문자열의 비표시 문자도 포함하여 출력**
```python
print(repr(talent_name))
```


<hr>
<h1> Python: BeautifulSoup </h1>
**데이터 가져오기**
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

print(soup.prettify())
# prettify()를 붙여서 출력하면 보기 좋게 정리돼서 출력됨
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
soup.select('상위태그명 > 하위태그명 > 하위태그명') # 바로 아래에 있는 직계 자손만 검색
soup.select('상위태그명.클래스명 > 하위태그명.클래스명')
soup.select('.클래스명:nth-child(자식의순서)')
soup.select('태그명[속성="값"]')
suop.select('클래스명 태그명') # 해당 클래스의 모든 후손 태그를 검색
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

MongoDB 업데이트 연산자
사용 예시 : `db.vtuber.update_one({'name': id}, {'$inc': {'like': 1}}) # 개추 수 1개 상승`

| 연산자            | 용도                                         | 예시                                         |
| -------------- | ------------------------------------------ | ------------------------------------------ |
| `$set`         | 지정된 필드를 값으로 설정합니다. <br>필드가 없으면 필드를 추가합니다.  | `{ $set: { field: value } }`               |
| `$unset`       | 지정된 필드를 문서에서 제거합니다.                        | `{ $unset: { field: "" } }`                |
| `$inc`         | 지정된 필드의 값을 지정된 양만큼 증가시킵니다. 필드가 없으면 생성합니다.  | `{ $inc: { field: amount } }`              |
| `$push`        | 값이나 값의 세트를 배열 필드의 끝에 추가합니다. 필드가 없으면 생성합니다. | `{ $push: { field: value_or_condition } }` |
| `$pull`        | 배열 필드에서 조건과 일치하는 모든 값을 제거합니다.              | `{ $pull: { field: query } }`              |
| `$addToSet`    | 값이 배열에 존재하지 않을 경우에만 배열에 값을 추가합니다.          | `{ $addToSet: { field: value } }`          |
| `$pop`         | 배열 필드의 첫 번째 또는 마지막 항목을 제거합니다.              | `{ $pop: { field: 1 } }` (마지막 항목 제거)       |
| `$rename`      | 필드 이름을 변경합니다.                              | `{ $rename: { "old_name": "new_name" } }`  |
| `$mul`         | 필드의 값을 지정된 숫자로 곱합니다. 필드가 없을 경우 `0`을 생성합니다. | `{ $mul: { field: number } }`              |
| `$min`         | 지정된 값이 현재 값보다 작을 때만 필드를 갱신합니다.             | `{ $min: { field: value } }`               |
| `$max`         | 지정된 값이 현재 값보다 클 때만 필드를 갱신합니다.              | `{ $max: { field: value } }`               |
| `$currentDate` | 필드를 현재 날짜로 설정합니다.                          | `{ $currentDate: { field: true } }`        |



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
> - 서버로부터 정보를 조회하기 위해 설계된 메소드
> - 데이터 전달 : URL 뒤에 물음표를 붙여 key=vaule로 전달
> - URL에 데이터가 노출되어 보안에 취약함
> - 쿼리스트링을 쓰면 URL로 특정 페이지를 링크하거나 북마크 할 수 있다
> - 동일한 요청이 발생하면 캐시된 데이터를 이용 가능

> POST
> - 서버에 저장된 리소스를 생성 및 변경하기 위해 설계된 메소드
> - 데이터 전달 : HTML 메시지의 body에 key:value 형식으로 전달
> - URL에 데이터가 노출되지 않기에 보안이 조금 더 좋다
> - 반복 요청 시 동일한 결과 보장 안됨 (멱등성 없음)

> PUT
> - 서버에 저장된 데이터를 대체하거나 데이터가 없는 경우 새로 생성하기 위해 설계된 메소드
> - 데이터 전달 : HTML 메시지의 body를 통해 전달
> - 리소스 전체를 갱신하기 위해 사용되므로, 부분적인 수정은 PATCH가 적합
> - 멱등성 가짐

> DELETE
> - 서버에 저장된 리소스를 삭제하기 위해 설계된 메소드
> - 데이터 전달 : URL을 통해 삭제할 리소스 지정
> - 멱등성 가짐

> PATCH
> - 리소스의 일부분만을 수정하기 위해 설계된 메소드
> - 데이터 전달 : HTTP 메시지의 body를 통해 전달
> - PUT 메소드와 비교했을 때, 전체 리소스 대신 일부만 변경할 수 있어 효율적

> HEAD
> - GET 메소드와 동일하지만, 서버로부터 헤더 정보만을 취득하기 위해 설계된 메소드
> - 데이터 전달 : URL 뒤에 물음표를 붙여 key=value 형식으로 전달
> - 실제 데이터를 전송받지 않으므로, 리소스에 대한 메타데이터만 필요할 때 유용함

> OPTIONS
> - 서버가 지원하는 메소드를 조회하기 위해 설계된 메소드
> - 데이터 전달 : 특정 URL에 대한 서버 지원 정보를 요청
> - CORS(Cross-Origin Resource Sharing)에서 사전 요청으로 사용됨
> - 클라이언트가 리소스에 어떤 HTTP 메소드를 사용할 수 있는지 확인할 때 사용

> CONNECT
> - 네트워크 상에서 프록시 서버를 통해 터널 접속을 설정하기 위해 설계된 메소드
> - 데이터 전달 : 클라이언트와 프록시 사이에 터널을 생성
> - 주로 HTTPS 트래픽을 프록시 서버를 통해 전송할 때 사용
> - 연결된 터널을 통해 클라이언트오 서버 사이의 데이터를 보안 유지하며 전송할 수 있음


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


<h5>Javascript와 Python 간 boolean 전달</h5>
Javascript에서는 boolean이 true / false
Python에서는 boolean이 True / False 이다.
URL로 정보를 전달하면 true, false가 문자열로만 인식되므로,
아래와 같은 코드를 app.py에 추가해주어야 한다.

```python
  trash = request.args.get('trash', default='false') # 문자열로 받음
  trashMode = trash.lower() == 'true' # 'true' 문자열이면 True, 그 외에는 False
```


<hr>
<h1>Amazon EC2</h1>
**GPT 질문 정리**
[EC2 명령어 질문](EC2%20명령어%20질문.md)

접속하는 법 : git bash 열고 `ssh -i /e/Hutosuto.pem ubuntu@13.일이오.64.40`

git bash에 명령어 복붙 : 마우스 우클릭

**리눅스 명령어**
```
ls: 내 위치의 모든 파일을 보여준다.

pwd: 내 위치(폴더의 경로)를 알려준다.

mkdir: 내 위치 아래에 폴더를 하나 만든다.

cd [갈 곳]: 나를 [갈 곳] 폴더로 이동시킨다.

cd .. : 나를 상위 폴더로 이동시킨다.

cp -r [복사할 것] [붙여넣기 할 것]: 복사 붙여넣기

rm -rf [지울 것]: 지우기

sudo [실행 할 명령어]: 명령어를 관리자 권한으로 실행한다.
sudo su: 관리가 권한으로 들어간다. (나올때는 exit으로 나옴)
```

**python, pip 등록**
```shell
# python 이라는 명령어로 3 버전 이상을 실행하도록 하는 명령어입니다. 
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10

# 아래 명령어를 입력하면 pip 라고 쳐도 pip3를 작동시킬 수 있습니다. 
sudo update-alternatives --install /usr/bin/pip pip /usr/bin/pip3 1
```

>[!bug] pip install 안됨
>##서버 내에서 pip 못 사용하게 막아서 가상환경을 만들어야 함.
>sudo apt install python3.12-venv  # venv 먼저 깔고
>python -m venv .venv  # 가상환경 만들고
>source .venv/bin/activate # 가상환경 켜고
>pip install flask

>[!memo] EC2 인스턴스 보안 규칙
>인바운드 규칙 : 클라이언트가 자신의 서버 데이터에 들어올 수 있는 규칙
>아웃바운드 규칙 : 서버에서 외부로 나가는 규칙


>[!bug] mongoDB start 안됨
우분투 24.04 버전으로 했더니 다 깔고 `sudo service mongod start`했는데 에러남.
```
wget http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.0g-2ubuntu4_amd64.deb
sudo dpkg -i libssl1.1_1.1.0g-2ubuntu4_amd64.deb
```
libssl1.1이라는게 없어서 그랬음. 강제로 설치해주고 다시 mongodb 설치하니까 해결됨.

