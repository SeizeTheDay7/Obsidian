- [[#📌 Tip|📌 Tip]]
- [[#🚀 Shortcut|🚀 Shortcut]]
- [[#⚙️ Preference|⚙️ Preference]]
- [[#🐵 Add|🐵 Add]]
- [[#🕹️ Transform|🕹️ Transform]]
- [[#🧊 Object|🧊 Object]]
- [[#✂️ Edit|✂️ Edit]]
- [[#🔭 View|🔭 View]]
- [[#🎥 Camera|🎥 Camera]]
- [[#🔧 Modifier|🔧 Modifier]]
- [[#🦫 Troubleshooting|🦫 Troubleshooting]]
	- [[#🦫 Troubleshooting#빛 추가했는데 반영이 안됨|빛 추가했는데 반영이 안됨]]
	- [[#🦫 Troubleshooting#Subdivision Surface 쭈글쭈글|Subdivision Surface 쭈글쭈글]]
	- [[#🦫 Troubleshooting#Add-ons에 검색했는데 안 나오는데|Add-ons에 검색했는데 안 나오는데]]
	- [[#🦫 Troubleshooting#복사하면 피직스 물리 엔진 반영 풀려|복사하면 피직스 물리 엔진 반영 풀려]]


### 📌 Tip

- 커브 작업할 때 잘 안 보이면 : Properties > Object Data > Geometry > Bevel > Round > Depth


### 🚀 Shortcut

- 이전 작업 반복 실행 : Shift + R
- 오브젝트 가리기 : H
- 가렸던 오브젝트 전부 보이게 하기 : Alt + H

- 

- 다른 이름으로 저장 : Shift+Ctrl+S

### ⚙️ Preference

Edit > Preference에 있는 설정들

- 오브젝트 중심 회전 : Navigation > Orbit & Pan > Orbit Around Selection 체크

애드온
- `Mesh: LoopTools` : 루프와 관련된 작업을 쉽게 수행
- `Node: Node Wrangler` : Shader Editor 패널에서 노드 작업 빠르고 효율적으로

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

원 만들기
- LoopTools > Circle
- 점 하나 선택 > Shift+Ctrl+B (Bevel) > Segment 조절
- 

### 🔭 View

- Vieport Shading : Z

- Camera View 활성화 : 숫자 키패드 0

- 한 오브젝트만 보이게 : `/`
- X-Ray : Alt+Z

### 🎥 Camera



- 카메라 보이는 각도 조절 : 숫자 키패드 0 > N > View > Camera to View > 스크롤 눌러 시점 이동

### 🔧 Modifier

- Subdivision Surface : Ctrl + 1~6


### 🦫 Troubleshooting

#### 빛 추가했는데 반영이 안됨
Power를 좀 더 올려보셈

#### Subdivision Surface 쭈글쭈글
오류가 생기는 부분 살짝 위에 Ctrl+R로 선 하나 추가하셈

#### Add-ons에 검색했는데 안 나오는데
Get Extensions에서 검색해

#### 복사하면 피직스 물리 엔진 반영 풀려
Modifier Apply 후 복사