- [[#팁|팁]]
	- [[#팁#코테|코테]]
		- [[#코테#cin, cout 더 빠르게|cin, cout 더 빠르게]]
- [[#문법|문법]]
	- [[#문법#namespace|namespace]]
	- [[#문법#변수 초기화|변수 초기화]]
		- [[#변수 초기화#초기화 리스트|초기화 리스트]]
	- [[#문법#익명 네임스페이스|익명 네임스페이스]]
- [[#자료형|자료형]]
	- [[#자료형#정수형|정수형]]
	- [[#자료형#실수형 (소수 포함 숫자)|실수형 (소수 포함 숫자)]]
	- [[#자료형#스마트 포인터|스마트 포인터]]
	- [[#자료형#배열|배열]]
		- [[#배열#std::vector|std::vector]]
		- [[#배열#c-style 배열|c-style 배열]]
		- [[#배열#std::array|std::array]]
	- [[#자료형#std::list|std::list]]
	- [[#자료형#스택|스택]]
	- [[#자료형#char|char]]
		- [[#char#UTF-8|UTF-8]]
- [[#함수|함수]]
	- [[#함수#최대값 비교|최대값 비교]]


---

## 팁

VSCode로 컴파일 및 실행 : 검색창 - run task - save and compile for c++ - execute 

### 코테
#### cin, cout 더 빠르게

```cpp
std::ios::sync_with_stdio(false);
std::cin.tie(nullptr);
```

cin, cout 쓸 때 printf와 scanf와의 연동을 끊어서 속도 더 빨라지게 하는 테크닉

#### 입력을 바로 할당

```cpp
for (int i = 0; i < n; ++i)
	cin >> v[i];
```

#### 간단한 n번  for문

```cpp
while(n--)
{
}
```



---
## 문법

### 레퍼런스

값 복사 대신 참조 복사지만 포인터보다는 간편하다.

변수에 새로운 이름을 부여한다.
처음에 반드시 초기화해야 하며,
그 이후엔 자신이 가리키는 변수를 바꿀 수 없다.

포인터는 값 자체에 접근하려면`*`를 붙여야 하지만, 레퍼런스는 그러지 않아도 된다.
레퍼런스 배열은 만들 수 없다.

```cpp
 int n = 5;
 int &r = n;
```

n을 바꿔도 r을 바꿔도 동일한 동작이다.

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

#### 익명 네임스페이스

```cpp
// some.cpp

namespace {
    void helper() {
        std::cout << "파일 내부 전용\n";
    }
}

void public_func() {
    helper();  // ✅ 내부에서만 호출 가능
}
```

.cpp 파일 안에서만 사용되는 함수 선언 가능

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

#### 초기화 리스트

```cpp
Marine::Marine() : hp(50), coord_x(0), coord_y(0), damage(5), is_dead(false) {}
```

초기화 리스트를 사용하면 선언과 동시에 초기화를 해줌.
이거 안 쓰면 선언 후에 초기화 함. 성능이 약간 더 좋아진다.


---
## 자료형

static 멤버 변수 : '클래스' 하나에 종속된다. 프로그램이 종료될 때 소멸된다.

### 정수형

|타입|크기 (보통)|값의 범위 예시 (signed 기준)|설명|
|---|---|---|---|
|`short`|2바이트|–32,768 ~ 32,767|작은 정수|
|`int`|4바이트|–2,147,483,648 ~ 2,147,483,647|일반적인 정수|
|`long`|4~8바이트|시스템에 따라 다름|큰 정수|
|`long long`|8바이트|–9,223,372,036,854,775,808 ~ ...|매우 큰 정수|
|`unsigned`|각 타입에 대응|0부터 시작하는 양의 정수만 가능|부호 없음|

### 실수형 (소수 포함 숫자)

| 타입            | 크기      | 정밀도       | 설명              |
| ------------- | ------- | --------- | --------------- |
| `float`       | 4바이트    | 약 7자리     | 단정도 부동소수점 (빠름)  |
| `double`      | 8바이트    | 약 15자리    | 일반적인 실수형 (정확도↑) |
| `long double` | 8~16바이트 | 플랫폼 따라 다름 | 정밀도 매우 높은 실수형   |

### 스마트 포인터

|스마트 포인터|소유권|참조 가능 개수|자동 해제|복사 가능|용도|
|---|---|---|---|---|---|
|`unique_ptr`|단독|1|✅|❌|기본 사용, 명확한 소유권|
|`shared_ptr`|공유|여러 개|✅|✅|참조 공유가 필요한 구조|
|`weak_ptr`|비소유|여러 개|❌|✅|순환 참조 방지|

### 배열

#### std::vector

- 동적 배열
- 조회 : O(1)
- 삽입/삭제 : O(n)

생성자 예시:
```cpp
vector<int> mpp(256, -1); // 크기 256, 각 요소 -1로 초기화
```


#### c-style 배열

- 고정 크기, 크기 변경 불가
- 범위 초과 시 위험 (검사 없음)

```cpp
int arr[5] = {};
```
→ 전부 0으로 초기화

```cpp
std::fill(table, table + 256, -1);
```
→ 모든 원소를 -1로 초기화
#### std::array

- 고정 크기 STL 배열
- 내부적으로 C-style 배열을 감싸는 구조
- `.size()`, `.at()`, `.begin()` 등 멤버 함수 제공
- 복사/대입 가능, STL 호환

### std::list

- 이중 연결 리스트
- 접근 : O(n), `l[i]` 직접 접근 불가능
- 삽입/삭제 : O(1)

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

### char

- char는 1바이트(8비트), 0~255 (부호 없을 경우)  
- ASCII : 0~127에 매핑된 문자 집합  
- 0~127 : 기본적으로 제어 문자, 공백, 숫자, 대소문자 영어 알파벳, 특수문자로 표현됨  
- 128~255 : 플랫폼 따라 들어있는거 다름

char 종류

|타입|부호 여부|범위|
|---|---|---|
|`char`|**플랫폼에 따라 다름**|`-128 ~ 127` 또는 `0 ~ 255`|
|`signed char`|항상 부호 있음|`-128 ~ 127`|
|`unsigned char`|항상 부호 없음|`0 ~ 255`|
#### UTF-8

- 유니코드 문자를 바이트로 저장하는 방식 중 하나
- 1~4바이트 가변 길이 인코딩
- string은 char 배열이라 유니코드 못 다룸

|문자 종류|바이트 수 (UTF-8 기준)|
|---|---|
|ASCII 문자|1바이트 (`'A'`, `'1'` 등)|
|유럽 문자|2바이트 (`é`, `ñ` 등)|
|한글, 한자|3바이트 (`가`, `中` 등)|
|이모지|4바이트 (`😁`, `🔥` 등)|

### string

관련 메서드
- clear() : 문자열 내용 모두 삭제
- append() : 문자열을 다른 문자열에 추가
- substr() : 문자열의 일부분을 추출
- find() : 문자열 내에서 특정 문자열 찾기
- replace() : 문자열의 일부분을 다른 문자열로 대체
- compare() : 두 문자열을 비교
- begin() / end() : 문자열의 시작과 끝 반복자 반환
- erase() : 문자열의 일부분 제거
- insert() : 문자열의 특정 위치에 다른 문자열 삽입
- swap() : 두 문자열의 내용 교환

#### stoi / stol / stoll

- 모두 `<string>` 헤더에 정의돼있음

```cpp
// stoi 함수
int stoi(const std::string& str, std::size_t* pos = 0, int base = 10);
int stoi(const std::wstring& str, std::size_t* pos = 0, int base = 10);
// stol 함수
long stol(const std::string& str, std::size_t* pos = 0, int base = 10);
long stol(const std::wstring& str, std::size_t* pos = 0, int base = 10);
// stoll 함수
long long stoll(const std::string& str, std::size_t* pos = 0, int base = 10);
long long stoll(const std::wstring& str, std::size_t* pos = 0, int base = 10);
```

- stoi는 int형, stol은 long형, stoll은 long long형으로 바꿔줌
- base는 대상이 되는 진법
- pos는 변환하다가 멈춘 곳

관련 메서드
- stoul, stoull : 문자열을 부호 없는 정수로 바꿔줌
- stof, stod, stold : 문자열을 부동 소수점 값으로 바꿔줌
- to_string : 정수나 부동 소수점 값을 문자열로 바꿔줌



---
## 함수

### 최대값 비교

```cpp
#include <algorithm>

int a = 5, b = 10;
int maximum = std::max(a, b);
```

기본

```cpp
int m = std::max({a, b, c});
```

여러 값 비교

```cpp
#include <algorithm>
#include <vector>

std::vector<int> v = {3, 8, 1, 6};
int maxVal = *std::max_element(v.begin(), v.end());  // 8
```

`std::max_element` 사용하여 여러 값 비교

### 안전한 형변환

```cpp
static_cast<int>(q.size())
```

`int(q.size())`처럼 C 스타일 형변환도 가능하지만, `static_cast`는 **타입 오류를 컴파일 시점에 잡아준다**는 점에서 더 안전하다.


### push_back과 emplace_back 차이

- `emplace_back()`은 **객체를 백터 내부에서 직접 생성**하는 함수다.
- `push_back()`은 **이미 만들어진 객체를 복사 또는 이동**해서 벡터에 넣는다.

따라서 단순한 자료형(예: `int`, `double`)에는 **차이 없다.**  
하지만 복잡한 객체일 경우, **불필요한 복사/이동을 피하기 위해 `emplace_back()`이 더 효율적**이다.

### 메모리 미리 할당 :: reserve()

```cpp
vector<T>::reserve(size_t n)
```

최소한 n개의 요소를 저장할 수 있는 메모리를 미리 할당합니다.
실제 요소 개수는 증가하지 않음 (size()는 그대로).
중간에 reallocation 없이 더 빠르게 .push_back()을 할 수 있음.

vector, string 등에서만 작동.