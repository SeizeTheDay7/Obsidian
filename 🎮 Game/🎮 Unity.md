- [[#📌 팁|📌 팁]]
	- [[#📌 팁#단축키|단축키]]
	- [[#📌 팁#최적화|최적화]]
	- [[#📌 팁#에디터|에디터]]
- [[#⚙️ 설정|⚙️ 설정]]
	- [[#⚙️ 설정#🏷️ 성능|🏷️ 성능]]
		- [[#🏷️ 성능#수정 후 빠르게 재생|수정 후 빠르게 재생]]
	- [[#⚙️ 설정#🏷️ 디버그|🏷️ 디버그]]
		- [[#🏷️ 디버그#애셋 직렬화 방식 통일|애셋 직렬화 방식 통일]]
		- [[#🏷️ 디버그#프로젝트 렌더링 파이프라인 확인|프로젝트 렌더링 파이프라인 확인]]
- [[#🔍 Inspector|🔍 Inspector]]
	- [[#🔍 Inspector#Line Renderer|Line Renderer]]
- [[#💾 개념|💾 개념]]
	- [[#💾 개념#🏷️ General|🏷️ General]]
		- [[#🏷️ General#.meta 파일|.meta 파일]]
	- [[#💾 개념#🏷️ Script|🏷️ Script]]
		- [[#🏷️ Script#재정의(override) 가능한 메서드|재정의(override) 가능한 메서드]]
- [[#📄 Docs|📄 Docs]]
	- [[#📄 Docs#🏷️ Component|🏷️ Component]]
		- [[#🏷️ Component#Rigidbody|Rigidbody]]
			- [[#Rigidbody#Body Type|Body Type]]
		- [[#🏷️ Component#CharacterController|CharacterController]]
		- [[#🏷️ Component#Mesh Renderer|Mesh Renderer]]
		- [[#🏷️ Component#Cinemachine|Cinemachine]]
			- [[#Cinemachine#Aim|Aim]]
	- [[#📄 Docs#🏷️ Shader Graph|🏷️ Shader Graph]]
		- [[#🏷️ Shader Graph#노드|노드]]
- [[#📋 Detail|📋 Detail]]
	- [[#📋 Detail#🏷️ Editor|🏷️ Editor]]
	- [[#📋 Detail#🏷️ Script|🏷️ Script]]
		- [[#🏷️ Script#GetKey 차이|GetKey 차이]]
		- [[#🏷️ Script#GetAxis, GetAxisRaw 차이|GetAxis, GetAxisRaw 차이]]
		- [[#🏷️ Script#private void vs void|private void vs void]]
		- [[#🏷️ Script#변수를 꼭 밖으로 뺄 이유는 없다|변수를 꼭 밖으로 뺄 이유는 없다]]
		- [[#🏷️ Script#레이캐스트 확인하는 방법|레이캐스트 확인하는 방법]]
	- [[#📋 Detail#🏷️ Graphic|🏷️ Graphic]]
		- [[#🏷️ Graphic#Image vs Raw Image|Image vs Raw Image]]
	- [[#📋 Detail#🏷️ Component|🏷️ Component]]
- [[#🦫 디버깅|🦫 디버깅]]
	- [[#🦫 디버깅#🏷️ Editor|🏷️ Editor]]
		- [[#🏷️ Editor#Tile Pallete 타일 크기 작음|Tile Pallete 타일 크기 작음]]
	- [[#🦫 디버깅#🏷️ 인게임|🏷️ 인게임]]
		- [[#🏷️ 인게임#오브젝트들 전부 살짝 흐림|오브젝트들 전부 살짝 흐림]]
		- [[#🏷️ 인게임#Cinemachine 따라가기 덜덜 떨림|Cinemachine 따라가기 덜덜 떨림]]
		- [[#🏷️ 인게임#콜라이더 적용해도 벽뚫|콜라이더 적용해도 벽뚫]]
		- [[#🏷️ 인게임#플레이어가 벽에 달라붙음|플레이어가 벽에 달라붙음]]
		- [[#🏷️ 인게임#플레이어가 벽에 닿으면 계속 점프 가능함|플레이어가 벽에 닿으면 계속 점프 가능함]]
		- [[#🏷️ 인게임#Navmesh Bake 안 보임|Navmesh Bake 안 보임]]
		- [[#🏷️ 인게임#Raycast 안됨|Raycast 안됨]]
		- [[#🏷️ 인게임#머테리얼을 Transparent로 설정해도 살짝 불투명|머테리얼을 Transparent로 설정해도 살짝 불투명]]
		- [[#🏷️ 인게임#플레이어 이동에 약간 딜레이|플레이어 이동에 약간 딜레이]]
		- [[#🏷️ 인게임#스프라이트 마스크 어떻게 씀?|스프라이트 마스크 어떻게 씀?]]
	- [[#🦫 디버깅#🏷️ UI|🏷️ UI]]
		- [[#🏷️ UI#9-slice 적용 안됨|9-slice 적용 안됨]]
	- [[#🦫 디버깅#🏷️ 협업|🏷️ 협업]]
		- [[#🏷️ 협업#깃 pull 할 때마다 메타파일 갱신|깃 pull 할 때마다 메타파일 갱신]]


## 📌 팁
---

### 단축키

- 창 전체화면 : Shift + Space
- 카메라를 씬 뷰 시선에 맞추기 : 카메라 선택하고 Ctrl+Sfhit+F

### 최적화
- 퀄리티 차이 안 날 때까지 Texture의 Max Size 줄이기

#### 플랫폼별 적절한 Tris(폴리곤) 개수 가이드라인  

| 플랫폼                                 | 권장 Tris 개수 (씬 전체 기준) | 최적화 필요 여부                 |
| ----------------------------------- | -------------------- | ------------------------- |
| 모바일 (Low-end, 보급형 기기)               | 100K ~ 300K          | ✅ 필수 (LOD + Occlusion)    |
| 모바일 (High-end, 플래그십 기기)             | 300K ~ 700K          | ⚠️ 일부 최적화 필요              |
| PC (Low-end, 내장그래픽, GTX 750 이하)     | 500K ~ 1M (100만)     | ✅ 필요 (LOD + Draw Call 감소) |
| PC (중급, GTX 1060 ~ 1660)            | 1M ~ 2M (200만)       | ⚠️ 적당한 최적화 필요             |
| PC (고급, RTX 3060 이상)                | 2M ~ 5M (500만)       | ❌ 최적화 크게 필요 없음            |
| PS4 / Xbox One                      | 1M ~ 2M (200만)       | ⚠️ 일부 최적화 필요              |
| PS5 / Xbox Series X                 | 3M ~ 10M (천만)        | ❌ 높은 처리 가능                |
| VR (Standalone, Quest 2)            | 100K ~ 500K          | ✅ 필수 (프레임 유지 필수)          |
| VR (PC VR, Valve Index, Quest Link) | 1M ~ 3M (300만)       | ⚠️ 약간의 최적화 필요             |

#### 씬 내 폴리곤 최적화

1️⃣ LOD(Level of Detail) 활용  
   - 가까운 오브젝트만 고해상도, 멀리 있는 건 저해상도로 자동 변경  
   - `LOD Group`을 활용해서 LOD 0 (높은 Tris) → LOD 3 (낮은 Tris) 설정

2️⃣ Occlusion Culling 활성화  
   - 카메라에 안 보이는 모델을 렌더링하지 않도록 최적화  
   - `Window > Rendering > Occlusion Culling`에서 적용

3️⃣ Batches / Draw Calls 최적화  
   - `Stats` 창에서 `SetPass Calls`가 많으면 병목 가능성 있음  
   - Mesh Combine + GPU Instancing을 적용해서 성능 개선

4️⃣ Shader & Material 최적화  
   - PBR 쉐이더 사용을 줄이고, Lightmap 사용으로 실시간 조명 연산을 줄이기  
   - 한 개의 머티리얼을 여러 개의 오브젝트에서 공유하면 드로우콜 감소

5️⃣ Dynamic Objects 줄이기  
   - 애니메이션이 적용된 오브젝트가 많으면 CPU 부하 증가  
   - `Static Batching`을 적용하면 정적인 오브젝트를 최적화할 수 있음
   - 

### 에디터
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

### 🏷️ General
#### .meta 파일
컴포넌트 간의 연결과 같은 메타 정보들을 담고 있다.
유니티 에디터에서 파일 위치나 이름 바꾼거 아니면 이거 때문에 정보 소실.

깃허브에 커밋할 때 .meta 빠뜨리면 안되고
외부에 깃 말고 보낼 땐 .unitypackage로 만들어라.

### 🏷️ Script
#### 재정의(override) 가능한 메서드
- 부모 클래스의 메서드가 `virtual`, `abstract`, 또는 `override`로 선언되지 않았다면, 자식 클래스에서 해당 메서드를 `override`로 재정의할 수 없습니다.
- Unity의 `Awake`는 기본적으로 MonoBehaviour의 메서드로 `virtual`이 아니므로, 재정의하려면 부모 클래스에서 `Awake`를 `virtual`로 명시해야 합니다.

#### Unity : Coroutine

**개념 및 원리**
- 설정한 만큼 멈췄다가 다시 실행
- 멈췄던 위치에서 다시 실행됨
- 긴 비동기 작업할 때 쓰면 됨
- 멀티쓰레딩은 아니다

**문제 및 해결**
- 디버깅 어렵다. 로그 넣어주자.
- 다 쓰고 안 꺼주면 성능 문제.
- 무거운 연산 쓰면 프레임 드랍. 프레임마다 쪼개서 실행하기.

**끄는 법**
- StopCoroutine(), StopAllCoroutines()
- 코루틴 붙은 오브젝트 SetActive(false), Destroy()
- Monobehaviour 스크립트는 enabled false로 해도 코루틴 안 꺼짐


## 📄 Docs
---

### 🏷️ Component

#### Rigidbody
##### Body Type
- Dynamic : 완전히 물리 연산
- Kinematic : 물리 연산 없이 충돌 감지만 가능. 움직이려면 rb.MovePosition()
- Static : 절대 안 움직임


#### CharacterController
- 정확한 충돌 감지 (벽 통과 방지)  
- 중력, 계단 이동, 경사면 처리 가능  
- Rigidbody 없이도 이동 및 점프 구현 가능  
- 플레이어 이동을 세밀하게 조정 가능  
- 물리 연산이 불필요하여 성능 최적화 가능 
#### Mesh Renderer
- 기본 역할: 정적(Static) 또는 변형되지 않는 3D 메시에 대한 렌더링을 처리.
- 사용 예시: 건물, 바위, 가구 등 변형되지 않는 오브젝트.
- 특징:
  - Transform 컴포넌트로 위치, 회전, 크기만 변경 가능.
  - 메시의 정점(Vertex)이나 형태가 바뀌지 않음.
  - 단순한 렌더링 파이프라인을 사용하며, 계산량이 적음.
  - 머티리얼 및 셰이더와 호환성이 높음.
#### Cinemachine
##### Aim
1. Do nothing  : 카메라가 대상을 바라보지 않고, 별도의 조정 없이 고정된 상태로 유지됩니다.
2. Composer : 자동으로 목표 오브젝트를 따라가며 화면에서 적절한 위치에 유지되도록 합니다. 카메라가 부드럽게 따라가는 효과가 있습니다.
3. Group Composer : 여러 개의 대상을 포함하는 그룹을 추적하는 기능입니다. 그룹 내 대상의 위치를 조정하여 카메라가 자연스럽게 움직이도록 합니다.
4. Hard Look At : 카메라가 항상 목표 오브젝트를 정확하게 바라보도록 강제하는 방식입니다. 회전이 즉각적으로 적용되며 자연스러운 움직임 없이 즉시 방향을 맞춥니다.
5. POV : 1인칭 혹은 3인칭 조작 방식에서 사용되며, 플레이어 입력(마우스 또는 컨트롤러)을 기반으로 카메라가 회전합니다. FPS(1인칭 슈팅 게임) 또는 TPS(3인칭 액션 게임) 카메라에서 많이 사용됩니다.
6. Same As Follow Target : 카메라가 설정된 대상의 회전을 그대로 따라갑니다.

### 🏷️ Shader Graph

#### 노드
- Scanline 효과: Checkerboard


## 📋 Detail
---
### 🏷️ Editor

- 오브젝트들 묶었을 때 피벗은 부모 오브젝트의 위치

#### Import
- 블랜더 export할 때 : Selected Objects, Apply Transform (유니티 원치않는 회전 막기)
- 유니티로 import할 때
	- Model > import 붙은 옵션 끄기
	- Model > Scale Factor 조절하여 크기 조절
	- Material Creation Mode > None
	- Animation > Import Animation 끄기

- 모델의 크기는 성능에 영향 안 주고, 버텍스와 폴리곤 개수가 성능에 영향 미친다

### 🏷️ Script

#### GetKey 차이
GetKey : 해당 키 누르는 동안 true 반복적 반환  
GetKeyDown : 해당 키 누르면 단 한 번 true 반환  
GetKeyUp : 해당 키 누름 해제되면 true 한 번 반환

#### GetAxis, GetAxisRaw 차이
Input.GetAxis() : 사용자가 키를 누르면 값이 0에서 1로 서서히 증가하며, 키를 떼면 1에서 0으로 서서히 감소합니다.
Input.GetAxisRaw() : 키를 누르는 순간 1이 되고, 키를 떼면 즉시 0으로 돌아갑니다.
#### private void vs void
접근 제한자는 생략해도 되지만 가독성을 위해 명시적으로 추가하는게 좋다.

#### 변수를 꼭 밖으로 뺄 이유는 없다
```cs
void Update()
{
	GameObject player = GameObject.FindWithTag("Player");
}
```

player를 update 문 바깥에서 전역 변수로 선언한다고 해서 메모리가 아껴지진 않는다. 
어차피 update 문이 끝나면 스택 메모리가 자동으로 정리되기 때문이다.


### 🏷️ Graphic

#### Image vs Raw Image
- Image는 UI 디자인 요소에 적합하며, 간단하고 효율적으로 사용 가능합니다.
- Raw Image는 동적 콘텐츠나 렌더 텍스처를 처리하거나, 셰이더 효과를 적용할 때 적합합니다.

### 🏷️ Component






## 🦫 디버깅
---

### 🏷️ Editor

#### Tile Pallete 타일 크기 작음
Tile Pallete 만들 때 Cell Size 1x1로 설정

### 🏷️ 인게임
#### 오브젝트들 전부 살짝 흐림
해상도를 Full HD로 바꾸고 1.5x로 돼있는 Scale을 1x로 바꾸기

#### Cinemachine 따라가기 덜덜 떨림
Rigidbody > Interpolation > Interpolate로 변경

#### 콜라이더 적용해도 벽뚫
Rigidbody > Collision Detection > Continous로 변경

#### 플레이어가 벽에 달라붙음
Physics Material 2D > Friction 0 > 적용

#### 플레이어가 벽에 닿으면 계속 점프 가능함
캡슐 콜라이더 아래에 점프 가능여부 확인하는 작은 네모 콜라이더 만들면 됨

#### Navmesh Bake 안 보임
- Bake 하는 방법을 못 찾겠음 : Navmesh Surface 추가
- Bake 했는데 안 보임 : 우측 하단 AI Navigation > Surfaces > Show Navmesh 체크

#### Raycast 안됨
- 2D 프로젝트면 Physics2D.Raycast() 사용하기
- 렌더 텍스쳐를 Output Texture에 넣으면 마우스 Raycast 작동 안 함. 셰이더 쓰셈.

#### 머테리얼을 Transparent로 설정해도 살짝 불투명
셰이더를 Unlit으로 설정한다

#### 플레이어 이동에 약간 딜레이
Input.GetAxis 쓰면 딜레이 생긴다. Input.GetAxisRaw 쓰기.

#### 스프라이트 마스크 어떻게 씀?
Sprite Mask component may not be an issue. 
check Mask Interaction component on parent.

#### Camera.main이 null임
`Camera.main`은 "MainCamera" 태그가 붙은 카메라만 인식

### 🏷️ UI
#### 9-slice 적용 안됨
UI element의 Image - Image Type을 sliced로 바꾼다

### 🏷️ 협업
#### 깃 pull 할 때마다 메타파일 갱신
1. 애셋 직렬화 방식 : Project Settings - Editor - Asset Serialization - Force Text 통일
2. Project Settings - Editor - Version Control - Visible Meta Files 통일

