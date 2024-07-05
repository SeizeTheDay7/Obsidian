- [[#백준 관련|백준 관련]]
	- [[#백준 관련#입력받을 때|입력받을 때]]
- [[#최대 재귀 깊이 설정|최대 재귀 깊이 설정]]
- [[#자료형|자료형]]
	- [[#자료형#기본 자료형|기본 자료형]]
	- [[#자료형#컬렉션 자료형|컬렉션 자료형]]
		- [[#컬렉션 자료형#list 조작|list 조작]]
	- [[#자료형#컬렉션 모듈|컬렉션 모듈]]
- [[#문법|문법]]
	- [[#문법#함수|함수]]
	- [[#문법#반복문|반복문]]
	- [[#문법#변수 출력|변수 출력]]
	- [[#문법#입력 받기|입력 받기]]
	- [[#문법#문자열을 리스트로 바꾸기|문자열을 리스트로 바꾸기]]
	- [[#문법#아스키 코드 변환|아스키 코드 변환]]
	- [[#문법#리스트 컴프리헨션|리스트 컴프리헨션]]
- [[#키에 대한 예외 처리|키에 대한 예외 처리]]
- [[#문자열 날짜로 변환|문자열 날짜로 변환]]
- [[#pymongo|pymongo]]
	- [[#pymongo#세팅|세팅]]
	- [[#pymongo#데이터 삽입|데이터 삽입]]
	- [[#pymongo#데이터 조회|데이터 조회]]
	- [[#pymongo#데이터 수정|데이터 수정]]
	- [[#pymongo#list 붙이는 이유|list 붙이는 이유]]
	- [[#pymongo#제외할 필드 설정|제외할 필드 설정]]
	- [[#pymongo#업데이트 연산자|업데이트 연산자]]




>[!note] if name == "main" 의미
해당 모듈이 임포트된 경우가 아니라 인터프리터에서 직접 실행한 경우에만 실행해라.


## 백준 관련
<hr>

### 입력받을 때
```python
import sys  
a = list(map(int, sys.stdin.readline().strip())
# a = [1, 2, 3, 4, 5]
```

**여러 라인 입력 받을 때**
```python
import sys  
n = input()  
a = [sys.stdin.readline().strip().split() for _ in range(n)]  
# a = ["1 2 3", "4 5 6"]
```
성능이 향상된다.

```python
S = [list(map(int, sys.stdin.readline().strip().split())) for _ in range(N)]
for line in S:
    print(line)
# [1, 2, 3] [4, 5, 6] [7, 8, 9]
```

## 최대 재귀 깊이 설정
```python
import sys  
sys.setrecursionlimit(10**8) # 10^8 까지 늘림.
```
DFS, BFS 문제의 경우 재귀 허용 깊이를 수동으로 늘려주는 코드를,코드 상단에 적어줘야 한다. (PyPy에서는 안됨)

## 자료형
<hr>

### 기본 자료형

| 자료형      | 설명      |
| -------- | ------- |
| int      | 정수형     |
| float    | 실수형     |
| str      | 문자열     |
| bool     | 불리언     |
| NoneType | None 객체 |

### 컬렉션 자료형

**list**: 순서가 있는 가변 시퀀스
```python
my_list = [1, 2, 3, 4, 5]
```

```python
N = 3
matrix = [[0] * N for _ in range(N)]
```
'N x N ' 크기의 행렬 생성

**tuple**: 순서가 있는 불변 시퀀스
```python
my_tuple = (1, 2, 3, 4, 5)
```

**set**: 순서가 없는 유일한 값들의 모음
```python
my_set = {1, 2, 3, 4, 5}
```

**dict**: 키-값 쌍의 모음
```python
my_dict = {"one": 1, "two": 2, "three": 3}
```

**frozenset**: 불변 세트
```python
my_frozenset = frozenset([1, 2, 3, 4, 5])
```

#### list 조작
**append**: 요소 추가하기
```python
>>> a.append([5, 6])
>>> a
[1, 2, 3, 4, [5, 6]]
```

**sort**: 요소 순서대로 정렬
```python
>>> a = [1, 4, 3, 2]
>>> a.sort()
>>> a
[1, 2, 3, 4]
```

**reverse**: 요소 뒤집기
```python
>>> a = ['a', 'c', 'b']
>>> a.reverse()
>>> a
['b', 'c', 'a']
```

**in**: 특정 값 존재 확인
```python
my_list = [1, 2, 3, 4, 5]

# 특정 값이 리스트에 있는지 확인
value = 3
if value in my_list:
```

**index**: 인덱스 반환
``` python
>>> a = [1, 2, 3]
>>> a.index(3)
2
>>> a.index(1)
0
```

**insert**: 요소 삽입
```python
>>> a = [1, 2, 3]
>>> a.insert(0, 4)
>>> a
[4, 1, 2, 3]
```
insert(a,b)는 리스트의 a번째 위치에 b를 삽입하는 함수

**remove**: 요소 제거
```python
>>> a = [1, 2, 3, 1, 2, 3]
>>> a.remove(3)
>>> a
[1, 2, 1, 2, 3]
```
첫 번째로 나오는 x 제거

**pop**: 요소 꺼내기
```python
>>> a = [1, 2, 3]
>>> a.pop()
3
>>> a
[1, 2]
```
맨 마지막 요소를 리턴하고 그 요소 삭제

**count**: 요소 개수 세기
```python
>>> a = [1, 2, 3, 1]
>>> a.count(1)
2
```
안에 x가 몇 개 있는지 개수 리턴

**extend**: 리스트 확장
```python
>>> a = [1, 2, 3]
>>> a.extend([4, 5])
>>> a
[1, 2, 3, 4, 5]
>>> b = [6, 7]
>>> a.extend(b)
>>> a
[1, 2, 3, 4, 5, 6, 7]
```
원래의 a 리스트에 x 리스트를 더한다

### 컬렉션 모듈

`collections` 모듈에는 추가적인 고급 자료형이 포함되어있음

**namedtuple**: 이름 붙은 필드가 있는 튜플
```python
from collections import namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(11, y=22)
```

**deque**: 양쪽 끝에서 빠르게 추가/삭제할 수 있는 자료형
```python
my_deque = deque([1, 2, 3, 4, 5])
```

**Counter**: 해시 가능한 객체의 개수를 세는 딕셔너리 서브 클래스
```python
my_counter = Counter('gallahad')
```

**OrderedDict**: 순서를 유지하는 딕셔너리
```python
my_ordered_dict = OrderedDict([('one', 1), ('two', 2), ('three', 3)])
```

**defaultdict**: 기본 값을 제공하는 딕셔너리
```python
my_defaultdict = defaultdict(int) my_defaultdict['missing'] += 1 
# missing 키가 없으면 기본 값 0으로 초기화
```

```python
D = defaultdict(list)
# 새로운 키가 추가될 때 자동으로 빈 리스트가 생성됨
```

### 타입 힌트
```python
def test(x: int) -> None:
```
콜론으로 함수의 매개변수에 자료형 지정 가능
화살표로 함수의 반환 타입을 지정 가능

## 문법
<hr>

### 함수
```python
def 함수이름(매개변수1, 매개변수2, ...):
    실행할 코드
    return 반환값
```

### 반복문

**for 루프**
```python
for 변수 in 시퀀스:
    실행할 코드
```

```python
for _ in range(9):
    print("Hello, World!")
```
여기서 변수 이름으로 `_`를 사용한 이유는, 반복 변수의 값을 사용하지 않음을 나타내기 위해서임

**while 루프**
```python
while 조건:
    실행할 코드
```

**break문**
```python
for i in range(10):
    if i == 5:
        break
    print(i)
```
반복문을 즉시 종료

**continue문**
```python
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)
```

### range
```python
range(start, stop, step)
```
- `start`: 시작 숫자 (포함)
- `stop`: 끝 숫자 (포함되지 않음)
- `step`: 증가 또는 감소 간격

### enumerate
```python
enumerate(iterable, start=0)
```
- `iterable`: 리스트, 튜플, 문자열 등 반복 가능한 객체를 의미합니다.
- `start`: 인덱스의 시작 값을 지정합니다. 기본값은 0입니다.

```python
fruits = ['apple', 'banana', 'cherry']

for index, value in enumerate(fruits):
    print(f"Index: {index}, Value: {value}")
```

### 변수 출력
```python
name = "Alice"
age = 30
print(f"Name: {name}, Age: {age}")
```
f 쓰고 중괄호 안에 변수 이름 넣으면 됨

print(i, N-i) 이렇게 하면 인자들 사이에 자동으로 공백 넣어줌

### 입력 받기
```python
user_input = input("Enter something: ")
```
input 함수는 항상 문자열을 반환하므로 숫자 쓰려면 int() 붙여줘야 함

### 문자열을 리스트로 바꾸기
```python
string = 'I became a zombie'
list(string) # 공백을 포함 한 문자씩 모두 나눔
```

### 아스키 코드 변환
```python
# 문자 'A'의 아스키 코드 값을 구하기
ascii_code = ord('A')
print(ascii_code)  # 65 출력
```

```python
# 아스키 코드 값이 65인 문자 'A'를 구하기
ascii_code = 65
character = chr(ascii_code)
```


### 리스트 컴프리헨션
```python
new_list = [expression for item in iterable]
```

```python
numbers = [1, 2, 3, 4, 5]
squares = [number ** 2 for number in numbers]
print(squares)  # [1, 4, 9, 16, 25]
```

```python
# N x N 행렬 생성
matrix = [[0] * N for _ in range(N)]
```

- **expression**: 새 리스트에 넣을 표현식
- **item**: 현재 반복 중인 개체의 개별 항목
- **iterable**: 반복 가능한 객체(예: 리스트, 튜플, 문자열 등)

## 키에 대한 예외 처리
<hr>

```python
def get_first_valid(info, keys, default=''):
for key in keys:
	if key in info:
		return info[key]
return default

# 딕셔너리의 각 키에 대해 유효한 값을 찾기
illustrator_keys = ['Illustrator', 'Makeup charge', '3D Modeler', 'illustrator', 'Illustrator Live2D Designer']
debut_keys = ['Debut Stream', 'Debut', 'Debut date']
height_keys = ['Height', 'Heigh', 'height']

# 각 필드에 대한 값 설정
illustrator = get_first_valid(info, illustrator_keys, '')
debut = get_first_valid(info, debut_keys, '')
height = get_first_valid(info, height_keys, '')
unit = info.get('Unit', '')
```

## 문자열 날짜로 변환
<hr>

```python
date = "August 12, 2020"

try:
    debut_date = datetime.strptime(debut, "%B %d, %Y").strftime("%Y.%m.%d")
except ValueError:
    debut_date = '미상'

print(debut_date) # 2020.08.12
```

## pymongo
<hr>

### 세팅
```python
from pymongo import MongoClient
client = MongoClient('localhost', 27017) # mongoDB는 27017 포트를 사용한다
db = client.jungle # 'jungle'이라는 이름의 db를 만든다.
```
### 데이터 삽입
```python
# 'users'라는 collection에 {'name':'bobby','age':21}를 넣는다. db.users.insert_one({'name':'bobby','age':21})
```
### 데이터 조회
```python
all_users = list(db.users.find({})) # 데이터 모두 보기 

same_ages = list(db.users.find({'age':21})) # 특정 조건 데이터 보기

user = db.users.find_one({'name':'bobby'},{'_id':False})
# 특정 결과 값 뽑아 보기 (그 중 id는 빼고 보기)
```
### 데이터 수정
```python
db.people.update_many(찾을조건,{ '$set': 어떻게바꿀지 })
# people이라는 collection에서 특정 조건에 해당하는 모든 문서들의 데이터를 수정
# '$set'은 MongoDB의 업데이트 연산자로, 지정된 필드의 값을 새로운 값으로 변경한다.

db.users.update_one({'name':'bobby'},{'$set':{'age':19}})
# users 컬렉션에서 name 필드가 bobby인 문서를 찾아서 age 필드를 19로 설정한다

db.users.delete_one({'name':'bobby'})
# 삭제하기
``` 
### list 붙이는 이유
```python
movies = list(db.movies.find({'open_month':target_month}))

# pymongo의 find 메서드는 Cursor 객체를 반환한다.
# Cursor는 데이터베이스에서 실제로 데이터를 가져오기 전까지는 데이터가 없다.

# list 함수를 사용하여 Cursor를 리스트로 변환하면, 데이터가 메모리로 로드된다.
# 이렇게 하면 데이터베이스로의 추가적인 요청 없이도 데이터를 사용할 수 있다.
```
### 제외할 필드 설정
```python
result = list(db.articles.find({}, {'_id': 0}))
```
MongoDB에서는 조회하는 동안 특정 필드를 포함/제외 할 수 있다. 이를 프로젝션이라 한다.
프로젝션은 쿼리의 2번째 인자로 전달되며, 포함할 필드는 '1', 제외할 필드는 '0'을 지정한다.

### 업데이트 연산자

사용 예시 : `db.articles.update_one({'name': id}, {'$inc': {'like': 1}})`

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
