
- [[#문법|문법]]
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

## 문법
### 리스트 컴프리헨션

```python
new_list = [expression for item in iterable]
```

```python
numbers = [1, 2, 3, 4, 5]
squares = [number ** 2 for number in numbers]
print(squares)  # [1, 4, 9, 16, 25]
```

- **expression**: 새 리스트에 넣을 표현식
- **item**: 현재 반복 중인 개체의 개별 항목
- **iterable**: 반복 가능한 객체(예: 리스트, 튜플, 문자열 등)

## 키에 대한 예외 처리

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
```python
date = "August 12, 2020"

try:
    debut_date = datetime.strptime(debut, "%B %d, %Y").strftime("%Y.%m.%d")
except ValueError:
    debut_date = '미상'

print(debut_date) # 2020.08.12
```

## pymongo

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
