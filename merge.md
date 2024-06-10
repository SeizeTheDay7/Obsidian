
비디오 넣는 방법들
```html
<video src="bridge.mp4" controls></video>

/* 호환성 챙길 수 있음 (첫번째거 재생 안되면 두번째거 재생) */
<video controls autoplay muted preload="none">
  <source src="bridge.mp4" type="video/mp4">
  <source src="birdge-m.webm" type="video/mp4">
</video>
```
 controls : 재생됨 
 autoplay muted : 자동 재생
 poster="경로" : 썸네일 이미지
 loop : 무한반복

preload="none" 미리다운X
preload="auto" 미리다운O
preload="metadata" 미리다운 적당히


오디오 넣는 방법
```html
<audio src="bass.mp3" controls></audio>
```
muted : 음소거 상태로 시작
autoplay : 자동재생인데 javascript 만져야 가능 
preload : video와 동일


애니메이션 관련 속성들
```css
.ani-text {
	transform: rotate(10deg);
	transform: translateX(100px);
}
```
rotate : 요소 회전
translateX : x축 좌표 이동 (애니메이션 줄 때 margin보다 부드럽고 성능좋게 이동)

#### transform: scale 주면 텍스트가 도망감
>[!bug]
>.ani-text {
  display: inline-block;
  transform: scale(2);
  transform-origin: center;
} 

```css
@keyframes 왔다갔다 {
  0% {
    transform: translateX(0);
  }
  50% {
    transform: translateX(100px);
  }
  100% {
    transform: translateX(0);
  }
}

.ani-text:hover {
  animation: 왔다갔다 1s infinite;
}
```
@keyframe으로 복잡한 애니메이션 정의 가능

infinite : 애니메이션 계속 반복
forwards : 애니메이션 결과 유지

```
.box:hover {
  animation-name : 움찔움찔;
  animation-duration : 1s;
  animation-timing-function : linear; /*베지어 주기*/
  animation-delay : 1s; /*시작 전 딜레이*/
  animation-iteration-count : 3; /*몇회 반복할것인가*/
  animation-play-state : paused;  /*애니메이션을 멈추고 싶은 경우 자바스크립트로 이거 조정*/
  animation-fill-mode: forwards;  /*애니메이션 끝난 후에 원상복구 하지말고 정지*/
}
```
애니메이션 세부 속성


**성능 잡을 수 있는 여러 방법1. will-change 쓰면 됩니다.**

```
.box {
  will-change: transform;
} 
```

애니메이션을 주는 .box가 약간 느리게 동작한다면 

will-change : 애니메이션줄속성;

이걸 써놓으면 성능개선이 가능합니다. 바뀔 내용을 미리 렌더링해주는 속성이라 그렇습니다.
뭔가 이상하게 버벅일 때만 쓰시고 애니메이션이 스무스하게 잘 된다면 쓸 이유는 없습니다.
이상하게 많이 쓰면 브라우저 자체가 더 느려질 수 있습니다.

[https://dev.opera.com/articles/ko/css-will-change-property/](https://dev.opera.com/articles/ko/css-will-change-property/)


**성능 잡을 수 있는 여러 방법2. 하드웨어 가속**

애니메이션이 너무 많아 CPU만으로 전부 연산이 불가능하다면
GPU의 도움을 받을 수도 있습니다.

```
.box {
  transform: translate3d(0, 0, 0);
}
```

transform : translate3d를 쓰면 3D 이동도 가능한데
이 속성의 경우 GPU를 사용해서 연산하게 됩니다.
그래서 translate3d(0, 0, 0) 이런 식으로 아무데도 움직이지 않는 3D 이동명령을 주고
뒤에 필요한 transform을 더 적용한다면 
GPU를 이용해서 .box가 가진 transform 속성들을 연산할 수 있습니다. 
꼭 써야하는건 아니고 뭔가 느리게 동작한다면 써볼 수 있는 것들입니다.



```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 100px 100px;
  grid-gap: 10px;
}
.grid-container div {
  border: 1px solid black;
}

<div class="grid-container">
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
</div>
```
그리드 만들기 예제
- fr 써서 프레임 단위로 폭 지정 가능하다 (rows는 height가 있어야 fr으로 지정 가능)
- grid-gap으로 격자 사이 간격 지정 

```css
.grid-nav {
  grid-column: 1/5;
}

<div class="grid-container">
	<div class="grid-nav"></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
</div>
```
grid-column : 세로선 1 ~ 4 만큼 차지해주세요
gird-row : 가로선을 차지해주세요