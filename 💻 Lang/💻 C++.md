


VSCode로 컴파일 및 실행 : 검색창 - run task - save and compile for c++ - execute 


---
## 개념

### namespace

```cpp
std::cout // std라는 namespace에 정의된 cout
```

어떤 정의된 객체에 대해 어디 소속인지 지정해주는 것.
자기 자신이 들어있는 namespace 안에선 굳이 명시해주지 않아도 된다.

```cpp
using header1::foo;
```

앞으로 모든 foo()는 header1이라는 namespace에서만 호출됨

```cpp
using namespace header1;
```

header1에 정의된 모든 것들을 `header1::` 없이 사용하기

>[!warning]
>`using namespace std;`는 권장되지 않음. std에 이름이 겹치는 함수를 만들게 되면 오류가 발생하기 때문. c++ 표준 라이브러리에는 수많은 함수가 존재하고 있다.

```cpp
namespace {
	int x = 20; // static int x = 10; 와 같은 효과
}
```

이름 없이 namespace 사용하면 해당 파일 안에서만 접근 가능함.
(static 키워드로 변수를 선언한 것과 같은 효과)



---
## 자료형

### 스택

```cpp
#include <stack>

std::stack<int> s;
```

| 함수          | 설명              |
| ----------- | --------------- |
| `s.push(x)` | 원소 삽입 (맨 위에 추가) |
| `s.pop()`   | 맨 위 원소 제거       |
| `s.top()`   | 맨 위 원소 접근       |
| `s.empty()` | 비었는지 여부 확인      |
| `s.size()`  | 현재 원소 수 반환      |


---
## 문법

### 스마트 포인터

|스마트 포인터|소유권|참조 가능 개수|자동 해제|복사 가능|용도|
|---|---|---|---|---|---|
|`unique_ptr`|단독|1|✅|❌|기본 사용, 명확한 소유권|
|`shared_ptr`|공유|여러 개|✅|✅|참조 공유가 필요한 구조|
|`weak_ptr`|비소유|여러 개|❌|✅|순환 참조 방지|

### 변수 초기화

RAII 철학 (Resource Acquisition Is Initialization) : 객체(생성자와 소멸자가 있는 struct, class 등0의 자원을 확보할 때 동시에 초기화한다

| 저장 영역              | 예시                    | 초기화 여부        | 비고                |
| ------------------ | --------------------- | ------------- | ----------------- |
| **로컬 변수** (자동 저장소) | 함수 내부 `int x;`        | ❌ 안 됨 (쓰레기 값) | 반드시 수동 초기화 필요     |
| **글로벌 변수**         | 파일 최상단 `int x;`       | ✅ 자동 0 초기화    | 명시 안 해도 안전        |
| **정적 변수**          | `static int x;`       | ✅ 자동 0 초기화    | 함수 안에 있어도 정적으로 취급 |
| **클래스 멤버 변수**      | `class A { int x; };` | ❌ 기본적으로 안 됨   | 생성자에서 직접 초기화해야 함  |
`std::stack` 같은 건 객체라서 생성자에 의해 자동으로 초기화된다. 그래서 로컬 변수여도 초기화됨. 기본 타입은 생성자 없으므로 로컬 변수일 때 수동 초기화해야됨.

로컬 변수는 초기화 안 해주는 이유 : 성능, 개발자의 초기화 제어권

### Template 함수

```cpp
template <typename T>
T Add<T>(T a, T b)
{
	return a + b;
}
template <typename T>
T Subtract<T>(T a, T b)
{
	return a - b;
}

float f = calculator.Add<float>(1.5f, 2.0f);
float i = calculator.Subtract<int>(3, 2);
```




