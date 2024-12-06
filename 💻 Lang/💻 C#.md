- [[#Tip|Tip]]
- [[#개념|개념]]
	- [[#개념#전역 변수와 지역 변수|전역 변수와 지역 변수]]
- [[#자료형|자료형]]
	- [[#자료형#기본 자료형 모음|기본 자료형 모음]]
	- [[#자료형#자료형 변환|자료형 변환]]
	- [[#자료형#const : 상수 선언|const : 상수 선언]]
	- [[#자료형#float|float]]
	- [[#자료형#var : 아무거나 넣어도 됨|var : 아무거나 넣어도 됨]]
	- [[#자료형#배열|배열]]
		- [[#배열#Rank, Length, GetLength()|Rank, Length, GetLength()]]
		- [[#배열#가변 배열|가변 배열]]
	- [[#자료형#GetType() : 자료형 확인|GetType() : 자료형 확인]]
	- [[#자료형#자료형 기본값으로 초기화|자료형 기본값으로 초기화]]
- [[#문법|문법]]
	- [[#문법#변수 선언 방식|변수 선언 방식]]
	- [[#문법#전위 연산자, 후위 연산자|전위 연산자, 후위 연산자]]
	- [[#문법#삼항 연산자|삼항 연산자]]
	- [[#문법#제어문 종류 : if, while, goto 등|제어문 종류 : if, while, goto 등]]
	- [[#문법#for문|for문]]
	- [[#문법#Switch 문|Switch 문]]
	- [[#문법#do while|do while]]
	- [[#문법#foreach|foreach]]
	- [[#문법#goto|goto]]
	- [[#문법#화살표 함수 (람다식) : 메서드 코드 줄이기|화살표 함수 (람다식) : 메서드 코드 줄이기]]
	- [[#문법#문자열 입력|문자열 입력]]
	- [[#문법#Console.WriteLine() : 명령줄 출력|Console.WriteLine() : 명령줄 출력]]
	- [[#문법#여러 문자열 합쳐서 출력|여러 문자열 합쳐서 출력]]
	- [[#문법#변수?.멤버 : null 체크하며 멤버나 메서드 접근|변수?.멤버 : null 체크하며 멤버나 메서드 접근]]
	- [[#문법#튜플 리터럴|튜플 리터럴]]
- [[#구현|구현]]



## Tip
---

**vscode에서 C# 컴파일**
dotnet new console 하면 프로젝트 생성
dotnet run 하면 실행

**C# 특징**
- 대소문자를 구분
- 공백이나 줄 바꿈은 무시

**코드 조각 자동 생성**
svm + Tab Tab
cw + Tab Tab 
if + Tab Tab
else + Tab Tab
for + Tab Tab

**using static 구문**
using static System.Console; 구문으로 System.Console을 생략하여 WriteLine()만 작성하여 사용할 수 있다.

```C#
int number = 1_000_000;
```
세 자리마다 콤마로 구분되는 긴 형태를 표현할 수 있다

**@ 기호로 여러 줄 문자열 저장할 수 있다**
``` c#
string multiLines = @"
	안녕하세요,
	반갑습니다.
	";
```


## 개념
---

### 전역 변수와 지역 변수

전역 변수, 필드 : 클래스와 같은 레벨에서 선언된 변수
지역 변수 : 함수 레벨에서 선언된 변수

동일한 이름으로 전역 변수와 지역 변수를 같이 선언할 수 있다.
함수 내에서는 지역 변수를 쓰고, 지역 변수가 없으면 전역 변수를 쓴다.

C#에서는 전역 변수가 아닌 필드라는 단어를 주로 사용하며,
전역 변수는 언더스코어(`_`) 또는 `m_` 접두사를 붙이는 경향이 있다.




## 자료형
---

### 기본 자료형 모음

| 데이터 형식 | 설명                                   |
| ------ | ------------------------------------ |
| int    | 정수형 데이터를 저장. 더 큰 정수는 long을 사용.       |
| string | 문자열 데이터를 저장.                         |
| bool   | 참 값 거짓 값 저장.                         |
| double | 실수형 데이터 저장. double, float 둘 다 실수 저장. |
| object | C#에서 사용하는 모든 형식의 데이터를 저장.            |

### 자료형 변환

| 메서드                | 대체             | 설명                        |
| ------------------ | -------------- | ------------------------- |
| Convert.ToString() |                | 숫자 데이터 형식을 문자열로 변경        |
| Convert.ToInt32()  | int.Parse()    | 숫자 데이터 형식을 정수 형식으로 변경     |
| Convert.ToDouble() | double.Parse() | 숫자 데이터 형식을 실수 형식으로 변경     |
| Convert.ToChar()   |                | 입력받은 숫자 또는 문자열 하나를 문자로 변경 |
데이터 형식 변환은 괄호 기호 이외에 Convert 클래스의 주요 메서드도 사용할 수 있다.

```C#
Convert.ToString(숫자, 2);
```
Convert 클래스의 ToString() 메서드는 특정 숫자의 값을 문자열로 변환할 수 있다. 정수를 이진수 문자열로 얻고 싶다면 위와 같은 형태로 두 번째 옵션에 이진수를 나타내는 2를 지정한다.

```C#
Convert.ToString(숫자, 2).PadLeft(8,'0');
```
비트 연산식을 이해하기 편하게 여덟 자리로 잡고, PadLeft() 메서드를 사용해서 8칸을 기준으로 이진수 문자열을 출력한다.

```c#
Convert.ToString(value, base); // base는 변환할 때 사용할 수치 체계
Convert.ToInt32(value, fromBase); // fromBase는 입력값의 현재 진법
```
int는 변환할 때 사용하는 진법이 정해져 있으니 입력값의 현재 진법을 알아야 하고,
string은 값을 어떤 진법으로 바꿀지 정해야 한다.

### const : 상수 선언
```C#
const int MAX = 100;
```

const로 선언하면 값 못바꾸고, 선언과 동시에 초기화해야 함.

### float
```C#
float num = 99.99f;
```
float 키워드로 실수 데이터를 직접 입력할 때는 대문자 F 또는 소문자 f를 접미사로 사용하여 대입해야 한다. 접미사를 사용하지  않으면 실수 값을 기본적으로 double 형식으로 인식하여 float 형식 변수에 담을 수 없다.

### var : 아무거나 넣어도 됨
```C#
var number = 1234;
```
C# 컴파일러는 **var**로 선언된 변수에 저장되는 값을 자동으로 추론해서 적당한 형식으로 변환한다. 이를 형식 추론(type inference)이라고 한다.

### 배열
```cs
int[] oneArray; // 1차원 배열 선언
int[,] twoArray; // 2차원 배열 선언
int[,,] threeArray; // 3차원 배열 선언
```

배열 선언

```cs
oneArray = new int[2] {1,2};
twoArray = new int[2,2] {{1,2},{3,4}};
```

배열 초기화
선언과 동시에 초기화하면 new 자료형 빼먹어도 된다
#### Rank, Length, GetLength()
```cs
arr.Rank // 3차원 배열이면 3
arr.Length // 배열 길이 반환
arr.GetLength(1) // 행의 개수
arr.GetLength(2) // 열의 개수
```

#### 가변 배열
```cs
// [2][] 형태로 두 번째를 비워 두면 동적으로 자료 n개로 초기화 가능
int[][] zagArray = new int[2][];
```

#### 리스트
```cs
List<int> oddNumbers = new List<int>()
```

```cs
List.Count // 요소 개수
List.Contains(3) // 들어있는지 확인
List.Add(3) // 요소 더하기
List.Remove(3) // 요소 지우기
List.RemoveAt(0) // 특정 인덱스에 있는 요소 지우기
List.Clear() // 리스트 지우기
```


#### 구조체
```cs
struct Point
{
    public int X;
    public int Y;
}
```
여러 자료형 변수를 하나로 묶을 수 있다

```cs
Point[] points = new Point[2];
```
구조체 배열도 만들 수 있다.

**내장 구조체 예시**
- DateTime 구조체: 시간/날짜 관련 모든 정보 제공
- TimeSpan 구조체: 시간/날짜 간격에 대한 모든 정보 제공
- Char 구조체: 문자 관련 모든 정보 제공
- Guid 구조체: 절대로 중복되지 않는 유일한 문자열을 생성

##### DateTime
```cs
> DateTime.Now.Year
2019
> DateTime now = DateTime.Now;
> Console.WriteLine(now.Date);
2019-09-23 오전 12:00:00
```

##### TimeSpan
```cs
class TimeSpanDemo
{
    static void Main()
    {
        // 시간 차 구하기
        TimeSpan dday = Convert.ToDateTime("2024-12-25") - DateTime.Now;
        Console.WriteLine((int)dday.TotalDays);
    }
}
```

#### Guid
```cs
string unique = Guid.NewGuid().ToString();
```

Guid는 GUID(Globally Unique Identifier)를 출력.
GUID 값은 실행할 때마다 동일한 값을 만날 확률이 0.

### 열거형
```cs
enum Animal { Mouse, Cow, Tiger }
```

상수로만 구분하면 어려우니까 이름을 붙여서 쓰는 느낌.
각각 Mouse: 1, Cow: 2, Tiger: 3으로 되어있다.
초기화 시키면 그 다음부터의 상수값도 바뀐다.

```cs
Animal animal = Animal.Dragon;
int num = (int)animal;
string str = animal.ToString();
```

이러면 num은 상수값, str은 Dragon이 된다.
열거형 값은 변환하는대로 변환된다.

```cs
Animal animal = Animal.Dog;

switch (animal)
{
	case Animal.Chicken:
		break;
	case Animal.Dog:
		break;
}
```

switch 문과 같이 사용하면 유용하다.

### TryParse() : 변환 시도하고 안되면 기본값
```cs
public static bool TryParse(string s, out DateTime result)
```

### GetType() : 자료형 확인
```cs
> "ABC".GetType()
[System.String]
> "ABC[0].GetType()
[System.Char]
```

### 자료형 기본값으로 초기화
```C#
> int i = default;
> string s = default;
> $"[{i}] [{s}]"
[0], []
```
변수를 선언하고 초기화할 때 C#에서 기본으로 제공하는 값으로 초기화하고 싶다면  default 키워드를 사용하면 된다.


## 문법
---

### 변수 선언 방식
```cs
int a, b, c; // 데이터 형식 동일한 변수 여러개 한꺼번에 선언
int a = 10, b = 20, c = 30;
a = b = c = 10; // 변수 여러개 동일한 값으로 초기화
```

### 전위 연산자, 후위 연산자

| 구분 | 설명 | 예 |
| ---- | ---- | ---- |
| 전위(prefix) 증감 연산자 | 정수형 변수 앞에 연산자가 위치하여 변수 값을 미리 증감한 후 나머지 연산을 수행 | ++a;<br>--b; |
| 후위(postfix) 증감 연산자 | 정수형 변수 뒤에 연산자가 위치하여 연산식(대입)을 먼저 실행한 후 나중에 변수 값을 증감 | a++;<br>b--; |
```C#
a = a + 1;
a += 1;
++a; // 세 개의 구문은 모두 기능이 동일하다.
```

```C#
> int i = 3;
int j = ++i; // 전위 연산자는 해당 라인에서 실행 우선 순위가 가장 높음

> int i = 3;
int j = i++; // 후위 연산자는 해당 라인에서 대입 연산자보다 우선순위가 낮음
```

### 삼항 연산자
```C#
조건식 ? 식1 : 식2; // 참이면 식1이 실행, 거짓이면 식2가 실행
조건식 ? 값1 : 값2; // 참이면 값1, 거짓이면 값21
```

### 제어문 종류 : if, while, goto 등

| 제어문 | 종류                                                                                                                                    |
| --- | ------------------------------------------------------------------------------------------------------------------------------------- |
| 조건문 | if 문 : 조건 하나 비교<br>else 문 : 조건 분기<br>switch 문 : 다양한 조건                                                                                |
| 반복문 | for 문 : 구간 반복<br>do 문 : 선행 반복<br>while 문 : 조건 반복<br>foreach 문 : 배열 반복                                                                 |
| 기타  | break 문 : 반복문 내에서 반복 중지<br>continue 문 : 반복문 내에서 그다음 반복문 이동<br>goto 문 : C#에서 자주 사용하진 않지만, <br>레이블(레이블 이름과 콜론(:)으로 만듦)로 지정된 곳으로 직접 이동시킴 |
### for문
```cs
for(초기식; 조건식; 증감식)
{
	실행문;
}
```

### Switch 문
```c#
switch(표현식)
{
	case 값1: 실행문1; break;
	case 값2: 실행문2; break;
	...
	case 값n: 실행문n; break;
	default: 실행문; break;
}
```

표현식의 결괏값이 '값1'이면 '실행문1' 수행. 
case 레이블에는 상수(값)가 들어오고, default 레이블은 생략 가능.

### do while
```cs
do
{
	실행문;
} while (조건식);
```

문장을 한 번 실행 후 조건을 따진다

### foreach
```cs
foreach(데이터형식 항목 in 항목들)
{
	문장; //변수에 들어 있는 값을 사용하는 문장이 온다
	
}
```

컬렉션 형식에서 데이터를 하나씩 꺼내면서 반복

### goto
```cs
if (chapter == 1)
	goto Chapter1;
else
	goto Chapter2;

Chapter1:
Console.WriteLine("1장");
Chapter2:
Console.WriteLine("2장");
```

특정 레이블로 이동하는 기능

### 화살표 함수 (람다식) : 메서드 코드 줄이기
```cs
class ArrowFunction
{
    static void Main()
    {
        Hi();
        Multiply(3, 5);
    }

    static void Hi() => Console.WriteLine("안녕하세요.");
    static void Multiply(int a, int b) => Console.WriteLine(a * b);
}
```

화살표 연산자 (=>) 를 사용하여 메서드 코드를 줄일 수 있다.

### 문자열 입력

- Console.ReadLine(): 콘솔에서 한 줄을 입력받는다.
- Console.Read(): 콘솔에서 한 문자를 정수로 입력받는다.
- Console.ReadKey(): 콘솔에서 다음 문자나 사용자가 누른 기능 키를 가져온다.

```C#
Console.WriteLine(Console.ReadLine()) // 콘솔에서 입력한 값을 그대로 출력

string num = Console.ReadLine();
Console.WriteLine(num); // 콘솔에서 입력한 값을 변수에 저장 후 출력
```

```C#
int x = Console.Read();
Console.WriteLine(x); // A를 입력했다면 A에 해당하는 정수 값 65 출력
Console.WriteLine(Convert.ToChar(x)); // 65에 해당하는 유니코드 문자 출력
```
Console.Read() 메서드를 사용하면 콘솔에서 문자를 하나만 입력받을 수 있음. 입력 값은 우리가 입력한 값과 다르게 문자에 해당하는 정수로 반환됨. 정수에 해당하는 문자를 출력할 때는 Convert.ToChar() 메서드 사용.

### Console.WriteLine() : 명령줄 출력
```cs
Console.WriteLine() // 명령 프롬프트에서 한 줄씩 출력
Console.Write() // 자동으로 줄 바꿈 하지 않고 출력
```

### 여러 문자열 합쳐서 출력

**자료 표시자**
```C# 
Console.WriteLine("{1}, {0}", "Hello", "C#");
```
프로그램 실행 결과를 화면에 출력할 때 사용하는 출력문 등에서 자리 표시자(틀) 개념을 이용해서 출력 서식을 지정할 수 있다. {n} 형태로 {0}, {1}, {2} 순서대로 자리를 만들고 그 다음에 있는 값을 차례로 넘겨받아 출력한다.

**String.Format() 메서드**
```C#
string msg = string.Format("{0}님, {1}", "백승수", "안녕하세요.")
Console.WriteLine(msg);
```
String.Format()은 Console.WriteLine() 메서드처럼 {0}, {1}, {2}, 순서대로 뒤에서 오는 문자열을 채워 문자열로 반환해 준다.

**문자열 보간법 ★ // 책 저자가 추천**
```C#
int number = 3;
string result = "홀수";
Console.WriteLine($"{number}은 {result}입니다.");
```
자리 표시자 대신 직접 특정 변수 값을 중괄호 기호로 표현할 수 있다. 이때 문자열 앞에는 $ 기호가 와야 한다.

### 변수?.멤버 : null 체크하며 멤버나 메서드 접근
```cs
ListNode l1 = null;
Console.WriteLine(l1?.next); // 출력: null (예외 발생하지 않음)

ListNode l2 = new ListNode(1);
Console.WriteLine(l2?.next); // 출력: null (l2.next는 null)
```

이 연산자는 객체가 `null`인지 확인한 다음, 
안전하게 멤버 또는 메서드에 접근하도록 도와준다.
nullref 피할 수 있음.

### 튜플 리터럴
```C#
> var t = (100, 200);
> Console.WriteLine(t.Item1);
100
> Console.WriteLine(t.Item2);
200
```

 var 키워드로 변수를 선언한 후 괄호에 콤마를 구분해서 숫자 데이터를 넣으면 자동으로 t.Item1, t.Item2의 형태로 값이 저장되어 그 값을 사용할 수 있다.
 
```C#
> var (x, y) = (300, 400);
> Console.WriteLine($"{x}, {y}");
300, 400
```

자동 생성되는 형태를 사용하지 않고 변수 여러 개를 괄호 안에 선언하여 사용할 수 있다.

### nameof() : 클래스, 메서드 이름을 문자열로 가져오기
```cs
> nameof(System)
"System"
> nameof(Console.WriteLine)
"WriteLine"
```



## 구현
---





