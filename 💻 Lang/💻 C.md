- [[#VS Code 단축키|VS Code 단축키]]
- [[#gcc, gdb|gcc, gdb]]
	- [[#gcc, gdb#gcc 명령어|gcc 명령어]]
	- [[#gcc, gdb#gcc 옵션|gcc 옵션]]
	- [[#gcc, gdb#gdb 명령어|gdb 명령어]]
		- [[#gdb 명령어#코드 보기 : list|코드 보기 : list]]
		- [[#gdb 명령어#실행 중단점 설정 : break|실행 중단점 설정 : break]]
	- [[#gcc, gdb#gdb tui|gdb tui]]
		- [[#gdb tui#명령어|명령어]]
- [[#헤더 라이브러리|헤더 라이브러리]]


## VS Code 단축키

ctrl + t → excute (단축키는 커스텀 키바인딩, excute는 tasks.json에 적은거)

---
## gcc, gdb

### gcc 명령어

| 명령어                                                                 | 설명                                                                                |
| ------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| gcc 파일명(*.c)                                                        | Default로 out 파일이 생성됨(*.out 이라는 파일이 생성되며 실행 가능)                                    |
| gcc -c 파일명(*.c)                                                     | 오브젝트 파일을 생성함(*.o라는 오브젝트 파일이 생성됨)                                                  |
| gcc -c 오브젝트파일명(*.o) 파일명(*.c)  <br>gcc -o 실행파일명(*.out) 오브젝트_파일명(*.o) | 실행 파일을 만듦                                                                         |
| gcc -o 실행파일 파일명(*.c)                                                | 실행 파일을 만듦 (바로 위 2줄을 간략화한 것)  <br>(소스 파일 컴파일 > 오브젝트 파일 생성 > 실행 파일 생성 > 오브젝트 파일 삭제) |

자주 사용되는 컴파일 옵션
- -g → gdb 디버깅 정보포함
- -I → include 경로
- -Wall → all warning enable
- -O → optimization for code ( = -O1)

### gcc 옵션

| 옵션           | 설명                                                                                   |
| ------------ | ------------------------------------------------------------------------------------ |
| -Wall        | 모든 모호한 코딩에 대해 경고를 보냄                                                                 |
| -W           | 합법적이지만 모호한 코딩에 대해 경고를 보냄                                                             |
| -W -Wall     | 아주 사소한 모호성에 대해서도 경고를 보냄                                                              |
| -O2          | 최적화 레벨 2로 설정 (대부분의 최적화를 시도)                                                          |
| -E           | 전처리 과정의 결과를 화면에 보이는 옵션 (전처리 과정 중 발생한 오류 검증)                                          |
| -S           | cc1으로 전처리된 파일을 어셈블리 파일로 컴파일까지만 수행하고 멈춤 (*.s)                                         |
| -c           | as에 의한 어셈블까지만 수행하고 링크는 수행하지 않음                                                       |
| -v           | gcc가 컴파일을 어떤 식으로 수행하는지 화면에 출력                                                        |
| --save-temps | 컴파일 과정에서 생성되는 중간 파일인 전처리 파일(*.i)과 어셈블리 파일(*.s)을 지우지 않고,  <br>현재 디렉토리에 저장 (오류 분석에 사용) |

### gdb 명령어 

| 명령어                                      | 설명                                      |
| ---------------------------------------- | --------------------------------------- |
| `gdb program_name`                       | GDB 시작                                  |
| `quit`, `q`                              | **GDB 종료**                              |
| `run [args]`, `r`                        | **프로그램 실행** (args는 프로그램에 전달할 인수)        |
| `break [file:]function`                  | 특정 함수에 중단점 설정                           |
| `break [file:]line`                      | **특정 파일의 특정 줄에 중단점 설정**                 |
| `delete [breakpoint_numbers]`            | **중단점 제거 (번호를 지정하지 않으면 모든 중단점을 제거)**    |
| `info breakpoints`                       | 현재 설정된 중단점 목록 표시                        |
| `continue`                               | 프로그램 실행을 중단점이나 종료 지점까지 계속               |
| `step`                                   | 한 줄씩 코드 실행 (함수 호출 시 함수 내부로 들어감)         |
| `next`, `n`                              | **한 줄씩 코드 실행** (함수 호출 시 함수 내부로 들어가지 않음) |
| `finish`                                 | 현재 함수의 끝까지 실행하고 반환                      |
| `frame [frame_number]`                   | 현재 스택 프레임을 변경                           |
| `print <변수명>`                            | **특정 변수의 값 출력**                         |
| `info locals`                            | 현재 스택 프레임의 모든 지역 변수 출력                  |
| `watch expression`                       | 특정 표현식의 값이 변경될 때 프로그램 중단                |
| `x/nfu address`                          | 메모리 덤프 (n: 단위 개수, f: 형식, u: 단위 크기)      |
| `backtrace`                              | 현재 호출 스택 출력                             |
| `info args`                              | 현재 함수의 인수 출력                            |
| `file program_name`                      | 디버그할 파일 다시 로드                           |
| `disassemble [function]`                 | 지정된 함수나 현재 위치의 어셈블리 코드 표시               |
| `info registers`                         | 현재 레지스터의 내용 출력                          |
| `condition breakpoint_number expression` | 특정 조건이 만족될 때만 중단점 작동                    |

#### 코드 보기 : list
```
(gdb) l(list)
(gdb) list 10
(gdb) list [함수명]
(gdb) list -  // 이전 10라인을 출력한다.
(gdb) list [파일명]:[함수명]
(gdb) list [파일명]:10
```

#### 실행 중단점 설정 : break
```
(gdb) b(break) [함수명]         // 함수명으로 중단점 지정
(gdb) break 10                // 라인번호로 중단점 지정
(gdb) break [파일명]:[함수명]    // 파일:함수명으로 중단점 지정
(gdb) break [파일명]:10        // 파일:라인번호로 중단점 지정
```

#### 브레이크포인트, 워치포인트 설정

- **`set breakpoint auto-hw off`**: 소프트웨어 브레이크포인트 사용 설정.
- **`set can-use-hw-watchpoints 0`**: 소프트웨어 워치포인트 사용 설정.

- **하드웨어 브레이크포인트**는 CPU의 디버깅 기능을 사용하여 설정됩니다. 일반적으로 설정할 수 있는 개수가 제한되어 있습니다.
- **소프트웨어 브레이크포인트**는 코드에 특정 명령어를 삽입하여 설정됩니다. 이는 하드웨어 브레이크포인트보다 유연하지만, 약간의 성능 저하가 있을 수 있습니다.

### gdb tui

```
$ gdb test --tui

// 또는 gdb 실행 후
(gdb) layout src
```
tui 실행

#### 명령어

**화면 분할 및 탐색**

|명령어|설명|
|---|---|
|`Ctrl + x o`|다른 창으로 포커스를 이동합니다.|
|`Ctrl + x 2`|화면을 위아래로 분할하여 소스 코드 창을 추가합니다.|
|`Ctrl + x 1`|하나의 창만 남기고 나머지 창을 닫습니다.|
|`Ctrl + l`|화면을 새로 고칩니다.|

**소스 코드 및 어셈블리 코드 보기**

|명령어|설명|
|---|---|
|`layout src`|소스 코드 창을 표시합니다.|
|`layout asm`|어셈블리 코드 창을 표시합니다.|
|`layout split`|소스 코드와 어셈블리 코드를 모두 표시합니다.|
|`focus src`|소스 코드 창으로 포커스를 이동합니다.|
|`focus asm`|어셈블리 코드 창으로 포커스를 이동합니다.|

**기타 유용한 명령어**

|명령어|설명|
|---|---|
|`tui enable`|TUI 모드를 활성화합니다.|
|`tui disable`|TUI 모드를 비활성화합니다.|
|`update`|화면을 새로 고칩니다.|
|`refresh`|화면을 새로 고칩니다. (기존 명령어와 동일)|

---
## 헤더 라이브러리

| 파일명          | 설명                                                                                    |
| ------------ | ------------------------------------------------------------------------------------- |
| <assert.h>   | assert 매크로, 논리오류 및 디버깅 시 오류 형 등을 지원                                                   |
| <complex.h>  | 복소수 처리용 세트                                                                            |
| <ctype.h>    | 초기의 대-소 문자 변환 함수 제공                                                                   |
| <errno.h>    | 함수에서 발생하는 오류 형태 변환 등의 오류 처리                                                           |
| <fenv.h>     | 부동소수점 환경 제어                                                                           |
| <float.h>    | 부동소수점 특성 정의  <br>(두 숫자 사이의 최소 차이(_EPSILON), 숫자의 최대 자리수(_DIG), 숫자의 범위의 표현(_MIN, _MAX)) |
| <inttypes.h> | 정수형 변수의 정확한 변환                                                                        |
| <iso646.h>   | ISO 646 문자열 처리                                                                        |
| <limits.h>   | 정수형의 특성 정의, 정수 숫자 범위(_MIN, _MAX)                                                      |
| <locale.h>   | 로케일 관련 상수, 국제어 처리를 위한 적용                                                              |
| <math.h>     | 수학 함수                                                                                 |
| <setjmp.h>   | setjmp와 longjmp 매크로 선언                                                                |
| <signal.h>   | 다양한 예외 처리 제어                                                                          |
| <stdarg.h>   | 아규먼트 변수 처리 (va_start, va_arg, va_end 함수 등)                                            |
| <stdbool.h>  | 논리 변수                                                                                 |
| <stdint.h>   | 정수형 변수의 각종 정의/선언                                                                      |
| <stddef.h>   | 유용한 형과 매크로 정의/선언                                                                      |
| <stdio.h>    | C 언어의 입출력 제공 (printf 등)                                                               |
| <stdlib.h>   | 라이브러리                                                                                 |
| <string.h>   | 문자열 조작                                                                                |
| <tgmath.h>   | 수학 함수에서 일반 형 변환 관련                                                                    |
| <time.h>     | 시간과 날짜 변환 함수                                                                          |
| <wchar.h>    | 국제어 등의 처리를 위한 확장 문자 (문자열 처리)                                                          |
| <wctype.h>   | 확장 문자 처리                                                                              |

---
## 개념


---
## 자료형

### 포인터
```c
int a = 10;
int* ptr = &a;
printf("Value of a: %d\n", *ptr);
printf("Address of a: %p\n", ptr);
```

### 배열
```c
int arr[5] = {1, 2, 3, 4, 5};
for (int i = 0; i < 5; i++) {
    printf("%d ", arr[i]);
}
```

### 구조체 : struct
```c
struct Point {
    int x;
    int y;
};
```

하나 이상의 변수 묶기

### union
```c
union Data {
    int i;
    float f;
    char str[20];
};
```

구조체랑 비슷한데, 모든 멤버가 같은 메모리 공간을 공유

### 열거형 : enum
```c
#include <stdio.h>

enum Color { RED, GREEN, BLUE };

int main() {
    enum Color myColor = GREEN;
    if (myColor == GREEN) {
        printf("The color is green.\n");
    }
    return 0;
}
```

관련된 상수들 묶기

### 타입 이름 바꾸기 : typedef
```c
#include <stdio.h>

typedef unsigned long ulong;

int main() {
    ulong largeNumber = 1234567890;
    printf("Large number: %lu\n", largeNumber);
    return 0;
}
```

기존 타입에 새로운 이름을 부여할 수 있다.



---
## 문법

### main 함수
```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

프로그램의 시작점

### 함수 선언
```c
int add(int x, int y) {
    return x + y;
}

int main() {
    int result = add(3, 4);
    printf("Result: %d\n", result);
    return 0;
}
```

### if, else
```c
int a = 5;
if (a > 5) {
    printf("a는 5보다 큽니다.\n");
} else if (a == 5) {
    printf("a는 5와 같습니다.\n");
} else {
    printf("a는 5보다 작습니다.\n");
}
```

### for
```c
for (int i = 0; i < 5; i++) {
    printf("%d ", i);
}
```

### while
```c
int i = 0;
while (i < 5) {
    printf("%d ", i);
    i++;
}
```

### 비트 연산자

- **AND**: `&`
- **OR**: `|`
- **XOR**: `^`
- **NOT**: `~`
- **비트 이동**: `<<`, `>>`

### 논리 연산자
```c
if (height >= 180 && weight >= 90) {
}
```
`&`나 `|`는 비트연산자다. 정확한 값을 연산해서 준다.
하지만 `&&`나 `||`를 사용하면 하나만 조건에 위배되도 바로 결과 값 줌.
연산 줄일 수 있음.

### 전처리 지시문
```c
#include <stdio.h>
#define PI 3.14
#define CIRCLE_AREA(r) (PI * (r) * (r))

int main() {
    int radius = 5;
    printf("Area of circle: %f\n", CIRCLE_AREA(radius));
    return 0;
}
```

**`#define`**: 상수나 매크로를 정의

### 메모리 동적 할당
```c
    int* ptr;
    int n = 5;

    ptr = (int*)malloc(n * sizeof(int)); // 동적 메모리 할당
    free(ptr); // 메모리 해제
```

- **`malloc`**: 메모리를 동적으로 할당 (쓰레기 값 들어있음)
- **`free`**: 동적으로 할당된 메모리를 해제
- **`calloc`**: 0으로 초기화된 메모리를 할당
- **`realloc`**: 할당된 메모리 크기를 조정

### 가변 인자 함수
```c
#include <stdio.h>
#include <stdarg.h>

void printNumbers(int count, ...) {
    va_list args;
    va_start(args, count);

    for (int i = 0; i < count; i++) {
        int num = va_arg(args, int);
        printf("%d ", num);
    }

    va_end(args);
    printf("\n");
}

int main() {
    printNumbers(3, 1, 2, 3);
    printNumbers(5, 10, 20, 30, 40, 50);
    return 0;
}
```

### 구조체 포인터로 멤버 접근 연산자 : ->
```c
struct Node* head = NULL;
head = (struct Node*)malloc(sizeof(struct Node));
head->data = 1;
(*head).data = 1; // 둘은 동일하다
*head.data = 1; // 이건 head.data가 포인터일 때 그 주소 안에 있는 값
```

헤드 노드로 가는 포인터가 할당되었다고 해보자.
1. 해당 포인터가 가리키는 노드로 가서
2. 그 노드 안에 있는 멤버를 가리키고 싶다.
그때 사용되는게 `->` 연산자다.

`.` 연산자는 구조체 변수의 멤버에 접근할 수 있다.
`*` 을 앞에 붙이면 해당 주소에 있는 값에 접근할 수 있다.