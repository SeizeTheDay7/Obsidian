- [[#General|General]]
	- [[#General#열려있는 화면 전체의 상대 길이 지정|열려있는 화면 전체의 상대 길이 지정]]
- [[#Code Snippet|Code Snippet]]
- [[#::before와 ::after|::before와 ::after]]
- [[#Flexbox|Flexbox]]


## General
<hr>

화면 꽉 채우는 방법 : `min-height: 100vh`

### vh, vw, vmin : 화면 전체 상대 길이
`vh` : viewport height (100이 최대)
`vw` : viewport width
`vmin` : viewport minimum, 뷰포트의 높이와 너비 중 더 작은 길이
(%는 부모 요소의 길이에 연관됨)





## Code Snippet
<hr>

``` css
* {
	box-sizing:border-box; // 테두리 포함한 크기 지정
	user-select: none; // 텍스트 선택 방지
}
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


