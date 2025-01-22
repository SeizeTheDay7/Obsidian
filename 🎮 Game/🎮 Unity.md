- [[#⚙️ 설정|⚙️ 설정]]
	- [[#⚙️ 설정#🏷️ 성능|🏷️ 성능]]
		- [[#🏷️ 성능#수정 후 빠르게 재생|수정 후 빠르게 재생]]
	- [[#⚙️ 설정#🏷️ 디버그|🏷️ 디버그]]
		- [[#🏷️ 디버그#애셋 직렬화 방식 통일|애셋 직렬화 방식 통일]]
		- [[#🏷️ 디버그#프로젝트 렌더링 파이프라인 확인|프로젝트 렌더링 파이프라인 확인]]
- [[#💾 개념|💾 개념]]
	- [[#💾 개념#.meta 파일|.meta 파일]]
- [[#📋 정보|📋 정보]]
	- [[#📋 정보#🏷️ Script|🏷️ Script]]
		- [[#🏷️ Script#public vs [SerializeField]|public vs [SerializeField]]]
		- [[#🏷️ Script#private void vs void|private void vs void]]
	- [[#📋 정보#🏷️ UI|🏷️ UI]]
		- [[#🏷️ UI#EventSystem|EventSystem]]
- [[#🦫 디버깅|🦫 디버깅]]
	- [[#🦫 디버깅#🏷️ 인게임|🏷️ 인게임]]
		- [[#🏷️ 인게임#오브젝트들 전부 살짝 흐림|오브젝트들 전부 살짝 흐림]]
		- [[#🏷️ 인게임#Cinemachine 따라가기 덜덜 떨림|Cinemachine 따라가기 덜덜 떨림]]
		- [[#🏷️ 인게임#콜라이더 적용해도 벽뚫|콜라이더 적용해도 벽뚫]]
	- [[#🦫 디버깅#🏷️ UI|🏷️ UI]]
		- [[#🏷️ UI#9-slice 적용 안됨|9-slice 적용 안됨]]
	- [[#🦫 디버깅#🏷️ 협업|🏷️ 협업]]
		- [[#🏷️ 협업#깃 pull 할 때마다 메타파일 갱신|깃 pull 할 때마다 메타파일 갱신]]


# 📌 팁
---

- 프리팹 옆에 있는 화살표 누르면 프리팹 편집기로 바로 들어갈 수 있다.




## ⚙️ 설정
---

### 🏷️ 성능

#### 수정 후 빠르게 재생
Edit → Project Settings → Editor → Enter Play Mode Options


### 🏷️ 디버그

#### 애셋 직렬화 방식 통일
Edit - Project Settings - Editor - Asset Serialization - Force Text로 바꾸기

#### 프로젝트 렌더링 파이프라인 확인
Edit - Project Settings - Graphics - Scriptable Pipeline Settings 확인



## 🔍 Inspector
---

### Line Renderer
Scene Tools : 점 세개 누르면 점 옮기기
Positions : 정점 추가
중앙 빨간 선 : 폭 조절
Conrner Vertices : 모서리 둥글기
End Cap Vertices : 끝점 둥글기





## 💾 개념
---
### .meta 파일
컴포넌트 간의 연결과 같은 메타 정보들을 담고 있다.
유니티 에디터에서 파일 위치나 이름 바꾼거 아니면 이거 때문에 정보 소실.

깃허브에 커밋할 때 .meta 빠뜨리면 안되고
외부에 깃 말고 보낼 땐 .unitypackage로 만들어라.

### 재정의(override) 가능한 메서드
- 부모 클래스의 메서드가 `virtual`, `abstract`, 또는 `override`로 선언되지 않았다면, 자식 클래스에서 해당 메서드를 `override`로 재정의할 수 없습니다.
- Unity의 `Awake`는 기본적으로 MonoBehaviour의 메서드로 `virtual`이 아니므로, 재정의하려면 부모 클래스에서 `Awake`를 `virtual`로 명시해야 합니다.



## 📋 정보
---
### 🏷️ Script

#### public vs [SerializeField]
둘 다 Inspector 창에서 수정이 가능하지만, 
SerializeField는 외부 스크립트에서 수정할 수 없는 캡슐화가 이루어진다.

#### private void vs void
접근 제한자는 생략해도 되지만 가독성을 위해 명시적으로 추가하는게 좋다.

### 🏷️ Graphic

#### Mesh Renderer
- 기본 역할: 정적(Static) 또는 변형되지 않는 3D 메시에 대한 렌더링을 처리.
- 사용 예시: 건물, 바위, 가구 등 변형되지 않는 오브젝트.
- 특징:
  - Transform 컴포넌트로 위치, 회전, 크기만 변경 가능.
  - 메시의 정점(Vertex)이나 형태가 바뀌지 않음.
  - 단순한 렌더링 파이프라인을 사용하며, 계산량이 적음.
  - 머티리얼 및 셰이더와 호환성이 높음.
#### Skinned Mesh Renderer
- 기본 역할: 본(bone) 애니메이션에 따라 움직이는 3D 메시에 대한 렌더링을 처리.
- 사용 예시: 캐릭터, 몬스터, 애니메이션이 적용된 메쉬.
- 특징:
  - 본(Bone)과 스킨(메시) 시스템을 사용해 동적 변형을 처리.
  - 메시의 정점(Vertex)이 본 애니메이션에 따라 실시간으로 변형됨.
  - 복잡한 계산이 필요하며, GPU 연산을 많이 사용함.
  - 추가적인 데이터(본, 버텍스 웨이트 등)를 셰이더가 처리해야 하므로 셰이더 호환성 문제가 발생할 수 있음.

### 🏷️ UI
#### EventSystem
UI 추가하면 Canvas와 함께 씬에 추가되는 요소.
사용자 입력과 UI 요소를 이어주는 오브젝트이다.
EventSystem을 사용하면 입력 설정을 변경할 수 있다.








## 🦫 디버깅
---
### 🏷️ 인게임
#### 오브젝트들 전부 살짝 흐림
해상도를 Full HD로 바꾸고 1.5x로 돼있는 Scale을 1x로 바꾸기

#### Cinemachine 따라가기 덜덜 떨림
Rigidbody > Interpolation > Interpolate로 변경

#### 콜라이더 적용해도 벽뚫
Rigidbody > Collision Detection > Continous로 변경

#### 플레이어가 벽에 달라붙음
Physics Material 2D > Friction 0 > 적용

### 플레이어가 벽에 닿으면 계속 점프 가능함
캡슐 콜라이더 아래에 점프 가능여부 확인하는 작은 네모 콜라이더 만들면 됨


### 🏷️ UI
#### 9-slice 적용 안됨
UI element의 Image - Image Type을 sliced로 바꾼다

### 🏷️ 협업
#### 깃 pull 할 때마다 메타파일 갱신
1. 애셋 직렬화 방식 : Project Settings - Editor - Asset Serialization - Force Text 통일
2. Project Settings - Editor - Version Control - Visible Meta Files 통일

