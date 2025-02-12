


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




---
## 문법




