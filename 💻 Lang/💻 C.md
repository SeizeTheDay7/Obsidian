- [[#VS Code 단축키|VS Code 단축키]]
- [[#헤더 라이브러리|헤더 라이브러리]]
- [[#개념|개념]]
	- [[#개념#네임스페이스|네임스페이스]]
	- [[#개념#함수에서 특정 변수 값 바꾸기|함수에서 특정 변수 값 바꾸기]]
	- [[#개념#토큰|토큰]]
- [[#자료형|자료형]]
	- [[#자료형#포인터|포인터]]
		- [[#포인터#포인터 선언|포인터 선언]]
		- [[#포인터#선언과 역참조의 차이|선언과 역참조의 차이]]
		- [[#포인터#포인터 연산|포인터 연산]]
		- [[#포인터#배열 포인터|배열 포인터]]
		- [[#포인터#함수 포인터|함수 포인터]]
		- [[#포인터#주소값이 필요할 때 포인터 변수 선언 대신 &|주소값이 필요할 때 포인터 변수 선언 대신 &]]
	- [[#자료형#배열|배열]]
	- [[#자료형#동적 배열|동적 배열]]
	- [[#자료형#size_t : 부호 없는 정수 타입|size_t : 부호 없는 정수 타입]]
	- [[#자료형#구조체 : struct|구조체 : struct]]
	- [[#자료형#공용체 : union|공용체 : union]]
	- [[#자료형#열거형 : enum|열거형 : enum]]
	- [[#자료형#타입 이름 바꾸기 : typedef|타입 이름 바꾸기 : typedef]]
	- [[#자료형#숫자 자료형|숫자 자료형]]
- [[#문법|문법]]
	- [[#문법#main 함수|main 함수]]
	- [[#문법#함수 선언|함수 선언]]
	- [[#문법#재귀 함수|재귀 함수]]
	- [[#문법#if, else|if, else]]
	- [[#문법#for|for]]
	- [[#문법#while|while]]
	- [[#문법#printf|printf]]
	- [[#문법#scanf|scanf]]
	- [[#문법#strlen : 문자열 크기 알아내기|strlen : 문자열 크기 알아내기]]
	- [[#문법#switch|switch]]
	- [[#문법#연산자|연산자]]
		- [[#연산자#산술 연산자|산술 연산자]]
		- [[#연산자#할당 연산자|할당 연산자]]
		- [[#연산자#기타 연산자|기타 연산자]]
		- [[#연산자#삼항 연산자|삼항 연산자]]
		- [[#연산자#비트 연산자|비트 연산자]]
		- [[#연산자#논리 연산자|논리 연산자]]
	- [[#문법#전처리 지시문 : 상수, 매크로 함수|전처리 지시문 : 상수, 매크로 함수]]
		- [[#전처리 지시문 : 상수, 매크로 함수#인라인 함수 대신 매크로 함수 써야 하는 경우|인라인 함수 대신 매크로 함수 써야 하는 경우]]
		- [[#전처리 지시문 : 상수, 매크로 함수#토큰 결합 연산자|토큰 결합 연산자]]
	- [[#문법#인라인 함수|인라인 함수]]
	- [[#문법#에러 처리|에러 처리]]
	- [[#문법#메모리 동적 할당 : malloc, free...|메모리 동적 할당 : malloc, free...]]
	- [[#문법#메모리 조작 : memmove, memcmp...|메모리 조작 : memmove, memcmp...]]
	- [[#문법#메모리 정렬|메모리 정렬]]
	- [[#문법#가변 인자 함수|가변 인자 함수]]
	- [[#문법#포인터 함수|포인터 함수]]
	- [[#문법#구조체 포인터로 멤버 접근 연산자 : ->|구조체 포인터로 멤버 접근 연산자 : ->]]
	- [[#문법#비트 필드|비트 필드]]
	- [[#문법#레지스터 안 쓰고 메모리 쓸거임 : volatile|레지스터 안 쓰고 메모리 쓸거임 : volatile]]
	- [[#문법#이 메모리 안 겹쳐질거임 : restrict|이 메모리 안 겹쳐질거임 : restrict]]
	- [[#문법#파일 입출력 함수 : fopen, fclose ...|파일 입출력 함수 : fopen, fclose ...]]
		- [[#파일 입출력 함수 : fopen, fclose ...#fopen|fopen]]
		- [[#파일 입출력 함수 : fopen, fclose ...#fclose|fclose]]
- [[#구현|구현]]
	- [[#구현#문자열 순회|문자열 순회]]
- [[#버그|버그]]
	- [[#버그#Segmentation fault|Segmentation fault]]
- [[#컴파일러, 디버거|컴파일러, 디버거]]
	- [[#컴파일러, 디버거#gcc|gcc]]
		- [[#gcc#명령어|명령어]]
		- [[#gcc#옵션|옵션]]
	- [[#컴파일러, 디버거#gdb|gdb]]
		- [[#gdb#명령어|명령어]]
		- [[#gdb#tui|tui]]
			- [[#tui#명령어|명령어]]
	- [[#컴파일러, 디버거#Splint : 코드 정적 분석 도구|Splint : 코드 정적 분석 도구]]
	- [[#컴파일러, 디버거#Valgrind : 코드 동적 분석 도구|Valgrind : 코드 동적 분석 도구]]




## VS Code 단축키

ctrl + t → excute (단축키는 커스텀 키바인딩, excute는 tasks.json에 적은거)

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

### 네임스페이스

**파일 안에서만 사용할 수 있는지, 파일 밖에 있는거 사용할 수 있는지 지정해줄 수 있다.**

```c
static int count = 0; // count 변수를 파일 범위로 설정(제한)
extern void increment(); 
```

- `increment` 함수를 `extern` 키워드로 선언하여 `file1.c`에서 정의된 `increment` 함수를 호출 (컴파일할 때 링크해줘야됨)

```c
gcc file1.o file2.o -o program
```

**서로 다른 namespace에 속해있는 명칭은 동일한 명칭일지라도 전혀 다른 개체를 지칭하는 명칭으로 취급된다**

1. label명
```c
foo:

	...
    
    goto foo;
```

- label명은 항상 `:`이 따라오거나 `goto`키워드 뒤에만 나온다.
- 🔍ex) label명 `foo`

2. 구조체(struct), 공용체(union), 열거(enum)를 위한 tag명칭
```c
enum foo{APPLE, KIWI, GRAPE};
```

- tag명칭은 `struct`, `union`, `enum`키워드 뒤에만 등장한다.
- 🔍ex) tag명칭 `foo`

3. 구조체(struct), 공용체(union)의 member명
```c
struct tag
{
	int foo;
} object;

object.foo;
```

- 멤버명은 구조체나 공용체 선언 문맥이나, 두 멤버 지정 연산자(`.` or `->`)뒤에만 나온다.
- 🔍ex) 구조체의 member명 `foo`

4. 그 외
- 함수명, 대상체 명칭(변수명), 열거 상수명, typedef name은 모두 같은 namespace을 공유한다.

### 함수에서 특정 변수 값 바꾸기
```c
int set_human(struct TEST a, int age, int gender) {
  a.age = age;
  a.gender = gender;

  return 0;
} // 이건 안됨

int set_human(struct TEST *a, int age, int gender) {
  a->age = age;
  a->gender = gender;

  return 0;
} // 이렇게 해야됨
```

특정한 변수의 값을 다른 함수를 통해 바꾸려면 변수의 주소값을 전달해야 한다

### 토큰

"토큰"은 컴파일러가 소스 코드를 분석할 때 사용하는 기본 단위다. C 언어에서 토큰은 프로그래밍 언어의 문법을 구성하는 가장 작은 단위로, 키워드, 식별자, 상수, 문자열 리터럴, 연산자, 기타 구분 기호(구두점) 등이 포함된다.

예를 들어, 다음 C 코드에서
```c
int a = 5;
```

이 코드는 여러 개의 토큰으로 구성된다:

- `int`
- `a`
- `=`
- `5`
- `;`


---
## 자료형

### 포인터
```c
int a = 10;
int* ptr = &a;
printf("Value of a: %d\n", *ptr);
printf("Address of a: %p\n", ptr);
```

원본을 바꾸고 싶을 땐 무조건 포인터를 사용해야 한다.

- 포인터의 용도 : 다른 곳에서도 원본값을 변경  
- 이중 포인터 용도 : 다른 곳에서도 가리키는 값을 변경

#### 포인터 선언
```c
int* p;  // p는 int 타입의 포인터
int *p;  // p는 int 타입의 포인터
```
자료형 뒤에 붙여도, 변수명 앞에 붙여도 뜻은 똑같지만

```c
int* p1, p2;
```
이렇게 사용하면 p1만 int* 포인터, p2는 그냥 int 이라 실수할 수 있음.

```c
int *p1, *p2;
```
이렇게 할 것

```c
(struct Node*)malloc(sizeof(struct Node));
```
타입 캐스팅할 땐 어쩔 수 없이 자료형 옆에 붙여야 함

#### 선언과 역참조의 차이
```c
int a = 10;     // 정수형 변수 a 선언 및 초기화
int* p = &a;    // 포인터 p 선언 및 a의 주소로 초기화
printf(*p); // p가 가리키는 주소의 값 출력
```
**선언할 때** 앞에 붙은 **별**은 **포인터 선언**이고 
**나중에** 포인터 변수 쓸 때 **또 별** 붙이는건 **역참조**

#### 포인터 연산
```c
char * ptr1 = 0;    // 0 대신 NULL을 사용해도 됩니다.
int * ptr2 = 0;    // 0 대신 NULL을 사용해도 됩니다.
double * ptr3 = 0;    // 0 대신 NULL을 사용해도 됩니다.

printf("%d번지, %d번지, %d번지\n", ptr1, ptr2, ptr3);
// 0번지, 0번지, 0번지

ptr1++;
ptr2++;
ptr3++;

printf("%d번지, %d번지, %d번지\n", ptr1, ptr2, ptr3);
// 1번지, 4번지, 8번지
```

변수의 주소에 1을 더하면 자료형의 크기만큼 더해진다

```c
int arr[3] = { 1, 2, 3 };
 
int * ptr = arr;
 
printf("%d %d %d\n", *ptr, *(ptr + 1), *(ptr + 2));
printf("%d %d %d\n", arr[0], arr[1], arr[2]);
```

arr[i] == `*`(arr+i) 이다.

#### 배열 포인터 (다차원 배열)

```c
int arr2d[2][3] = {
{10, 20, 30},
{40, 50, 60},
};

printf("%d %d\n", *arr2d[0], *arr2d[1]); // 10 40
```

arr2d[0]과 arr2d[1]은 각 부분 배열의 시작 주소를 가리킴. 
arr2d[0]은 2차원 배열의 첫 번째 행을 의미하고, arr2d[1]은 두 번째 행을 의미.

| arr[i][j] | *(arr+i)[j] | *(arr[i]+j) | *(*(arr+i)+j) |
| --------- | ----------- | ----------- | ------------- |
이 4개는 전부 같은 값을 가리킴

[참고](https://sejong-kr.libguides.com/c.php?g=942235&p=6822367)

![[Pasted image 20240806155005.png]]
[출처](https://www.tcpschool.com/c/c_array_twoDimensional)


```c
#include <stdio.h>
int main() {
  int arr[2][3] = {{1, 2, 3}, {4, 5, 6}};
  int **parr;

  parr = arr;

  printf("parr[1][1] : %d \n", parr[1][1]);  // 버그!

  return 0;
}
```

>[!memo] 배열 포인터 완벽 이해하기
>그렇다면 위 코드는 무슨 일을 했던 것일까요? 일단 parr 에는 arr 배열의 주소값이 들어가 있기는 합니다. 하지만 `parr[1][1]` 이 어떻게 해석되는지 생각해봅시다.
>
>먼저 `parr[1][1]` 은 `*(*(parr + 1) + 1)` 과 동일한 문장이죠? `parr + 1` 을 하면 뭐가 될까요? 지금 `parr` 은 `int*` 를 가리키는 포인터 이고, `int*` 의 크기는 8 바이트 이기 때문에 `parr + 1` 을 하면 실제 주소값이 8 증가하게 됩니다.
>
>따라서 `parr + 1` 은 `arr` 배열의 세 번째 원소의 주소값을 가지게 됩니다 (왜냐면 `int` 는 4 바이트 니까). 따라서 `*(parr + 1)` 은 3 이 될 것입니다.
>
>그 다음에 `*(parr + 1) + 1` 을 하면 몇이 증가할까요? 현재 (parr + 1) 의 타입은 `int *` 입니다. 따라서 `int` 의 크기 만큼인 4 가 늘어나게 됩니다. 결국 `*(parr + 1) + 1` 은 7 이 되겠죠
>
>그래서 결국 `*(*(parr + 1) + 1)` 은 마치 주소값 7 에 있는 값을 읽어라! 하는 말과 동일합니다. 그리고 해당 위치는 프로그램이 읽을 수 없기에 오류가 발생하게 되는 것이지요. 이해가 되시나요?

[출처](https://modoocode.com/25)


#### 함수 포인터

함수 포인터 선언 형식
```c
return_type (*pointer_name)(parameter_list);
```

```c
#include <stdio.h> 
 
void fun(int num) {
    printf("%d\n", num);
}
 
int main() {
    void (*fun_ptr)(int);   // 함수 포인터 선언
 
    // 아래는 전부 같은 기능을 하는 코드이다.
    fun_ptr = &fun;
    fun_ptr = fun;
    fun_ptr = *fun;
    fun_ptr = **fun;
    
    return 0;
}
```

함수의 명령 시작 주소로 가도 결국 또
함수 이름(함수의 명령 시작 주소 가리키는 포인터로 해석됨)이 있어서 
4가지가 전부 같은 기능

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int main() {
    int (*operation)(int, int);
    operation = add;
    printf("Addition: %d\n", operation(5, 3));

    operation = subtract;
    printf("Subtraction: %d\n", operation(5, 3));

    return 0;
}
```

함수의 주소를 저장하는 포인터

- 함수 포인터도 포인터이기 때문에, 일반적인 포인터와 마찬가지로 **메모리 주소**를 가리킨다.
- 하지만 일반적인 포인터와 달리, 함수 포인터는 **데이터**가 아닌 **코드의 위치**를 가리킨다.
- 마치 배열을 가리키는 포인터가 배열의 시작부분을 가리키는 것과 같이, 함수 포인터도 코드를 가리킬 때 **코드의 시작부분**을 가리킨다.
- 또한 함수 포인터를 통해 메모리를 **할당**하거나 **회수**하는 것이 불가능하다.
- 따라서 함수 포인터를 대상으로 malloc(), free() 함수를 사용할 수 없다.

```c
int (*operations[3])(int, int) = {add, subtract, multiply};  // 함수 포인터 배열 선언 및 초기화
int a = 5, b = 3;
```

일반 자료형이 "이 친구는 이런 애에요~"라고 하는 것처럼,
함수 포인터도 "이런 함수들"을 넣을 수 있는 것.


#### 주소값이 필요할 때 포인터 변수 선언 대신 &
```c
Stack *rS;
rS = (Stack *)calloc(1,sizeof(Stack));
push(rS, dequeue(q));
```

주소값이 필요하면 곧이 곧대로 포인터 변수 쓰고 malloc하는게 아니라

```c
Stack s;
num = dequeue(q);
push(&s, num);
```

그냥 바로 변수 선언한 다음 & 쓰면 된다.


### 배열
```c
int arr[5] = {1, 2, 3, 4, 5};
int arr_b[2][3] = {{1, 2, 3}, {4, 5, 6}};
int arr_c[] = {1, 2, 3, 4};
for (int i = 0; i < 5; i++) {
    printf("%d ", arr[i]);
}
```

```c
printf("a[3] : %d \n", arr[3]); // a[3] : 4 
printf("*(a+3) : %d \n", *(arr + 3)); // *(a+3) : 4
```  

배열 이름은 배열의 첫 번째 요소를 가리키는 포인터로 해석된다.
arr[3] 이라 사용한 것은 사실 `*`(arr + 3) 으로 바뀌어서 처리가 된다

```c
3[arr] : 4 
*(3+a) : 4
```
그래서 이것도 arr[3]이랑 똑같음

### 동적 배열
```c
int n = 5;
    int* arr = (int*)malloc(n * sizeof(int));
```

### size_t : 부호 없는 정수 타입
```c
char str[] = "Hello, World!";
size_t len = strlen(str);
```

- 시스템의 최대 메모리 크기를 표현
- 각 시스템마다 적절한 크기로 정의됨 (32bit = 4byte, 64bit = 8byte)

### 구조체 : struct
```c
typedef struct Point {
    int x;
    int y;
} P;
```

하나 이상의 변수 묶기 (`struct Point` 형의 `P`라는 구조체 변수를 정의함)

### 공용체 : union
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

### 숫자 자료형
| 자료형                  | 크기(바이트) | 최소값                                              | 최대값                                             |
| -------------------- | ------- | ------------------------------------------------ | ----------------------------------------------- |
| `char`               | 1       | `-128`                                           | `127`                                           |
| `unsigned char`      | 1       | `0`                                              | `255`                                           |
| `short`              | 2       | `-32,768`                                        | `32,767`                                        |
| `unsigned short`     | 2       | `0`                                              | `65,535`                                        |
| `int`                | 4       | `-2,147,483,648`                                 | `2,147,483,647`                                 |
| `unsigned int`       | 4       | `0`                                              | `4,294,967,295`                                 |
| `long`               | 4 또는 8  | `-2,147,483,648` 또는 `-9,223,372,036,854,775,808` | `2,147,483,647` 또는 `9,223,372,036,854,775,807`  |
| `unsigned long`      | 4 또는 8  | `0`                                              | `4,294,967,295` 또는 `18,446,744,073,709,551,615` |
| `long long`          | 8       | `-9,223,372,036,854,775,808`                     | `9,223,372,036,854,775,807`                     |
| `unsigned long long` | 8       | `0`                                              | `18,446,744,073,709,551,615`                    |

- **크기 및 범위**: 자료형의 크기와 범위는 시스템 및 컴파일러에 따라 달라질 수 있습니다. 특히 `long`은 일부 시스템에서 4바이트, 일부 시스템에서 8바이트를 가질 수 있습니다. (stdint.h에서 제공하는 고정 폭 정수형 자료형은 크기와 범위가 명확하긴 한데 웬만하면 필요 없을듯)

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

### 재귀 함수
```c
int factorial(int n) {
    if (n <= 1) {
        return 1;
    }
    return n * factorial(n - 1);
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

```c
if (a > 0)
	printf("a is positive\n");
else
	printf("a is non-positive\n");
```

한 줄만 있을 땐 중괄호 생략 가능

### for
```c
for (int i = 0; i < 5; i++) {
    printf("%d ", i);
}
```

조건과 증감만 사용하기
```c
for (; root; root = root->left)
```

- 초기화 부분: 없음 (; 앞 부분이 비어 있음).
- 조건 부분: root가 NULL이 아닐 때까지 반복.
- 증감 부분: root를 root->left로 갱신하여 계속 왼쪽 자식 노드로 이동.

### while
```c
int i = 0;
while (i < 5) {
    printf("%d ", i);
    i++;
}
```

### printf
```c
#include <stdio.h>

int printf(const char *format, ...);
printf("You entered: %d, %f, %c, %s\n", a, b, c, str);
```

- **format**: 출력할 내용을 지정하는 서식 지정 문자열입니다. 이 문자열은 일반 텍스트와 서식 지정자를 포함할 수 있습니다.
- **...**: 가변 인수 목록으로, 서식 지정자에 대응하는 값을 제공합니다.

**서식 지정자** : 출력할 데이터의 타입을 지정
- `%d` 또는 `%i`: 정수형(int)
- `%u`: 부호 없는 정수형(unsigned int)
- `%f`: 부동 소수점 형식(float)
- `%lf`: 부동 소수점 형식(double)
- `%c`: 문자형(char)
- `%s`: 문자열(char 배열 또는 포인터)
- `%p`: 포인터 주소
- `%x` 또는 `%X`: 부호 없는 정수를 16진수로 출력

### scanf
```c
#include <stdio.h>

int scanf(const char *format, ...);
```

```c
scanf("%d", &num);
```

```c
scanf("%d %d %d", &H, &W, &N);
```

- **format**: 입력받을 데이터의 서식을 지정하는 문자열입니다. 서식 지정자는 `printf` 함수와 유사합니다.
- **...**: 가변 인수 목록으로, 입력받은 데이터를 저장할 변수의 주소를 제공합니다.

- `%d` 또는 `%i`: 정수형(int)
- `%u`: 부호 없는 정수형(unsigned int)
- `%f`: 부동 소수점 형식(float)
- `%lf`: 부동 소수점 형식(double)
- `%c`: 문자형(char)
- `%s`: 문자열(char 배열 또는 포인터) 
	- 공백(스페이스바), 탭, 개행 문자 등 만나면 입력 중단 (다음 단어는 버퍼에 남아 다음 입력을 기다림)
- `%x` 또는 `%X`: 부호 없는 정수를 16진수로 입력

### strlen : 문자열 크기 알아내기

```c
char str[] = "Hello, World!";
int len = strlen(str);
```


### switch
```c
switch (expression) {
    case constant1:
        // statement(s)
        break;
    case constant2:
        // statement(s)
        break;
    // 다른 case들...
    default:
        // statement(s)
}
```

주로 단일 변수의 값을 여러 경우에 대해 각각 다른 동작을 수행함
default : 모든 case가 일치하지 않을 때 실행되는 블록

### 연산자

#### 산술 연산자

| 연산자 | 설명   | 예제    |
|--------|--------|---------|
| `+`    | 덧셈   | `a + b` |
| `-`    | 뺄셈   | `a - b` |
| `*`    | 곱셈   | `a * b` |
| `/`    | 나눗셈 | `a / b` |
| `%`    | 나머지 | `a % b` |

#### 할당 연산자

| 연산자   | 설명           | 예제         |
| ----- | ------------ | ---------- |
| `=`   | 할당           | `a = b`    |
| `+=`  | 더해서 할당       | `a += b`   |
| `-=`  | 빼서 할당        | `a -= b`   |
| `*=`  | 곱해서 할당       | `a *= b`   |
| `/=`  | 나눠서 할당       | `a /= b`   |
| `%=`  | 나머지를 구해서 할당  | `a %= b`   |
| `&=`  | 비트 AND 후 할당  | `a &= b`   |
| `     | =`           | 비트 OR 후 할당 |
| `^=`  | 비트 XOR 후 할당  | `a ^= b`   |
| `<<=` | 왼쪽 시프트 후 할당  | `a <<= 1`  |
| `>>=` | 오른쪽 시프트 후 할당 | `a >>= 1`  |

#### 기타 연산자

| 연산자      | 설명              | 예제                   |
| -------- | --------------- | -------------------- |
| `? :`    | 조건 연산자 (삼항 연산자) | `a ? b : c`          |
| `sizeof` | 데이터 크기 반환       | `sizeof(a)`          |
| `&`      | 주소 연산자          | `&a`                 |
| `*`      | 포인터 연산자         | `*p`                 |
| `,`      | 쉼표 연산자          | `a = (b = 3, b + 2)` |
| `->`     | 구조체 포인터 멤버 접근   | `p->member`          |
| `.`      | 구조체 멤버 접근       | `a.member`           |
| `(type)` | 형 변환            | `(int)a`             |


#### 삼항 연산자

```c
int max_value = (a > b) ? a : b;
```

`a > b`가 참이면 `a`의 값을 반환 
`a > b`가 거짓이면 `b`의 값을 반환

#### 비트 연산자

- **AND**: `&`
- **OR**: `|`
- **XOR**: `^`
- **NOT**: `~`
- **비트 이동**: `<<`, `>>`

#### 논리 연산자
```c
if (height >= 180 && weight >= 90) {
}
```
`&`나 `|`는 비트연산자다. 정확한 값을 연산해서 준다.
하지만 `&&`나 `||`를 사용하면 하나만 조건에 위배되도 바로 결과 값 줌.
연산 줄일 수 있음.


### 전처리 지시문 : 상수, 매크로 함수
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

**`#define`**: 상수나 매크로를 정의한다. 코드에 텍스트가 치환된다.
전처리기 단계에서 코드에 그대로 합쳐져서 디버깅하기가 어렵다.
함수보다도 빠르게 실행될 수 있다.

**괄호 넣어줘야 하는 이유**

`#define MAX(x, y) ((x) > (y) ? (x) : (y))`에서 괄호를 제거하여 `#define MAX(x, y) (x > y ? x : y)`로 변경하면 의도하지 않은 결과를 초래할 수 있습니다. 괄호를 추가하는 이유는 매크로를 사용할 때 발생할 수 있는 연산자 우선순위 문제를 방지하기 위해서입니다.

```c
int max_value = (a + 1 > b ? a + 1 : b);
```

이 경우, `a + 1 > b`가 먼저 평가됩니다. 따라서 `1`이 `b`와 비교되기 때문에 예상치 못한 결과를 초래할 수 있습니다.


#### 인라인 함수 대신 매크로 함수 써야 하는 경우

- **코드 생성 제어가 필요할 때** : 매크로 함수는 코드가 생성되는 방식을 더 직접적으로 제어할 수 있다. 예를 들어, 특정한 코드 블록을 조건부로 포함하거나 생략할 때 매크로가 유용하다.
- **다양한 타입을 지원해야 하는 경우** : 매크로 함수는 텍스트 치환을 통해 다양한 타입의 인수를 처리할 수 있다. 인라인 함수는 특정 타입에 대해서만 동작한다.
- **코드 내 문맥 정보를 활용해야 하는 경우** : 매크로는 코드의 소스 파일, 라인 번호 등을 `__FILE__` 및 `__LINE__` 매크로를 통해 삽입할 수 있다. 이는 디버깅 정보나 로그 메시지를 포함할 때 유용하다.
- **오래된 컴파일러 지원** : 일부 오래된 컴파일러나 특정 임베디드 시스템 컴파일러는 인라인 함수 지원이 제한적일 수 있음

#### 토큰 결합 연산자

```c
#define AddName(x, y) x##y
int AddName(a, b);
```

```c
int ab;
```

`##`로 변수 이름을 합칠 수 있다.

### 인라인 함수
```c
#include <stdio.h>

static inline int max(int a, int b) {
  return (a > b) ? a : b;
}

int main() {
  printf("3과 2 중 최대값은: %d\n", max(3, 2));
  return 0;
}
```

디버깅이 편하고 연산자 우선순위같은거 고민할 필요 없는 매크로 함수.
디버깅 도구에서 함수로 인식되고 추적할 수 있다.

### 에러 처리
```c
#include <stdio.h>
#include <errno.h>
#include <string.h>

int main() {
    FILE *file;
    file = fopen("non_existent_file.txt", "r");

    if (file == NULL) {
        printf("Error opening file: %s\n", strerror(errno));
    }

    return 0;
}
```

`errno` 변수를 통해 에러 코드를 확인하고, `strerror` 함수를 사용하여 에러 메시지를 출력할 수 있음

### 메모리 동적 할당 : malloc, free...
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

**calloc 사용법**
```c
rS = (Stack *)calloc(1,sizeof(Stack));
```

### 메모리 조작 : memmove, memcmp...

**memmove**
```c
void *memmove(void *dest, const void *src, size_t n);

memmove(str + 7, str, 6);
```

`memmove` 함수는 복사할 메모리 블록을 임시 버퍼에 저장한 후, 이 임시 버퍼에서 대상 메모리 블록으로 복사합니다. 이를 통해 중복된 영역에서 안전하게 복사를 수행할 수 있습니다.

**memcpy**
```c
void *memcpy(void *dest, const void *src, size_t n);

memcpy(dest, src, strlen(src) + 1);
```

`memcpy` 함수는 소스 메모리 블록에서 대상 메모리 블록으로 데이터를 직접 복사합니다. 중복된 영역에 대해서는 안전하지 않습니다.

**memcmp**
```c
int memcmp(const void *s1, const void *s2, size_t n);
```

`memcmp` 함수는 두 메모리 블록을 바이트 단위로 비교합니다. 비교 결과는 정수 값으로 반환되며, 두 메모리 블록이 같은지 여부를 판단할 수 있습니다.

매개변수
- `s1`: 첫 번째 메모리 블록의 시작 주소.
- `s2`: 두 번째 메모리 블록의 시작 주소.
- `n`: 비교할 바이트 수.

반환 값
- `0`: 두 메모리 블록이 동일함.
- `양수`: 첫 번째 블록이 두 번째 블록보다 큼.
- `음수`: 첫 번째 블록이 두 번째 블록보다 작음.


### 메모리 정렬
```c
struct Aligned {
    char a;
    int b;
    char c;
};

struct Packed {
    char a;
    char c;
    int b;
} __attribute__((packed));
```

![[memory pack.png]]

왼쪽처럼 구조체 대충 짜면 메모리 낭비하는데
오른쪽처럼 정성 들여서 짜면 메모리 효율적 사용.

근데 귀찮으면 `__attribute__((packed));` 넣으면 됨.

```c
struct Foo
{
   uint32_t mUInt1;     // 32비트 
   int32_t  mInt1;      // 32비트
   char*    mCharPtr;   // 32비트
   uint8_t  mUint2;     // 8비트
   bool     mBool1;     // 8비트
   uint8_t  pad[2];     // 16비트 패딩 데이터
};
```

```c
#pragma pack(push, 1) // 1바이트 정렬

struct FooPacked {
    uint32_t mUInt1;   // 32비트, 4바이트
    int32_t  mInt1;    // 32비트, 4바이트
    char*    mCharPtr; // 32비트, 4바이트
    uint8_t  mUint2;   // 8비트, 1바이트
    bool     mBool1;   // 8비트, 1바이트
    // 패딩 없음
};

#pragma pack(pop) // 원래의 정렬로 복원
```

`#pragma pack(push, 1)`은 구조체의 모든 멤버를 1바이트 경계에 맞춰 정렬하도록 지정


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

### 포인터 함수
```c
void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
```

함수 인자에 포인터 넣으면 함수의 지역 변수가 아니라 원본 변수를 조작할 수 있음

**포인터 반환하는 함수**
```c
int* allocateArray(int size) {
    int* array = (int*)malloc(size * sizeof(int));
    return array;
}
```

함수 내에서 할당된 메모리의 주소나 전역 변수의 주소를 반환할 수 있음

### 구조체 포인터로 멤버 접근 연산자 : ->
```c
struct Node* head = NULL;
head = (struct Node*)malloc(sizeof(struct Node));
head->data = 1;
(*head).data = 1; // 둘은 동일하다
*head.data = 1; // 이건 he구조체에서 정수형 데이터를 비트 단위로 나누어 사용할 수 있는 기능ad.data가 포인터일 때 그 주소 안에 있는 값
```

헤드 노드로 가는 포인터가 할당되었다고 해보자.
1. 해당 포인터가 가리키는 노드로 가서
2. 그 노드 안에 있는 멤버를 가리키고 싶다.
그때 사용되는게 `->` 연산자다.

`.` 연산자는 구조체 변수의 멤버에 접근할 수 있다.
`*` 을 앞에 붙이면 해당 주소에 있는 값에 접근할 수 있다.

### 비트 필드
```c
#include <stdio.h>

struct Flags {
    unsigned int a : 1;     // a는 1비트 크기
    unsigned int b : 3;     // b는 3비트 크기
    unsigned int c : 7;     // c는 7비트 크기
};

int main()
{
    struct Flags f1;    // 구조체 변수 선언

    f1.a = 1;      //   1: 0000 0001, 비트 1개
    f1.b = 15;     //  15: 0000 1111, 비트 4개
    f1.c = 255;    // 255: 1111 1111, 비트 8개
    
    return 0;
}
```

구조체에서 정수형 데이터를 비트 단위로 나누어 사용할 수 있는 기능

### 레지스터 안 쓰고 메모리 쓸거임 : volatile
```c
volatile bool flag = true;
```

- `volatile` 키워드가 붙은 변수는 컴파일러가 최적화하지 않도록 하여, 항상 메모리에서 값을 읽도록 함. (변덕스럽게 변할 수 있다~)
- 멀티스레딩 환경이나 하드웨어 레지스터에서 값을 읽을 때 유용함.

### 이 메모리 안 겹쳐질거임 : restrict
```c
void copyArray(int* restrict dest, const int* restrict src, size_t n) {
    for (size_t i = 0; i < n; i++) {
        dest[i] = src[i];
    }
}
```

- `restrict` 키워드를 사용하면 포인터가 가리키는 메모리 블록이 다른 포인터가 가리키는 메모리 블록과 겹치지 않음을 컴파일러에 알림.
- 이를 통해 컴파일러는 최적화를 수행할 수 있음.

### 파일 입출력 함수 : fopen, fclose ...

- **`fopen`**: 파일을 열고 파일 포인터를 반환합니다.
- **`fclose`**: 파일을 닫습니다.
- **`fgets`**: 파일에서 문자열을 읽어옵니다.
- **`fgetc`**: 파일에서 한 문자를 읽어옵니다.
- **`fputs`**: 문자열을 파일에 씁니다.
#### fopen
```c
FILE *fopen(const char *filename, const char *mode);
```

- `filename`: 열고자 하는 파일의 이름을 나타내는 문자열입니다.
- `mode`: 파일을 여는 모드를 나타내는 문자열입니다. 주요 모드는 다음과 같습니다:
    - `"r"`: 읽기 모드로 파일을 엽니다. 파일이 존재해야 합니다.
    - `"w"`: 쓰기 모드로 파일을 엽니다. 파일이 존재하지 않으면 새로 생성됩니다.
    - `"a"`: 추가 모드로 파일을 엽니다. 파일이 존재하지 않으면 새로 생성됩니다.
    - `"r+"`: 읽기/쓰기 모드로 파일을 엽니다. 파일이 존재해야 합니다.
    - `"w+"`: 읽기/쓰기 모드로 파일을 엽니다. 파일이 존재하지 않으면 새로 생성됩니다.
    - `"a+"`: 읽기/쓰기 추가 모드로 파일을 엽니다. 파일이 존재하지 않으면 새로 생성됩니다.

```c
FILE *file = fopen("example.txt", "r");
```

`fopen` 함수는 파일을 열고 파일 포인터를 반환합니다. 파일이 성공적으로 열리면 해당 파일에 대한 포인터를 반환하고, 실패하면 NULL을 반환합니다

#### fclose
```c
int fclose(FILE *stream);
```

`fclose` 함수는 열려 있는 파일을 닫습니다. 파일 포인터를 인수로 받아 파일을 닫고, 성공하면 0을 반환하며, 실패하면 EOF를 반환합니다.


---
## 구현

### 문자열 순회

1. for문으로 문자열 배열 인덱스 순회
```c
for (i = 0; str[i] != '\0'; i++) {
	printf("%c\n", str[i]);
}
```

2. 포인터로 문자열 순회
```c
char *ptr;

for (ptr = str; *ptr != '\0'; ptr++) {
    printf("%c\n", *ptr);
}
```

3. while로 문자열 순회
```c
while (str[i] != '\0') {
	printf("%c\n", str[i]);
	i++;
}
```



---
## 버그

### Segmentation fault

- NULL 포인터 참조
- 배열 범위 초과 접근
- 잘못된 포인터 사용
- 중복 해제된 포인터 사용
- 스택 오버플로우
- 읽기 전용 메모리 수정 시도

해결 1 : malloc + 초기화하거나 calloc



---
## 컴파일러, 디버거

### gcc 

#### 명령어

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

#### 옵션

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

### gdb
#### 명령어 

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

**코드 보기 : list**
```
(gdb) l(list)
(gdb) list 10
(gdb) list [함수명]
(gdb) list -  // 이전 10라인을 출력한다.
(gdb) list [파일명]:[함수명]
(gdb) list [파일명]:10
```

**실행 중단점 설정 : break**
```
(gdb) b(break) [함수명]         // 함수명으로 중단점 지정
(gdb) break 10                // 라인번호로 중단점 지정
(gdb) break [파일명]:[함수명]    // 파일:함수명으로 중단점 지정
(gdb) break [파일명]:10        // 파일:라인번호로 중단점 지정
```

**브레이크포인트, 워치포인트 설정**

- **`set breakpoint auto-hw off`**: 소프트웨어 브레이크포인트 사용 설정.
- **`set can-use-hw-watchpoints 0`**: 소프트웨어 워치포인트 사용 설정.

- **하드웨어 브레이크포인트**는 CPU의 디버깅 기능을 사용하여 설정됩니다. 일반적으로 설정할 수 있는 개수가 제한되어 있습니다.
- **소프트웨어 브레이크포인트**는 코드에 특정 명령어를 삽입하여 설정됩니다. 이는 하드웨어 브레이크포인트보다 유연하지만, 약간의 성능 저하가 있을 수 있습니다.

#### tui

```
$ gdb test --tui

// 또는 gdb 실행 후
(gdb) layout src
```
tui 실행

##### 명령어

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

### Splint : 코드 정적 분석 도구

```bash
splint example.c
```

사용되지 않는 변수: 선언되었지만 사용되지 않는 변수
초기화되지 않은 변수: 초기화되지 않은 상태에서 사용된 변수
포인터 오류: 잘못된 포인터 사용, 널 포인터 역참조 등
배열 경계 초과: 배열의 경계를 넘어서는 접근
형식 불일치: 형식 불일치로 인한 잠재적 버그

### Valgrind : 코드 동적 분석 도구

1. 기본 사용법
```bash
valgrind ./example
```

2. 메모리 누수 검출
```bash
valgrind --leak-check=full ./example
```

3. 출력 결과를 파일에 저장
```bash
valgrind --log-file=valgrind-output.txt ./example
```

4. 요약 정리
```bash
valgrind -s ./example
```

- `--leak-check=yes`: 메모리 누수를 확인합니다.
- `--leak-check=full`: 상세한 메모리 누수 정보를 확인합니다.
- `--track-origins=yes`: 초기화되지 않은 메모리의 사용 위치를 추적합니다.
- `--log-file=<file>`: Valgrind의 출력을 지정한 파일에 저장합니다.

