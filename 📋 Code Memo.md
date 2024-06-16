

### 3D 스타일 회전시키기 (HTML, CSS)

**transform을 쓰면 3D 스타일 회전이 가능합니다.** 

```
transform : rotateX(180deg);
transform : rotateY(180deg);
transform : rotateZ(180deg);
```

각각 X,Y,Z축 회전이 가능합니다. 

X축은 가로줄입니다. 그래서 rotateX()는 가로줄을 축으로 회전이 들어갑니다.

뭔소린지 모르겠으면 연필을 모니터에 가로로 대보십시오.

그리고 그 연필을 돌돌 말아봅니다. 그게 X축 회전, rotateX() 입니다.

아니면 직접 CSS로 박스나 글자를 rotateX() 줘보면 알 수 있습니다. 

Y축은 세로줄입니다. 모니터에 연필을 세로로 놓고 돌돌 말면 그게 Y축 회전입니다. 

Z축은 여러분 얼굴과 모니터 간의 가상의 선을 하나 그려보십시오. 

그 선을 회전시키면 그것이 Z축 회전입니다. 

Q. 그럼 위에 지금 돌아가고 있는 저 노란 사진은 무슨 축으로 회전하고 있는 것일까요? 

**step 1. 앞면과 뒷면 레이아웃을 각각 만들어줍니다.** 

```
<div class="flip-outer">
    <div class="flip-inner">
      <img src="profile.png" class="front">
      <div class="back">
        <h4>개발자 김철용</h4>
        <p>Frontend Developer</p>
      </div>
    </div>
 </div> 
```

앞면엔 사진, 뒷면엔 글씨 몇개를 집어넣고 싶어서 저렇게 했습니다. 

그리고 중요한건 flip-inner라고 작명한 앞뒷면 둘다 싸매는 박스를 하나 만들어줘야합니다. 

왜냐면

1. 마우스를 올리면 앞면과 뒷면을 각각 회전시키기 보다는 저 박스 전체를 회전시키면 편리하니까요.

2. 앞면과 뒷면은 position : absolute로 띄워야 앞뒤로 배치가 가능합니다. 그래서 position : relative를 어딘가에 줘야하는데 그걸 싸매는 박스에 주면 편리합니다. 

**step2. 앞면과 뒷면에 position : absolute를 줍니다.** 

```
(css파일)

.flip-outer {
  width: 300px;
  height: 300px;
}

.flip-inner {
  width: 100%;
  height: 100%;
  position: relative;
}

.front {
  width: 100%;
  position: absolute;
  z-index : 1;   //안나오면 이것도 추가
}

.back {
  width: 100%;
  position: absolute;
  transform: rotateY(180deg);
} 
```

absolute를 이용해서 앞뒷면으로 배치를 잘 한 모습입니다. 

앞면이 안보이면 앞면사진에 z-index : 1; 이것도 추가해봅시다.

그리고 뒷면은 rotateY(180deg)를 먼저 쥐어줍니다. 

그래야 최종완성본에서 **마우스를 올려 회전시켰을 때 제대로 글씨가 보이겠죠?** 

의심스러우면 이걸 빼고 한번 실험해봅시다. 

**step3. 마우스를 올렸을 때 Y축으로 180도 회전시키라고 애니메이션을 줍니다.** 

```
.flip-inner {
  width: 100%;
  height: 100%;
  position: relative;
  transition: all 1s;
  transform-style: preserve-3d;
}

.flip-inner:hover {
  transform: rotateY(180deg);
} 
```

hover시 Y축 180도 회전을 주라고 했습니다.

근데 애니메이션처럼 동작하도록 transition도 포함했습니다.

그리고 중요한건 transform-style: preserve-3d; 이 속성이 있어야 어떤 요소를 회전시킬 때 우리가 평소에 생각하는 3d 사물처럼 동작합니다.

**step4. 뒷면에 비치는 그림자를 안보이게 처리하려면** 

```
.front {
  backface-visibility: hidden;
} 
```

이런걸 추가해줍니다.

원래 어떤 HTML 요소를 뒤집으면 뒷면의 그림자가 보이는데 그걸 안보이게 처리해주는 명령어입니다.