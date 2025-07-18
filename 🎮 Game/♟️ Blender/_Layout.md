- [[#📌 Tip|📌 Tip]]
- [[#🚀 Shortcut|🚀 Shortcut]]
- [[#⚙️ Preference|⚙️ Preference]]
- [[#🐵 Add|🐵 Add]]
- [[#🕹️ Transform|🕹️ Transform]]
- [[#🧊 Object|🧊 Object]]
- [[#✂️ Edit|✂️ Edit]]
- [[#🦴 Rigging|🦴 Rigging]]
- [[#🔭 View|🔭 View]]
- [[#🔧 Modifier|🔧 Modifier]]
- [[#🔨 Physics|🔨 Physics]]
- [[#🎥 Camera|🎥 Camera]]
- [[#🎬 Animation|🎬 Animation]]
- [[#➕ Add-on|➕ Add-on]]
- [[#🪄 Optimization|🪄 Optimization]]
- [[#📤 Export|📤 Export]]
- [[#🦫 Troubleshooting|🦫 Troubleshooting]]
	- [[#🦫 Troubleshooting#Pan View가 안됨|Pan View가 안됨]]
	- [[#🦫 Troubleshooting#빛 추가했는데 반영이 안됨|빛 추가했는데 반영이 안됨]]
	- [[#🦫 Troubleshooting#Subdivision Surface 쭈글쭈글|Subdivision Surface 쭈글쭈글]]
	- [[#🦫 Troubleshooting#Add-ons에 검색했는데 안 나오는데|Add-ons에 검색했는데 안 나오는데]]
	- [[#🦫 Troubleshooting#복사하면 피직스 물리 엔진 반영 풀려|복사하면 피직스 물리 엔진 반영 풀려]]
	- [[#🦫 Troubleshooting#가로 루프가 마음대로 선택 안돼|가로 루프가 마음대로 선택 안돼]]
	- [[#🦫 Troubleshooting#Simple Deform 왜 원기둥 안됨|Simple Deform 왜 원기둥 안됨]]
	- [[#🦫 Troubleshooting#머테리얼 적용했는데 왜 안 보임|머테리얼 적용했는데 왜 안 보임]]
	- [[#🦫 Troubleshooting#Physics 적용했는데 왜 위로 감|Physics 적용했는데 왜 위로 감]]
	- [[#🦫 Troubleshooting#Physics 적용한거 옮겼더니 찌그러짐|Physics 적용한거 옮겼더니 찌그러짐]]
	- [[#🦫 Troubleshooting#Cloth 적용했는데 왜 옷감처럼 안 구겨짐|Cloth 적용했는데 왜 옷감처럼 안 구겨짐]]
	- [[#🦫 Troubleshooting#빛 추가했는데 안 보임|빛 추가했는데 안 보임]]
	- [[#🦫 Troubleshooting#왜 오브젝트들 transform이 sync됨|왜 오브젝트들 transform이 sync됨]]
	- [[#🦫 Troubleshooting#유니티로 export 했더니 안이 비쳐보임|유니티로 export 했더니 안이 비쳐보임]]
	- [[#🦫 Troubleshooting#리깅이 모델이 묻혀서 안 보임|리깅이 모델이 묻혀서 안 보임]]
	- [[#🦫 Troubleshooting#왜 나는 리깅해도 안 구부러짐|왜 나는 리깅해도 안 구부러짐]]
	- [[#🦫 Troubleshooting#Insert Keyframe Menu 왜 안 뜸|Insert Keyframe Menu 왜 안 뜸]]
	- [[#🦫 Troubleshooting#외부 모델 Import 했더니 보라색|외부 모델 Import 했더니 보라색]]
	- [[#🦫 Troubleshooting#마우스 커서 위에 동그라미 생기고 pan 이동도 안됨|마우스 커서 위에 동그라미 생기고 pan 이동도 안됨]]
	- [[#🦫 Troubleshooting#유니티로 export 했더니 내부 면이 안 보임|유니티로 export 했더니 내부 면이 안 보임]]
	- [[#🦫 Troubleshooting#Curve Modifier 했더니 크기가 너무 커짐|Curve Modifier 했더니 크기가 너무 커짐]]



### 📌 Tip

- 커브 작업할 때 잘 안 보이면 : Properties > Object Data > Geometry > Bevel > Round > Depth
- 수직 수평 루프 선택 방법 : 누른 면 위치에 따라 달라진다
- Segments 조절하면 용량 많이 드니까 Subdivision Surface 사용
- 평면에서 Mirror로 입체감 주고 나면 안에 있는 **면**들 x-ray로 삭제해줘야 함
- Ctrl + A > Scale로 크기 값 1로 초기화해야 하는 경우
	- 리깅(Armature) 후 애니메이션 적용 시 → Bone이 이상하게 움직일 수 있음
	- Modifiers 사용 시 (예: Bevel, Mirror, Boolean 등) → 이상한 크기로 적용될 수 있음
	- Physics(물리 엔진, Cloth, Rigid Body 등) 적용 시 → 물리 시뮬레이션이 이상하게 작동할 수 있음
	- Unity로 내보낼 때 (FBX Export) → 크기, 애니메이션이 꼬일 가능성이 높음
- N > View > 3D Cursor에서 커서의 Location을 설정할 수 있다
- 노말 확인 : Blender 우측 상단 원 두개 겹친 아이콘 (Overlay) > Face Orientation 켜기
- edge 선택하고 f 연속으로 누르면 그 방향대로 계속 채워짐

### 🚀 Shortcut

- 모든 가능 작업 검색 : F3

- 이전 작업 반복 실행 : Shift + R
- 오브젝트 가리기 : H
- 가렸던 오브젝트 전부 보이게 하기 : Alt + H

- 

- 다른 이름으로 저장 : Shift+Ctrl+S

### ⚙️ Preference

Edit > Preference에 있는 설정들

- 오브젝트 중심 회전 : Navigation > Orbit & Pan > Orbit Around Selection 체크



### 🐵 Add

이미지 불러오기 : Object Mode > Header > Add > Image > Reference

Curve
- 모양 편집 : Edit 모드에서 점 선택하고 G로 옮기기
- 자유 선 그리기 : Edit 모드 화면 왼쪽 Draw 도구
- 포토샵 패스 선 그리기 : 화면 왼쪽 Curve Pen
- 점 삭제 : 점 선택 > X > Vertices
- 점 돌출 : E 또는 화면 왼쪽 Extrude
- 점 5개 직선 패스선 생성 : Object Mode > Shift + A > Curve > Path


### 🕹️ Transform

- Move : G
- Rotate : R
- Scale : S

- 축이 나옴 : Header 패널 > Gizmo > Object Gizmo > Move, Rotate, Scale
- 한 축 제외 : Shift + x,y,z
- 수치로 조절 : G,R,S + 숫자
- 스냅 기능 : Ctrl 누르고 이동
- 스냅 기능 (스냅) : Shift + Tab
- 스냅 이동 (3D Cursor, Grid, Object) : Shift + S
- Snap Base : G > B > 붙일 점 클릭 > 이동
- 단축키 도움말 : 하단

- Transform Pivot Point : 축의 위치 설정, `.`, 상단 링크 아이콘
- Transform Orientation : 좌표계 설정, `,`, 상단 축 아이콘
- Propositional Editing : 주변 오브젝트 영향 미칠건지, `O`, 상단 봉우리 아이콘

### 🧊 Object

Object Mode에서만 작동하는 것들

- 오브젝트 추가 : Sfhit + A

- 3D Cursor : 십자 표시, 오브젝트를 생성하는 기준, 이동 : Shift + 우클
- Origin : 주황 점, 크기 위치 회전 중심축
	- Object 모드에선 같이 움직이고, Edit 모드에선 안 움직임
	- 이동 : 우클 > Set Origin, 오브젝트 모드 이동 : Ctrl + `.` > G
- 부모 설정 : 부모로 만들 오브젝트 마지막에 선택 > Ctrl + P > Object
- 링크 설정
	- 오브젝트들 선택 > Ctrl + L > Link Object Data
	- Object 모드에선 영향 안 받음, Edit Mode에선 서로 영향 받음

### ✂️ Edit

Edit Mode에서만 작동하는 것들

- 1,2,3 : Select Mode 변경
- 지나오는 점 전부 선택 : Ctrl + 클릭
- 한 칸 걸러 선택 해제 : 좌측 상단 Select > Checker Deselect
- 연결된 버텍스 선택 : L

- 중심점 기준 x,y,z 이동 : G > X,Y,Z > X,Y,Z
- 엣지 기준 슬라이드 이동 : G 두번

- 오브젝트 합치기 : Ctrl + J
- 다른 객체로 분리하기 : 면 선택 > P > Selection
- 같은 객체인 상태로 분리 : Y
- 선 생성 : K, 엔터 눌러서 확정
- 각진 부분 부드럽게 : Ctrl + B

- 점 여러개 잇기 : 우클 > Connect Vertex Path 위아래 있는 것들 or Header > Vertex > Connect Vertex Path
- 구멍 메우거나 선 만들기 : F
- 점, 선, 면 합치기 : M
- 면 안에 새 면 만들기 : I
	- I 또 누르면 개별적으로 면 만들지 따로 만들지
- 표면에 선 나누기 : Ctrl + R, 마우스 휠 돌려서 개수 결정

- 기본 돌출 : E
- 면을 나누지 않고 돌출 : Alt + E
- 선택한 요소의 Normal 방향으로 돌출 : Alt + E
- 루프 만들기 : Ctrl + R
- 두께 주기 : Header > Face > Solidify Faces

- 법선 방향 기준 면 수축 또는 팽창 : Alt + S

- 선 루프 합치기 : (같은 오브젝트의) 루프  2개 선택 > Ctrl + E > Bridge Edge Loops
- 면 대각선 2개로 나누기 : Header > Face > Poke Faces
- 전체 면을 삼각형으로 변형 : Ctrl + T (루프 선택 어려워짐)
- 일부 면을 사각형으로 변형 : Header > Face > Tris to Quads

원 만들기
- LoopTools > Circle
- 점 하나 선택 > Shift+Ctrl+B (Bevel) > Segment 조절

Tip
- Bevel 했는데 기울어져서 나눠짐 : 오브젝트 모드 > Ctrl + A > Scale


### 🦴 Rigging

- 리깅 거울 : Header > 나비 모양 아이콘 > X > 뼈 선택하고 Shift + E
- 리깅 뒤집기 : 다 선택 > Alt + F
- 부모 연결 : Ctrl + P
- 부모 끊기 : Alt + P

뼈 연결
1. 연결할 오브젝트 선택
2. Shift 누른 상태로 Armature 선택
3. Ctrl + P > Armature Deform > With Automatic Weights

### 🔭 View

- 뷰포트 단축키 : `~`
- Vieport Shading : Z

- Camera View 활성화 : 숫자 키패드 0

- 한 오브젝트만 보이게 : `/`
- X-Ray : Alt+Z

- 앞면 뒷면 구분 : Viewport Overlays (우측 상단 원 2개 겹친 아이콘) > Face Orientation

### 🔧 Modifier

- Subdivision Surface : Ctrl + 1~6, 메시를 부드럽게 만들어준다
	- Mean Crease : 특정 엣지는 날카롭게 유지
- Decimate : 메시를 단순하게 만들어준다
- Bevel : 오브젝트에 추가 폴리곤을 넣어 부드럽게 만든다

- Mirror : Origin을 중심으로 한쪽 편집할 때 반대편이 동일하게 수행
	- Clipping : 중첩된 오브젝트가 통과되지 않고 서로 겹치지 않음
	- Mirror Object : 대칭할 때 어떤 오브젝트를 대상으로 할지
- Boolean
	- Intersection : 두 부분이 겹치는 공통된 부분만 남는다
	- Union : 두 오브젝트 합치기 (내부 면 삭제, 물리 시뮬 시 하나로 인식)

- Array : 오브젝트를 여러 개 복제하여 배열 형태로 배치
- Curve : 오브젝트의 형태를 곡선으로 변형함 (적용할 형태는 Curve여야 함)
- Screw : 나선 모양의 입체 만듦
- Shirinkwrap : 오브젝트를 다른 오브젝트의 표면에 달라붙게 함

### 🔨 Physics

- Cloth
	- Self Collisions : 천이 자기 자신과 겹치는 현상 방지

### 🎥 Camera

- 카메라 보이는 각도 조절 : 숫자 키패드 0 > N > View > Camera to View > 스크롤 눌러 시점 이동

### 🎬 Animation

- Ctrl + Tab : Pose Mode

키프레임 추가
- 재생 바 좌측의 'Auto Keying' 활성화 : 속성 조작하면 Keyframe 생겨남
  - 애니 편집 다 끝나면 옵션 꺼주기. 안 그러면 다른 거 조작하는 거 다 키프레임에 추가된다.
  - 아무 이동도 안 하고 Transform 키프레임 추가하려면 G만 누르고 바로 클릭
- 전체 추가 : 오브젝트 선택하고 `I`, 
- 옵션 선택 : 오브젝트 선택하고 `K`
- 특정 속성 : N > Item > 속성에 대고 `I`
- Shader Editor 등에서도 속성 추가 가능 (Unity에서는 의미 없지만) (해당 속성을 클릭해야 프레임 속성이 뜬다)

키프레임 조작
- G : 시점 이동, X : 삭제, Shift + D : 복사
- 키프레임 사이에 연결된 선 의미 : 둘이 같다. 변경점이 없다. (블렌더 버전 올라오면서 '같다'는 기준이 빡세진듯. Hierarchy를 열어야 이어진게 보인다.)
- 키프레임 수정 : 특정 속성만 바꾸고 같은 종류 키프레임 추가로 Override 가능

Graph Editor
- 그래프 비율 확대 축소 : 휠 누르고 드래그
- X축이나 Y축 고정시키며 이동 : G > 휠 클릭
- 그래프에 붙은 Handle로 전환 속도 조절
- Handle 종류 변경 : T

타임라인 조작
- 재생 바 : 뒤로 재생, 이전/다음 키프레임으로 이동, 시작/마지막 프레임 이동
- 우측 상단 Start, End : 애니 프레임 시작/끝 시점 결정
- Frame rate : Game용은 30fps이 국룰인듯


### ➕ Add-on

- `LoopTools` : 루프와 관련된 작업을 쉽게 수행
- `Node Wrangler` : Shader Editor 패널에서 노드 작업 빠르고 효율적으로
- `Extra Curve Objects`, `Extra Mesh Objects` : 추가 도형 제공

- `Bool Tools`
	- Boolen 효과 : 뺄 거 선택 > Shift 누르고 빼질 거 선택 > Ctrl + Numpad `-`

- `BlenderKit` : blender kit 플랫폼 자료들을 블랜더에서 바로 다운 바로 사용

### 🪄 Optimization

- A로 모든 점 선택 > M > By Distance : 겹치는 점 병합
- A로 모든 점 선택 > Backsapce > Limited Dissolve


### 📤 Export

Unity에서 머테리얼 인식시키기
- 텍스쳐는 따로 넣어줘야 된다?? << 조사해볼 것
- Unity는 FBX 모델의 "머티리얼 이름"과 "머티리얼 파일명"이 일치하면 자동으로 공유함
- `Shading` 탭에서 모든 오브젝트에 같은 머티리얼 사용하기
- Blender에서 같은 이름의 머티리얼을 사용하면 Unity의 특정 머테리얼도 사용 가능

텍스쳐 이미지 export
- render property 이동
- render engine을 Cycles로 변경 
- Baked > Combined에서 Diffuse로 변경 
- Influence > Contributions > Direct, Indirect 체크 해제
- Shader to RGB 노드 등 EEVEE 전용 노드는 제거
- material output 전에 diffuse bsdf 노드 경유하게 추가
- 이미지 노드 하나 꺼내서 선택 
- Bake

### 🦫 Troubleshooting

#### Pan View가 안됨
오브젝트 모드로 가서 Home 누르셈

#### 빛 추가했는데 반영이 안됨
Power를 좀 더 올려보셈

#### Subdivision Surface 쭈글쭈글
오류가 생기는 부분 살짝 위에 Ctrl+R로 선 하나 추가하셈

#### Add-ons에 검색했는데 안 나오는데
Get Extensions에서 검색해

#### 복사하면 피직스 물리 엔진 반영 풀려
Modifier Apply 후 복사

#### 가로 루프가 마음대로 선택 안돼
원하는 방향 변에 대고 선택해야됨
Alt + 클릭을 해당 면의 여러 곳에 시도

#### Simple Deform 왜 원기둥 안됨
Twist가 아니라 Bend로 돼있어야지

#### 머테리얼 적용했는데 왜 안 보임
뷰포트를 Material Preview로 바꾸셈

#### Physics 적용했는데 왜 위로 감
애니메이션이 적용돼버려서 그럼. 0으로 옮겨보거나 중력을 끄셈.

#### Physics 적용한거 옮겼더니 찌그러짐
모디파이어에서 apply 하셈

#### Cloth 적용했는데 왜 옷감처럼 안 구겨짐
Subdivide 하셈, Pressure 푸셈

#### 빛 추가했는데 안 보임
뷰포트를 Rendered로 바꾸셈

#### 왜 오브젝트들 transform이 sync됨
Propositional Editing 끄셈

#### 유니티로 export 했더니 안이 비쳐보임
Overlays에서 Face Orientation 켠 다음 Shift + N으로 노말 뒤집으셈

#### 리깅이 모델이 묻혀서 안 보임
Armature 탭 (뼈다귀 아니라 포즈 아이콘) > Viewport Display > In Front, Axes 체크

#### 왜 나는 리깅해도 안 구부러짐
구부러질 수 있게 Ctrl+R로 루프 쪼개셈

#### Insert Keyframe Menu 왜 안 뜸
오브젝트 누르고 K 눌러야 됨 (I도 키프레임 넣는거고 이것도 키프레임 넣는거)

#### 외부 모델 Import 했더니 보라색
File > External Data > Find Missing Files > 텍스처 폴더 들어가서 확인 

#### 마우스 커서 위에 동그라미 생기고 pan 이동도 안됨
w 누르셈

#### 유니티로 export 했더니 내부 면이 안 보임
유니티 > 머테리얼 > Render Face > Both

#### Curve Modifier 했더니 크기가 너무 커짐
두 물체 origin을 가까이 하셈
