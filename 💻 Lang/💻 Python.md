- [[#백준 관련|백준 관련]]
	- [[#백준 관련#입력받을 때|입력받을 때]]
	- [[#백준 관련#최대 재귀 깊이 설정|최대 재귀 깊이 설정]]
- [[#개념|개념]]
	- [[#개념#GPT 답변 모음|GPT 답변 모음]]
	- [[#개념#`__name__`|`__name__`]]
	- [[#개념#싱글톤 패턴|싱글톤 패턴]]
	- [[#개념#변수|변수]]
	- [[#개념#모듈|모듈]]
	- [[#개념#self의 의미|self의 의미]]
	- [[#개념#특수 메서드|특수 메서드]]
- [[#자료형|자료형]]
	- [[#자료형#기본 자료형|기본 자료형]]
	- [[#자료형#컬렉션 자료형|컬렉션 자료형]]
		- [[#컬렉션 자료형#list 조작|list 조작]]
		- [[#컬렉션 자료형#슬라이스식|슬라이스식]]
	- [[#자료형#컬렉션 모듈|컬렉션 모듈]]
	- [[#자료형#스택|스택]]
	- [[#자료형#큐|큐]]
	- [[#자료형#자료형 변환|자료형 변환]]
	- [[#자료형#타입 힌트|타입 힌트]]
- [[#문법|문법]]
	- [[#문법#조건문|조건문]]
	- [[#문법#함수|함수]]
	- [[#문법#반복문|반복문]]
	- [[#문법#조건 연산자|조건 연산자]]
	- [[#문법#range|range]]
	- [[#문법#enumerate|enumerate]]
	- [[#문법#print|print]]
	- [[#문법#두 변수 값 교환|두 변수 값 교환]]
	- [[#문법#입력 받기|입력 받기]]
		- [[#입력 받기#.readline()|.readline()]]
		- [[#입력 받기#.strip()|.strip()]]
		- [[#입력 받기#map(function, iterable)|map(function, iterable)]]
	- [[#문법#문자열을 리스트로 바꾸기|문자열을 리스트로 바꾸기]]
	- [[#문법#역순으로 정렬한 리스트 생성|역순으로 정렬한 리스트 생성]]
	- [[#문법#접두사, 접미사 확인|접두사, 접미사 확인]]
	- [[#문법#아스키 코드 변환|아스키 코드 변환]]
	- [[#문법#리스트 컴프리헨션|리스트 컴프리헨션]]
	- [[#문법#return|return]]
	- [[#문법#False로 취급되는 값들|False로 취급되는 값들]]
- [[#구현|구현]]
	- [[#구현#키에 대한 예외 처리|키에 대한 예외 처리]]
	- [[#구현#문자열 날짜로 변환|문자열 날짜로 변환]]
- [[#PEP 20|PEP 20]]
- [[#PEP 8|PEP 8]]
	- [[#PEP 8#이름 짓기 관습|이름 짓기 관습]]
	- [[#PEP 8#줄바꿈은 이진 연산자의 앞|줄바꿈은 이진 연산자의 앞]]
	- [[#PEP 8#연산자 공백|연산자 공백]]
	- [[#PEP 8#주석|주석]]
	- [[#PEP 8#프로그래밍 권장 사항|프로그래밍 권장 사항]]
- [[#pymongo|pymongo]]
	- [[#pymongo#list 붙이는 이유|list 붙이는 이유]]
	- [[#pymongo#제외할 필드 설정|제외할 필드 설정]]
	- [[#pymongo#업데이트 연산자|업데이트 연산자]]
- [[#Flask|Flask]]
	- [[#Flask#flash alert|flash alert]]
- [[#버그|버그]]
	- [[#버그#리스트 컴프리헨션 안 쓰고 list()|리스트 컴프리헨션 안 쓰고 list()]]
	- [[#버그#.sort()는 NoneType 반환|.sort()는 NoneType 반환]]



## 백준 관련
<hr>

### 입력받을 때

**메서드 이름 줄이기**
```python
input = sys.stdin.readline
input().strip().split()
```

**공백으로 구분된 자료 받기**
```python
import sys  
a = list(map(int, sys.stdin.readline().strip()))
# a = [1, 2, 3, 4, 5]
```

**공백으로 구분된 자료를 변수에 바로 할당**
```python
m, n, l = map(int, input().split())
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

**공백으로 구분된 문자열을 세트로 저장하는 법**
```python
S_find = set(input().split())
```

### 최대 재귀 깊이 설정
```python
import sys  
sys.setrecursionlimit(10**5) # 10^5 까지 늘림.
```
DFS, BFS 문제의 경우 재귀 허용 깊이를 수동으로 늘려주는 코드를,코드 상단에 적어줘야 한다. (PyPy에서는 안됨)

## 라이브러리
<hr>

###  annotations

> type hinting을 도와주는 라이브러리. 부정확해도 실행상 어떤 오류도 발생시키지 않는다.
> 

**Any**: 모든 타입
```python
from typing import Any

def func(x: Any) -> Any:
    return x
```

**Union**: 여러 타입 중 하나
```python
def func(x: Union[int, str]) -> str:
```

**Optional**: 특정 값이 주어지거나 'None'
```python
def func(x: Optional[int] = None) -> Optional[int]:
```

**List**: 리스트 타입 명시
**Dict**: 딕셔너리 타입 명시
**Tuple**: 튜플 타입 명시
```python
def func(xs: List[int]) -> List[int]:
def func(d: Dict[str, int]) -> Dict[str, int]:
def func(t: Tuple[int, str]) -> Tuple[int, str]:
```

**TypeVar**: 제네릭 타입 정의 가능해짐
```python
from typing import TypeVar, List

T = TypeVar('T')

def func(x: T) -> List[T]:
    return [x]
```

**Generic**: 클래스와 함께 사용할 수 있는 제네릭 타입 정의 가능해짐
```python
from typing import TypeVar, Generic

T = TypeVar('T')

class Box(Generic[T]):
    def __init__(self, content: T):
        self.content = content

    def get_content(self) -> T:
        return self.content

box = Box(123)
print(box.get_content())  # 출력: 123
```

## 자신의 클래스로 초기화
```python
from __future__ import annotations

class Node:
def __init__(self, key: Node = None)
```
이 import 문은 무조건 파일 맨 위에 선언되어야 함

## 개념
<hr>

### GPT 답변 모음
가급적 사용 지양. 썼더라도 재정리 고려.

[[from __future__ import annotations]]
[[from typing import Any, Type]]


## 제네릭 프로그래밍

하나의 자료형에만 의존하지 않고 공통 속성을 갖는 여러 자료형에 대해 동일하게 작동하는 알고리즘을 작성하는 기법 일반을 의미. 파이썬은 애초에 동적 타이핑 언어이기 때문에 제네릭을 따로 구현할 필요가 없다.


### 동적 프로그래밍

복잡한 문제를 더 작은 하위 문제로 나누어 해결하는 알고리즘 설계 기법


### `__name__` 

- 스크립트 프로그램이 직접 실행될 때 변수 `__name__`은 `'__main__'`
- 스크립트 프로그램이 임포트될 때 변수 `__name__`은 원래의 모듈 이름

**if name == "main"** 의미
: 해당 모듈이 임포트된 경우가 아니라 인터프리터에서 직접 실행한 경우에만 실행해라.


### 싱글톤 패턴

객체 지향 프로그래밍에서 특정 클래스의 인스턴스가 오직 하나만 존재하도록 보장하기 위해 사용되는 디자인 패턴

**사용하는 이유**

1. **리소스 절약**:    
    - 특정 리소스의 인스턴스를 하나만 유지하여 메모리 사용을 최소화합니다.
    - 예를 들어, 데이터베이스 연결 객체를 싱글톤으로 만들어 하나의 연결을 재사용하면 리소스를 절약할 수 있습니다.

2. **상호 배제**:    
    - 특정 작업이 동시에 여러 번 실행되는 것을 방지하기 위해 사용됩니다.
    - 예를 들어, 파일에 로그를 기록하는 로거 객체를 싱글톤으로 만들어, 여러 스레드에서 동시에 접근해도 하나의 로거 인스턴스를 사용하게 할 수 있습니다.

3. **글로벌 접근**:    
    - 애플리케이션 전역에서 동일한 객체에 접근해야 할 때 사용됩니다.
    - 예를 들어, 애플리케이션 설정을 싱글톤 객체로 관리하면 어디서나 설정 값에 접근하고 수정할 수 있습니다.

**구현 예시**

1. `__new__` 메서드를 사용
2.  데코레이터를 사용
3. None, True, False와 같은 내장 객체


### 변수

파이썬에선 데이터, 함수, 클래스, 모듈, 패키지 등을 모두 객체로 취급함. 객체는 자료형을 가지며 메모리(저장 공간)를 차지함. 파이썬의 이런 특징 때문에 파이썬의 변수는 값을 갖지 않는다는 특징이 있음.

예를 들어 x = 17은 x가 17이라는 값을 갖고 있다고 말할 수 없음. 보통 프로그래밍 언어에서 변수란 값을 저장하는 상자와 같다고 비유하는데 파이썬에서는 이 비유가 맞지 않음.

> [!note]
> - 변수는 객체를 참조하는 객체에 연결된 이름에 불과함
> - 모든 객체는 메모리를 차지하고, 자료형과 식별 번호(identity)를 가짐

즉, n=17은 **변수에 값을 저장하는게 아니라** int형 **객체 17에 이름이 부여되는 것**

변수 쓸 때 자료형 선언 안 해도 값 대입만 하면 바로 쓸 수 있는 이유가 이거 때문.


### 모듈

- 모듈 : 하나의 스크립트 프로그램. 확장자(.py)를 포함하지 않는 파일의 이름 자체를 모듈 이름으로 사용함.
- 스크립트 프로그램이 직접 실행될 때 변수 `__name__`은 `'__main__'`
- 스크립트 프로그램이 임포트될 때 변수 `__name__`은 원래의 모듈 이름
- 파이썬은 모든 것을 객체로 다루므로 모듈도 당연히 객체

### self의 의미

- 클래스 메서드를 정의할 때, 첫 번째 매개변수로 항상 인스턴스 자신을 참조하는 `self`를 사용합니다.
- `self`를 사용하여 인스턴스 변수와 다른 메서드에 접근하고 수정할 수 있습니다.
- 파이썬은 인스턴스 메서드를 호출할 때 자동으로 인스턴스를 첫 번째 인수로 전달합니다. 이를 통해 메서드 내부에서 인스턴스 변수와 메서드를 사용할 수 있습니다.

```python
class Human:
    def __init__(self):
        self.nutrition = 0  # 인스턴스 변수 초기화

    def eat(self):
        nutrition += 1  # 이 코드는 오류가 발생합니다

# 객체 생성
human = Human()

# 메서드 호출
human.eat()
print(human.nutrition)
```

이 코드는 `nutrition` 변수가 정의되지 않았다는 오류가 발생합니다. `self.nutrition`을 사용해야 인스턴스 변수를 참조할 수 있습니다.

### 특수 메서드

**역할**
1. 객체 초기화 및 소멸: 객체가 생성, 소멸될 때 자동 호출
2. 객체 표현: 객체의 문자열 표현을 정의
3. 컨테이너 타입 동작: 객체를 리스트, 딕셔너리, 집합 등과 같은 컨테이너 타입처럼 동작하게 함
4. 연산자 오버로딩: 연산자를 사용자 정의 객체에 대해 사용할 수 있도록 정의
5. 속성 접근 및 관리: 객체의 속성 접근 방식을 제어

**1, 객체 초기화 및 소멸**
- `__init__(self, ...)`: 객체가 생성될 때 호출
```python
class MyClass:
    def __init__(self, value):
        self.value = value

obj = MyClass(10)  # MyClass의 인스턴스가 생성될 때 __init__ 메서드가 자동으로 호출됩니다.
print(obj.value)  # 출력: 10
```
- `__del__(self)`: 객체가 소멸될 때 호출


**2, 객체 표현**
- `__str__(self)`: str() 함수나 print() 함수가 호출될 때 실행. 객체의 비공식적인 문자열 표현을 반환.
- `__repr__(self)`: `repr()` 함수나 대화형 인터프리터에서 객체를 출력할 때 실행. 객체의 공식적인 문자열 표현을 반환.

**3, 컨테이너 타입 동작**
- `__len__(self)`: len() 함수가 호출될 때 실행
- `__getitem__(self, key)`: 객체의 특정 요소에 접근할 때 호출
- `__setitem__(self, key, value)`: 객체의 특정 요소에 값 설정할 때 호출
- `__delitem__(self, key)`: 객체의 특정 요소를 삭제할 때 호출
- `__iter__(self)`: 객체를 반복(iteration)할 때 호출
```python
class MyIterable:
    def __iter__(self):
        self.current = 0
        return self

    def __next__(self):
        if self.current < 5:
            self.current += 1
            return self.current
        else:
            raise StopIteration

it = MyIterable()
for value in it:  # for 루프가 시작될 때 __iter__ 메서드가 자동으로 호출됩니다.
    print(value)  # 출력: 1, 2, 3, 4, 5
```
- `__next__(self)`: 이터레이터의 다음 요소를 반환할 때 호출
```python
class MyIterable:
    def __iter__(self):
        self.current = 0
        return self

    def __next__(self):
        if self.current < 5:
            self.current += 1
            return self.current
        else:
            raise StopIteration

it = iter(MyIterable())  # __iter__ 메서드가 호출됩니다.
print(next(it))  # __next__ 메서드가 호출되어 1을 반환합니다.
print(next(it))  # __next__ 메서드가 호출되어 2을 반환합니다.
```

**4, 연산자 오버로딩**
- `__add__(self, other)`: + 가 호출될 때 실행
- `__sub__(self, other)`: - 가 호출될 때 실행
- `__mul__(self, other)`: * 가 호출될 때 실행
- `__truediv__(self, other)`: / 가 호출될 때 실행
- `__floordiv__(self, other)`: // 가 호출될 때 실행
- `__mod__(self, other)`: % 가 호출될 때 실행
- `__pow__(self, other)`: ** 가 호출될 때 실행
- `__eq__(self, other)`: == 가 호출될 때 실행
- `__lt__(self, other)`: < 가 호출될 때 실행

**5, 속성 접근 및 관리**
- `__getattr__(self, name)`: 객체에 없는 속성에 접근하려 할 때 호출
- `__setattr__(self, name, value)`: 객체의 속성에 값을 설정할 때 호출
- `__delattr__(self, name)`: 객체의 속성을 삭제할 때 호출.
- `__getattribute__(self, name)`: 객체의 속성에 접근할 때 항상 호출


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

```python
tree[root] = left, right
```
이렇게 입력하면 tree 딕셔너리에서 root 키는 튜플 (left, right)

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

```python
def third_val(e):
	return(e[2])  

Edges.sort(key = third_val)
```
이중 리스트를 세번째 요소에 대해 정렬하는 법

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

**del**: 특정 범위 요소 제거
```python
del my_list[2:5]
```
인덱스 2부터 4까지의 요소 제거 

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

#### 슬라이스식

| 패턴      | 설명                                | 실행 예    | 실행 결과                        |
| ------- | --------------------------------- | ------- | ---------------------------- |
| s[:]    | 리스트 s의 원소를 모두 출력합니다.              | s[:]    | [11, 22, 33, 44, 55, 66, 77] |
| s[:n]   | 리스트 s의 원소 중 맨 앞부터 n개까지 출력합니다.     | s[:3]   | [11, 22, 33]                 |
| s[i:]   | 리스트 s의 원소 중 s[i]부터 맨 끝까지 출력합니다.   | s[3:]   | [44, 55, 66, 77]             |
| s[-n:]  | 리스트 s의 원소 중 -n부터 맨 끝까지 출력합니다.     | s[-3:]  | [55, 66, 77]                 |
| s[:k]   | 리스트 s의 원소 중 맨 앞부터 k개씩 건너뛰며 출력합니다. | s[::2]  | [11, 33, 55, 77]             |
| s[::-1] | 리스트 s의 원소 중 맨 끝부터 전부 출력합니다.       | s[::-1] | [77, 66, 55, 44, 33, 22, 11] |


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

#### 큐 연산

- append(): 오른쪽에서 데이터를 삽입
- appendleft(): 왼쪽에서 데이터를 삽입
- pop(): 오른쪽에서 데이터 삭제
- popleft(): 왼쪽에서 데이터 삭제

### 스택
1. 리스트 : 스택을 구현하는 가장 기본적인 방법
```python
stack = []
stack.append(1)
stack.append(2)
print(stack.pop()) # 출력: 2
```

2. collections.deque : 양쪽 끝에서 요소 추가, 제거 가능한 이중 연결 리스트
```python
from collections import deque
stack = deque()
```

3. queue.LifoQueue : LIFO(Last In, First Out) 구조의 스레드 안전한 큐
```python
from queue import LifoQueue
stack = LifoQueue()
stack.put(1)
stack.put(2)
print(stack.get()) # 출력: 2
```

### 큐
1. 리스트 : 큐를 구현할 수는 있지만, 앞 부분 요소 제거가 비효율적
```python
queue = []
queue.append(1)
queue.append(2)
print(queue.pop(0)) # 출력: 1
```

2. collections.deque : 양쪽 끝에서 요소 추가, 제거 가능한 이중 연결 리스트
```python
from collections import deque
queue = deque()
queue.append(1)
queue.append(2)
print(queue.popleft()) # 출력: 1
```

3. queue.Queue : FIFO(First In, First Out) 구조의 스레드 안전한 큐
```python
from queue import Queue
queue = Queue()
queue.put(1)
queue.put(2)
print(queue.get()) # 출력: 1
```


### 자료형 변환

int(문자열, 진수): n진수를 나타내는 문자열을 각각 정수로 변환
```python
>>> int('17') # 10진수 문자열을 10진수 정수형으로 변환(기본)
17
>>> int('0b110', 2) # 2진수 문자열을 10진수 정수형으로 변환
6
>>> int('0o75', 8) # 8진수 문자열을 10진수 정수형으로 변환
61
```

### 타입 힌트
```python
def test(x: int) -> None:
```
콜론 : 함수의 매개변수에 자료형 지정
화살표 : 함수의 반환 타입을 지정

## 문법
<hr>

### 조건문
```python
if a < b: min2 = a
if a < b: min2 = a; max2 = b;
```
단순문이 2개 이상이면 각각의 단순문을 세미콜론으로 구분할 수 있다.

### 함수
```python
def 함수이름(매개변수1, 매개변수2, ...):
    실행할 코드
    return 반환값
```

```python
def __init__(self, value: int = 1, next: Node = None):
```
함수 값 초기화 값 지정 (값 안 넣으면 이걸로 자동 초기화)

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

### try-except
```python
try:
    # 실행할 코드
    pass
except:
    # 예외가 발생했을 때 실행할 코드
    pass
```
코드 실행 중에 에러 발생하면 except 아래를 실행한다

**예시**
```python
arr = []  # 정수를 저장할 리스트

while True:
    try:
        x = int(input())  # 사용자로부터 입력을 받아 정수로 변환
        arr.append(x)     # 변환된 정수를 리스트에 추가
    except:
        break  # 예외가 발생하면 루프를 종료
```

**구체적인 예외 처리**
```python
try:
    # 실행할 코드
    pass
except ValueError:
    # ValueError가 발생했을 때 실행할 코드
    pass
except TypeError:
    # TypeError가 발생했을 때 실행할 코드
    pass
except Exception as e:
    # 그 외의 모든 예외를 처리할 때 실행할 코드
    # 예외 객체를 e로 받아서 사용할 수 있음
    pass
```

**else 블럭**
```python
try:
    # 실행할 코드
    pass
except:
    # 예외가 발생했을 때 실행할 코드
    pass
else:
    # 예외가 발생하지 않았을 때 실행할 코드
    pass
```

**finally 블럭**
```python
try:
    # 실행할 코드
    pass
except:
    # 예외가 발생했을 때 실행할 코드
    pass
else:
    # 예외가 발생하지 않았을 때 실행할 코드
    pass
finally:
    # 항상 실행되는 코드
    pass
```

### 조건 연산자
```python
value_if_true if condition else value_if_false
```

```python
status = "성인" if age >= 18 else "미성년자"
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
인덱스와 원소를 짝지어 튜플로 꺼낸다

- `iterable`: 리스트, 튜플, 문자열 등 반복 가능한 객체
- `start`: 인덱스의 시작 값 지정. 기본값은 0.

```python
fruits = ['apple', 'banana', 'cherry']

for index, value in enumerate(fruits):
    print(f"Index: {index}, Value: {value}")
```

### print

```python
name = "Alice"
age = 30
print(f"Name: {name}, Age: {age}")
```
f 쓰고 중괄호 안에 변수 이름 넣으면 변수가 출력됨

print(i, N-i) 이렇게 하면 인자들 사이에 자동으로 공백 넣어줌

**end 매개변수**
```python
print("Hello", end='') 
print("World")
# HelloWorld
```
- 기본값: `\n` (newline, 개행 문자)\
- 사용법: `print` 함수의 출력이 끝난 후에 추가할 문자열을 지정

### join
```python
separator.join(iterable)
```
문자열로 결합할 시퀀스(리스트, 튜플 등)의 각 요소 사이에 seperator를 삽입해 반환

### 두 변수 값 교환
```python
a, b = b, a
```
두 값을 압축한 튜플이 생성된 후에 각각 a, b에 대입됨

### 입력 받기
```python
user_input = input("Enter something: ")
```
input 함수는 항상 문자열을 반환하므로 숫자 쓰려면 int() 붙여줘야 함

```python
list(map(int, sys.stdin.readline().strip()))
```
공백으로 구분된 여러 문자를 list에 넣기

#### .readline()
```pyhon
line = sys.stdin.readline()
```
한 줄 읽음. 끝에 개행 문자 포함됨.

sys.stdin : 사용자 입력을 받을 때 쓰는 객체

#### .strip()
```python
line = "  123 456  \n"
stripped_line = line.strip() # "123 456"
```
문자열의 양쪽 끝 공백 문자 제거

공백 문자 : 개행 문자`\n`, 공백, 탭`\t`

#### map(function, iterable)
```python
mapped = map(int, numbers_list)  # [123, 456]
```
첫 번째 인수로 주어진 함수를
두 번째 인수로 주어진 이터러블(반복 가능한 객체)의 모든 요소에 적용하여 결과 반환.
map 객체는 게으른 평가를 함.

>[!memo] map 객체란?
> **순회 가능**한 객체의 **각 원소**에 **지정한 함수**를 각각 **적용**하는 객체

>[!memo] 게으른 평가란?
>결과를 즉시 생성하지 않고, 필요할 때 값을 생성
>메모리 사용량이 적고, 당장 계산 결과를 기다리지 않아도 됨


### 문자열을 리스트로 바꾸기
```python
string = 'I became a zombie'
list(string) # 공백을 포함 한 문자씩 모두 나눔
```

### 역순으로 정렬한 리스트 생성

- reversed(x) : x의 원소를 역순으로 정렬하는 이터러블 객체. '역순으로 꺼낼 거에요~'라는 명령들일 뿐임. 이렇게는 역순으로 정렬 안됨.
- list(reversed(x)) : 이렇게 해야 역순으로 정렬된 리스트 얻음
- x.reverse() : 이렇게 하면 리스트가 역순으로 정렬됨

### 접두사, 접미사 확인
```python
string = "hello world"
prefix = "hello"
suffix = "world"

# 접두사 확인
if string.startswith(prefix):
    print("접두사가 일치합니다.")
if string.endswith(suffix):
    print("접미사가 일치합니다.")
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

### return
- 그냥 return만 쓰면 return None 과 같다

### False로 취급되는 값들
```python
None is False
0 is False
[] is False
() is False
 is False
{} is False
set() is False
False is False
```


## 구현
<hr>

### 키에 대한 예외 처리
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

### 문자열 날짜로 변환
```python
date = "August 12, 2020"

try:
    debut_date = datetime.strptime(debut, "%B %d, %Y").strftime("%Y.%m.%d")
except ValueError:
    debut_date = '미상'

print(debut_date) # 2020.08.12
```


## PEP 20
<hr>

[출처](https://icedhotchoco.tistory.com/entry/PEP-20)

**Beautiful is better than ugly (아름다운 것이 못생긴 것보다 낫다)**  
- 작성된 코드를 읽을 때 예쁘다고 느끼게 작성하자

**Explicit is better than implicit (명시적인 것이 암시적인 것보다 낫다)**
- 표현을 명확히하지 않으면 쉽게 이해하지 못할 수 있다

**Simple is better than complex (간단한 것이 복합적인 것보다 낫다)**
- 간단하게 작성해야 테스트와 수정이 쉽다

**Flat is better than nested (수평적인 것이 중첩된 것보다 낫다)**
- loop 중첩이 늘어날수록 코드를 알아보기 어렵다

**Sparse is better than dense (풀어놓는 것이 밀집된 것보다 낫다)**
- 짧게 쓰는 것을 목적으로 한 줄에 많은 동작을 하게끔 무리한 코딩은 좋지 않다

**Special cases aren't special enough to break the rules (특별한 경우도 규칙을 어겨야 할 정도로 특별하지는 않다)**
- 규칙은 지키도록 노력하고, 지키자. 규칙을 지키지 않는다는 것은 좋은 관행을 포기하는 것이다

**Although practicality beats purity (하지만 실용성은 순수성보다 우선이다)**
- 이것은 위의 것과 상충된다. 규칙을 지키지 않지만 더 좋은 선택지가 있다면, 그 좋은 것을 선택하자

**Errors should never pass silently (오류는 절대 조용히 넘어가선 안 된다)**
- 특히 예외처리를 하는 try - except 구문에서, 에러를 꼭 짚고 넘어가자

**Unless Explicitly silenced (명시적으로 침묵하지 않는 한)**
- 오류가 발생해도 프로그램이 중단되지 않도록 원하는 경우에는 명시적으로 예외를 작성하자
- 실용성은 순수성보다 우선임을 기억하자

**There should be one-- and preferably only one --obvious way to do it. (그것을 할 수 있는 분명한 하나의 -- 유일하면 더 좋고 -- 방법이 존재할 것이다)**
- 해결책은 반드시 존재한다. 멈추지 않고 나아가자.

**Although that way may not be obvious at first unless you're Dutch (비록 당신이 네덜란드인이 아니라면 처음에는 그 방법이 분명하지 않을 수도 있다)**  
- 명백한 해결법이 바로 떠오르지 않을 수 있지만 더 많이 생각하고 노력하자  
- 네덜란드인을 왜 언급했나 찾아보니 파이썬 창시자 귀도 반 로섬이 네덜란드인이라 그렇다고 한다..

**Now is better than never (지금 하는 것이 아예 하지 않는 것보다 낫다)**  
- 본인을 스스로 늦추지 말자. 시작하고 차근차근 발전해보자.

**Although never is often better than *right* now (아예 하지 않는 것이 지금 *바로* 보다 더 나은 경우도 종종 있지만)**  
- 계획은 구현만큼 중요하다. 너무 급하지는 말자.

**If the implementation is hard to explain, it's a bad idea (구현 결과를 설명하기 어렵다면, 그 생각은 별로다)**  
- 이해가 부족하거나 최적화되지 않은 구현일 것이다.

**If the implementation is easy to explain, it may be a good idea (구현 결과를 설명하기 쉽다면, 그 생각은 좋을지도 모른다)**  
- 심플한 조각들로 구성된 최적화된 구현이며 이해를 잘 하고 있다는 뜻이다.

**Namespaces are one honking great idea -- let's do more of those! (네임스페이스는 완전 좋은 생각이다 -- 더 활용하라!)**  
- 네임스페이스는 파이썬의 핵심 포인트이다.


## PEP 8
<hr>

**최대 줄 길이** : 모든 줄은 최대 79자로 제한

### 이름 짓기 관습

- b (single lowercase letter) : 단일 소문자  
- B (single uppercase letter) : 단일 대문자  
- lowercase : 소문자  
- lower_case_with_underscores : 밑줄을 포함하는 소문자 (snake case)  
- UPPERCASE : 대문자  
- UPPER_CASE_WITH_UNDERSCORES : 밑줄을 포함하는 대문자  
- CapitalizedWords : 각 단어의 첫 글자는 대문자 (CapWords)  
- camelCase : 첫 글자는 소문자, 그 뒤 각 단어 첫 글자는 대문자  
- Capitalized_Words_With_Underscores : 이렇게는 쓰지 말자 (**ugly**)  
  
'l' (소문자 엘), 'O' (대문자 오), 'I' (대문자 아이)는 단일 문자 변수 이름으로 절대 쓰지 않아야한다.  
  
**클래스** 이름은 CapWord 표기법을 사용한다  
**함수, 메소드, 변수** 이름은 snake_case를 사용한다  
**상수**는 보통 모듈 수준에서 정의되며 밑줄을 포함하는 대문자를 사용한다

### 줄바꿈은 이진 연산자의 앞
```python
# Wrong
# 연산자와 피연산자가 멀리 떨어져있다
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)
 
# Correct:
# 연산자와 피연산자를 매치시키기 쉽다
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

### 연산자 공백
다음 연산자들은 항상 단일 공백으로 둘러싸야한다
1. 대입이나 복합대입연산자 (=, +=, -= 등)
2. 비교 연산자 (`==`, <, <=, >, >=, is, in 등)
3. 논리 연산자 (and, or, not)

우선 순위가 다른 연산자들을 사용하는 경우 
**우선 순위가 낮은 연산자 주위에 공백**을 사용해야한다.
**연산자의 양쪽에는 같은 개수의 공백**을 사용해야한다.

```python
# Wrong
i=i+1
total +=1
x = x * 2 - 1
result = x * x + y * y
c = (a + b) * (a - b)
 
# Correct
i = i + 1
total += 1
x = x*2 - 1
result = x*x + y*y
c = (a+b) * (a-b)
```

**키워드 인자** 혹은 **디폴트 파라미터** 값을 나타낼 때는 = 앞뒤로 공백을 사용하지 않아야한다.
```python
# Wrong
def complex(real, imag = 0.0):
    return magic(r = real, i = imag)
 
# Correct
def complex(real, imag=0.0):
    return magic(r=real, i=imag)
```

### 주석
- 인라인 코멘트(코드와 같은 줄에 있는 코멘트)는 드물게 사용해야한다. 사용한다면 2개 이상 공백으로 코드와 분리되며 **#과 하나의 공백으로 시작**해야한다.  
- 명확한 코드에 대한 인라인 주석은 산만하게 만든다.
```python
# Wrong
x = x + 1   # Increment x
 
# Useful
# 어떤 목적인지에 대한 주석
x = x + 1   # Compensate for border
```

### 프로그래밍 권장 사항

None과 같은 singletons에 대한 비교는 `==`를 사용하지 않고 **is, is not**
```python
print(foo == None) # True
print(foo is None) # False
```

**not ... is 보다 is not 연산자를 사용**해야한다.
```python
# Wrong
if not foo is None:
 
# Correct
if foo is not None:
```

식별자에 직접 람다 표현을 대입하는 대신 **항상 def 구문을 사용**해야한다.
```python
# Wrong
f = lambda x: x * 2
 
# Correct
def f(x):
  return x * 2
```

예외처리를 할 때 **가능하다면 특정 예외를 언급**

try / except 구문의 **try 는 필요한 최소의 코드로 제한**

함수 안에서 return 문은 반환할 값이 없는 경우 **명시적으로 return None을 사용**

접두사와 접미사를 확인하기 위해 문자열 슬라이싱보단 **.startswith() 와 .endswith()를 사용**해야한다.
```python
# Wrong
if foo[:3] == 'abc':
 
# Correct
if foo.startswith('abc'):
```

불리언 값의 비교는 == 연산자를 이용해 True나 False와 비교하지 않아야한다.
```python
# No
if greeting == True:
 
# No
if greeting is True:
 
# Yes
if greeting:
```


## pymongo
<hr>
### 세팅
```python
from pymongo import MongoClient
client = MongoClient('localhost', 27017) # mongoDB는 27017 포트를 사용한다
db = client.jungle # 'jungle'이라는 이름의 db를 만든다.
```
### 데이터 관리

**데이터 삽입**
```python
# 'users'라는 collection에 {'name':'bobby','age':21}를 넣는다. db.users.insert_one({'name':'bobby','age':21})
```

**데이터 조회**
```python
all_users = list(db.users.find({})) # 데이터 모두 보기 

same_ages = list(db.users.find({'age':21})) # 특정 조건 데이터 보기

user = db.users.find_one({'name':'bobby'},{'_id':False})
# 특정 결과 값 뽑아 보기 (그 중 id는 빼고 보기)
```

**데이터 수정**
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

## Flask
<hr>

### flash alert
```python
{% with messages = get_flashed_messages() %}
    {% if messages %}
        <script>
            alert("{{messages[-1]}}")
        </script>
    {% endif %}
{% endwith %}
```

이걸 html에 추가하면  
flask에서 flash로 날린 메시지를 alert로 띄울 수 있다  
출처 : [https://journeytosth.tistory.com/45](https://journeytosth.tistory.com/45)



## 버그
<hr>

### 리스트 컴프리헨션 안 쓰고 list()
>[!bug]
>A = list(map(int, sys.stdin.readline().strip().split()) for _ in range(M))  
아니 이거 왜 출력했더니  
<map object at 0x78b44b5198a0>  
이딴 식으로 뜨는거임

```python
A = list(map(int, sys.stdin.readline().strip().split()) for _ in range(M))
```

이 코드는 map 객체의 리스트를 반환하지 않고, map 객체 자체를 요소로 갖는 리스트를 생성합니다.

```python
A = [list(map(int, sys.stdin.readline().strip().split())) for _ in range(M)]
```

올바른 방법은 위와 같습니다.

리스트 컴프리헨션을 사용하여 각 입력 줄을 정수 리스트로 변환해야 합니다.

>list(map(int, sys.stdin.readline().strip()))  
>이건 리스트 컴프리헨션 안 써도 출력하면 잘 나오던데

- list(map(int, sys.stdin.readline().strip()))는 문자열의 각 문자를 개별적으로 정수로 변환합니다.
- 여러 줄의 입력을 2차원 리스트로 처리하려면 리스트 컴프리헨션을 사용하여 각 줄을 개별적으로 처리해야 합니다.

### .sort()는 NoneType 반환

```python
gun = list(map(int, input().strip().split())).sort()
```

는 안된다.

```python
gun = list(map(int, input().strip().split()))
gun.sort()
```

로 해야 오류가 안 난다.

### Dict에 없는 key에 값을 넣으면 오류

```python
if A not in Dict: Dict[A] = []
Dict[A].append([ B,C ])
```

원래는 키 없어도 되는데 리스트는 미리 선언을 해놓던가
넣을 때마다 위 코드처럼 초기화시켜주면 됨


