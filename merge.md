
비디오 넣는 방법들
```html
<video src="bridge.mp4" controls></video>

/* 호환성 챙길 수 있음 (첫번째거 재생 안되면 두번째거 재생) */
<video controls autoplay muted preload="none">
  <source src="bridge.mp4" type="video/mp4">
  <source src="birdge-m.webm" type="video/mp4">
</video>
```
 controls 넣어야 재생됨 
 autoplay muted 넣으면 자동 재생됨

preload="none" 미리다운X
preload="auto" 미리다운O
preload="metadata" 미리다운 적당히