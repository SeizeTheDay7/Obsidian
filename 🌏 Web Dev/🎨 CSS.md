# Flexbox
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
