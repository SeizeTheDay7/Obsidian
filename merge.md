
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
```html
.ani-text {
	transform: rotate(10deg);
	transform: translateX(100px);
}
```
rotate : 요소 회전
translateX : x축 좌표 이동 (애니메이션 줄 때 margin보다 부드럽게 이동)

#### transform: scale 주면 텍스트가 도망감
>[!bug]
>.ani-text {
  display: inline-block;
  transform: scale(2);
  transform-origin: center;
} 

