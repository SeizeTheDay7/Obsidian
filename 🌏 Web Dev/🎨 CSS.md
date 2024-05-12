- [[#General|General]]
	- [[#General#화면 꽉 채우는 방법|화면 꽉 채우는 방법]]
	- [[#General#css 변수 선언|css 변수 선언]]
	- [[#General#CSS 상대 단위|CSS 상대 단위]]
		- [[#CSS 상대 단위#vh, vw, vmin : 화면 전체 상대 길이|vh, vw, vmin : 화면 전체 상대 길이]]
		- [[#CSS 상대 단위#em, rem : font-size 기준 크기|em, rem : font-size 기준 크기]]
- [[#중앙 정렬하는 방법|중앙 정렬하는 방법]]
- [[#margin|margin]]
- [[#Position|Position]]
- [[#::before와 ::after|::before와 ::after]]
- [[#Flexbox|Flexbox]]
- [[#Code Snippet|Code Snippet]]



## General
<hr>

○ img 태그는 style 생략하고 `width="100%"` 이런 식으로 넣어도 된다

### 화면 꽉 채우는 방법 
: `min-height: 100vh`

### CSS 변수 선언
```css
:root {
	--main-font-color: #000f22;  /* CSS 전역 변수 선언 */
}

div {
	left: calc(var(--left) * 1%);   /* CSS 변수 사용 */
}
```
변수 맨 앞에 `--`를 붙이면 변수 선언 된다. 변수 호출할 땐 var(변수명) 으로 사용한다.


### 배경 관련 속성
```css
background-image: url(../img/shoes.jpg);
background-size: cover;  /* 이미지 크기에 맞게 조절 */
background-repeat: no-repeat; /* 이미지 반복 없음 */
background-position: center; /* 이미지 중앙에 위치 */
background-attachment: fixed; /* 스크롤 시 이미지 고정 */
filter: brightness(70%); /* 이미지 어둡게 */
```
`background-size: cover` 빈 공간 없이 배경으로 꽉 채워라
`background-size: contain` 배경 짤리면 안된다

### CSS 상대 단위
<hr>

#### vh, vw, vmin : 화면 전체 상대 길이
`vh` : viewport height (100이 최대)
`vw` : viewport width
`vmin` : viewport minimum, 뷰포트의 높이와 너비 중 더 작은 길이
(%는 부모 요소의 길이에 연관됨)

#### em, rem : font-size 기준 크기
[정리글](https://www.daleseo.com/css-em-rem/)

**계산 방식**
1em = 16 px x 1 = 16px
2em = 16 px x 2 = 32px

`em` : 해당 단위가 사용되고 있는 요소의 font-size 값 기준 (font-size는 부모에게 상속받을 수 있음)
`rem` : 루트 요소 `<html>` 의 font-size 기준


## 중앙 정렬하는 방법
<hr>

1.
``` CSS
display:block; // div,p, h 등은 block 속성을 이미 갖고 있어서 생략 가능
translate(-50%, -50%)는 요소를 그의 X축과 Y축 위치에서 각각 50% 만큼 이동시킴.
position: absolute와 함께 사용하면 부모 컨테이너 내 중앙에 정확히 위치시킬 수 있음.
```


2.
``` CSS
margin-left: auto; 
margin-right: auto;
```


## margin
<hr>

[정리글](https://developer.mozilla.org/ko/docs/Web/CSS/margin)

> margin은 요소의 주위에 빈 공간을 추가하고,
> padding은 요소의 내부에 빈 공간을 만든다.

- **한 개의 값**은 모든 면의 여백을 설정.
- **두 개의 값**을 지정하면 첫 번째는 **위와 아래**, 두 번째는 **왼쪽과 오른쪽** 여백을 설정.
- **세 개의 값**을 지정하면 첫 번째는 **위**, 두 번째는 **왼쪽과 오른쪽,** 세 번째 값은 **아래** 여백을 설정.
- **네 개의 값**을 지정하면 각각 **상, 우, 하, 좌** 순서로 여백을 지정. (시계방향)

``` css
margin: 5%; /* 모두 5% */

margin: 10px; /* 모두 10px */

margin: 1.6em 20px;
/* 상하: 1.6em */
/* 좌우: 20px  */

margin: 10px 3% -1em;
/* 상: 10px */
/* 좌우: 3% */
/* 하: -1em */

margin: 10px 3px 30px 5px;
/* 상: 10px */
/* 우:  3px */
/* 하: 30px */
/* 좌:  5px */

margin: 2em auto;
/* 상하: 2em */
/* 수평 중앙정렬 */

margin: auto;
/* 상하: 0 */
/* 수평 중앙정렬 */
```

```CSS
margin-top: -25px;
margin-right: 10px;
margin-bottom: 30px;
margin-left: 100px;
```

## Position
<hr>

[정리글](https://creamilk88.tistory.com/197)

```css
.world {
	position : absolute; 
	// 문서 흐름에서 제거하여 가장 가까운 위치에 있는 조상 요소를 기준으로 배치
}
```

|데이터 유형|설명|
|---|---|
|static|기준 없음 (배치 불가능 / 기본값)|
|relative|요소 자기 자신을 기준으로 배치|
|absolute|부모(조상) 요소를 기준으로 배치|
|fixed|뷰포트 기준으로 배치|
|sticky|스크롤 영역 기준으로 배치|

## ::before와 ::after
<hr>

::before : 실제 내용 바로 앞에서 생성되는 자식요소  
::after : 실제 내용 바로 뒤에서 생성되는 자식요소​

::before와 ::after을 쓸 땐 content라는 속성이 필요함

| 속성      | 사용                            |
| ------- | ----------------------------- |
| normal  | 아무것도 표시하지 않는 기본값              |
| string  | 문자열 생성                        |
| image   | 이미지나 비디오를 불러올 수 있음. 크기 조절 불가능 |
| counter | 순서를 매길 수 있음.                  |
| none    | 아무것도 표시하지 않음                  |
| attr    | 해당속성의 속성값 표시                  |


## Flexbox
<hr>

[정리글](https://studiomeal.com/archives/197)

| justify-content | 요소를 가로선 상에서 정렬 |
| --------------- | -------------- |
| flex-start      | 왼쪽 정렬          |
| flex-end        | 오른쪽 정렬         |
| center          | 가운데로 정렬        |
| space-between   | 요소 사이에 동일한 간격  |
| space-around    | 요소 주위에 동일한 간격  |

| align-items | 요소를 세로선 상에서 정렬    |
| ----------- | ----------------- |
| flex-start  | 꼭대기로 정렬           |
| flex-end    | 바닥으로 정렬           |
| center      | 세로선 상의 가운데로 정렬    |
| baseline    | 시작 위치에 정렬         |
| stretch     | 요소들을 컨테이너에 맞도록 늘림 |

| flex-direction | 정렬 방향 지정         |
| -------------- | ---------------- |
| row            | 텍스트의 방향과 동일하게 정렬 |
| row-reverse    | 텍스트의 반대 방향으로 정렬  |
| column         | 위에서 아래로 정렬       |
| column-reverse | 아래에서 위로 정렬       |

| flex-wrap    | 몇 줄에 걸쳐 정렬할지 지정      |
| ------------ | -------------------- |
| nowrap       | 모든 요소들을 한 줄에 정렬      |
| wrap         | 요소들을 여러 줄에 걸쳐 정렬     |
| wrap-reverse | 요소들을 여러 줄에 걸쳐 반대로 정렬 |

> [!NOTE]
> `flex-flow`은 `flex-direction`과 `flex-wrap`을 묶어서 사용 가능
> 
> 예를 들어, `flex-flow: row wrap` 사용 가능

| align-content | 여러 줄 사이의 간격 지정      |
| ------------- | ------------------- |
| flex-start    | 꼭대기에 정렬             |
| flex-end      | 컨테이너의 바닥에 정렬        |
| center        | 세로선 상의 가운데에 정렬      |
| space-between | 여러 줄들 사이에 동일한 간격    |
| space-around  | 여러 줄들 주위에 동일한 간격    |
| stretch       | 여러 줄들을 컨테이너에 맞도록 늘림 |

>[!bug]
>부모 요소가 `display: flex`라면 `<button>`의 높이가 부모 요소와 같아지는 현상 발생.
>`<button>`에 `align-self: center` 적용시켜주면 정상화.

## Code Snippet
<hr>


``` css
* {
	box-sizing:border-box; // 테두리 포함한 크기 지정
	user-select: none; // 텍스트 선택 방지
}
```