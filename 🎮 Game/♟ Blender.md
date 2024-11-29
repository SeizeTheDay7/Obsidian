

## 단축키

`키패드 5` : 시점 변경 (Perspective, Orthographic : 원근감, 공간감 없음)
	










[Beginner Blender 4.0 Tutorial Part 1](https://www.youtube.com/watch?v=B0J27sf9N1Y&list=PLjEaoINr3zgEPv5y--4MKpciLaoQYZB1Z&index=2)

시점 이동 방법
휠 버튼+이동
Shift+휠 버튼+이동

오브젝트 추가 단축키 : Shift + A

오브젝트 선택하고 g 누르면 마우스에 붙어서 이동
오브젝트 선택하고 x,y,z 누르면 각 축에 붙어서 이동

F12 이미지 렌더
화면 우측 카메라 아이콘 (혹은 0) : 카메라 시점

카메라 뷰에서 우측 상단에 있는 것들은 카메라에 담기는 물체들
이때 물체를 선택하고 N을 누르면 Properties 나온다

크기 조절 : Scale 툴에서 s 누르기

카메라 누르고 R 누르면 시점 각도 돌릴 수 있고, R 한 번 더 누르면 시점 자체가 돌아감


[Beginner Blender 4.0 Tutorial Part 2 : Basic Modelling](https://www.youtube.com/watch?v=tBpnKTAc5Eo&list=PLjEaoINr3zgEPv5y--4MKpciLaoQYZB1Z&index=2)

우클릭 - Shade Smooth : 부드럽게 렌더해줌
우클릭 - Shade Flat : 각지게 보임

우측 하단 - 랜치 모양 - Add Modifier - Generate - Subdivision Surface : 매우 자주 쓰이는 Modifier. 각 면에 대한 평균점으로 면을 또 나눠서 부드럽게 만든다
Levels Viewport : 작업할 때 보이는 쪼개기
Render : 렌더하고 나서 보이는 쪼개기

오브젝트에서 Edit Mode 들어가면 점 선 면 편집할 수 있다.
점 누르고 G 누르면 점이 마우스 따라 움직인다.
Tab을 통해 Object Mode와 Edit Mode를 오갈 수 있다.

화면 상단에 있는 ![[Pasted image 20240114183153.png]] (Propositional Editing) 누르면 점 일일이 옮기지 않아도 점 하나만 옮길 때도 다른 점들도 같이 움직인다. 스크롤 휠을 조절하여 Propositonal Editing의 영향을 받는 영역도 조절할 수 있다.

**점 하나 누르고 Alt 누르면서 다른 점 클릭하면 해당 선 전부 클릭해준다.**

s를 누르면 scale을 조절할 수 있다.


[Beginner Blender 4.0 Tutorial Part 3 : Modelling the Icing](https://www.youtube.com/watch?v=AqJx5TJyhes&list=PLjEaoINr3zgEPv5y--4MKpciLaoQYZB1Z&index=3)

Shift+D 누르면 오브젝트 복사. 그 상태에서 우클릭이나 Esc 누르면 같은 위치에 복사.

Edit Mode에서 그냥 드래그하면 카메라에 보이는 부분만 선택됨.
이 때 화면 우측 상단에 있는 ![[Pasted image 20240114174107.png]] (Toggle X-ray)를 누르면 가려지는 부분도 전부 선택 가능.

Solidify Modifier는 오브젝트의 두께를 늘린다
offset을 조절하여 어느 방향으로 늘릴지 고를 수 있다

화면 상단에 있는 ![[Pasted image 20240114175411.png]] (Snap) 을 누르면 스냅하여 이동할 수 있다.
Snap To를 Face로 바꾸면 선택한 점이 아래의 면을 따라 움직이고,
![[Pasted image 20240114180128.png]]
Snap 설정에서 이걸 선택하면 Propositional Editing할 때 다른 점들도 같이 면을 따라 움직인다.
![[Pasted image 20240114182240.png]]
Issue : Solidify Modifier가 Edit Mode에서 보이게 설정되어 있어서 Subdivision Modifier Apply 후 Edit Mode로 돌아왔더니 Vertices가 안 보임. Solidify를 잠시 끄면 해결됨.

점 클릭 + Alt + 다른 점 클릭으로 선을 선택했을 때 Ctrl + '+'를 누르면 그 다음 선들이 선택된다.

영역을 선택하고 H를 누르면 잠시 숨겨진다.
Alt + H를 누르면 다시 나타난다.

움직일 때 가운데 버튼 누르면 축에 맞추어 움직이게 할 수 있음

Modifier는 정렬 순서에 따라 적용된다.

Solidify Modifier - Edge Data - Crease Inner를 조절하여 도넛 아이싱 끝 부분을 안으로 숨겨 부드럽게 만듬

선을 선택하고 E를 누르면 Extrude(돌출)시킬 수 있다. 즉, 선을 하나 추가한다.


[Beginner Blender 4.0 Tutorial Part 4 : Sculpting](https://www.youtube.com/watch?v=AqJx5TJyhes&list=PLjEaoINr3zgEPv5y--4MKpciLaoQYZB1Z&index=4)

Edit Mode에서는 Precise한 변형을 가한다면,
Sculpt Mode에선 좀 더 광범위하고 자연스러운 변형을 가할 수 있다.

F : 도구 크기 바꾸기
Shift + F : 도구 Strength 바꾸기

Subdivision Modifier를 Apply할 땐 Render는 안 쓰고 Levels Viewport만 쓴다.

Sculpt 하기 전에 Subdivision Modifier으로 detail한 vertices를 추가해줘야 한다

Sculpt Mode - Inflate - 

Sculpt Mode 도구들
Inflate (단축키 I) : 키우고 싶은 부분에 작은 원 그리며 움직이기
Grab (단축키 G) : 살짝씩 뒤트는 도구
Mask (단축키 M) : 마스크 칠한 부분을 제외하고 Sculpt (Strength는 1.0으로 설정, Brush에서 Front Faces Only 선택)
Mesh filter : 원하는 필터를 모든 영역에 동일하게 적용할 수 있음
Smooth(Shift 꾹 누르고 있기) : 높낮이 자연스럽게 맞추는 도구

**오브젝트 선택하고 / 누르면 그 오브젝트만 볼 수 있다.**

Ctrl + i : 마스크 선택 영역 반전

Mask - Smooth Mask : 마스크 테두리 연하게


[Beginner Blender 4.0 Tutorial Part 5 : Shading](https://www.youtube.com/watch?v=AqJx5TJyhes&list=PLjEaoINr3zgEPv5y--4MKpciLaoQYZB1Z&index=5)

![[Pasted image 20240117232616.png]] Material 적용했는데 안 보인다면 우측 상단 4번째 아이콘

오브젝트 A (자녀) 선택하고 Shift 누르면서 오브젝트 B (부모) 선택한 뒤 Ctrl + P 누르면 하나로 묶어서 이동시킬 수 있다. Object (Keep Transform) 골라야 함.

이미지 텍스처 적용 : Material - New - Base Color - 노란 동그라미 - Image Texture (뷰포트 모드 4번째 걸로 바꿔줘야 적용된거 보임!)

화면 상단 Shading - Roughness 옆에 점 드래그하고 Image Color - Roughness 파일 적용 - Color Space - Non-Color 적용시키는 거 해봄

Normal 옆에 점 드래그하고 Image Color -  보라색 그림 적용 - Color Space - Non-Color - 사이에 이어진 선에 Shift+A - Vector - Normal Map

(하지만 방금 한 것들은 자신의 애드온을 사용하건 뭘 사용하건 보통 수동으로 일일이 연결하지는 않지만 알아두면 좋다~)

풀스크린 : Ctrl+Space 

Ctrl+P 해제 : 자식 오브젝트 선택 후 Alt+P

Normal Map의 어원은 Normal Vector가 어느정도인지를 지정하여서 그런것인듯?

화면 상단 Texture Paint - New - Color 선택 - 붓 색깔 바꾸고 칠하기 - 이렇게 만든 Texture는 저장하지 않으면 사라짐. 꼭 저장해야함.

