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
	- [[#💾 개념#.meta 파일|.meta 파일]]
	- [[#💾 개념#재정의(override) 가능한 메서드|재정의(override) 가능한 메서드]]
- [[#📋 정보|📋 정보]]
	- [[#📋 정보#🏷️ Editor|🏷️ Editor]]
	- [[#📋 정보#🏷️ Script|🏷️ Script]]
		- [[#🏷️ Script#GetKey 차이|GetKey 차이]]
		- [[#🏷️ Script#private void vs void|private void vs void]]
		- [[#🏷️ Script#변수를 꼭 밖으로 뺄 이유는 없다|변수를 꼭 밖으로 뺄 이유는 없다]]
		- [[#🏷️ Script#레이캐스트 확인하는 방법|레이캐스트 확인하는 방법]]
	- [[#📋 정보#🏷️ Graphic|🏷️ Graphic]]
		- [[#🏷️ Graphic#Mesh Renderer|Mesh Renderer]]
		- [[#🏷️ Graphic#Image vs Raw Image|Image vs Raw Image]]
- [[#🦫 디버깅|🦫 디버깅]]
	- [[#🦫 디버깅#🏷️ 인게임|🏷️ 인게임]]
		- [[#🏷️ 인게임#오브젝트들 전부 살짝 흐림|오브젝트들 전부 살짝 흐림]]
		- [[#🏷️ 인게임#Cinemachine 따라가기 덜덜 떨림|Cinemachine 따라가기 덜덜 떨림]]
		- [[#🏷️ 인게임#콜라이더 적용해도 벽뚫|콜라이더 적용해도 벽뚫]]
		- [[#🏷️ 인게임#플레이어가 벽에 달라붙음|플레이어가 벽에 달라붙음]]
		- [[#🏷️ 인게임#플레이어가 벽에 닿으면 계속 점프 가능함|플레이어가 벽에 닿으면 계속 점프 가능함]]
		- [[#🏷️ 인게임#Navmesh Bake 안 보임|Navmesh Bake 안 보임]]
		- [[#🏷️ 인게임#Raycast 안됨|Raycast 안됨]]
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
### 🏷️ Editor



### 🏷️ Script

#### GetKey 차이
GetKey : 해당 키 누르는 동안 true 반복적 반환  
GetKeyDown : 해당 키 누르면 단 한 번 true 반환  
GetKeyUp : 해당 키 누름 해제되면 true 한 번 반환
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

#### 레이캐스트 확인하는 방법
Analysis > Physics Debugger


### 🏷️ Graphic

#### Mesh Renderer
- 기본 역할: 정적(Static) 또는 변형되지 않는 3D 메시에 대한 렌더링을 처리.
- 사용 예시: 건물, 바위, 가구 등 변형되지 않는 오브젝트.
- 특징:
  - Transform 컴포넌트로 위치, 회전, 크기만 변경 가능.
  - 메시의 정점(Vertex)이나 형태가 바뀌지 않음.
  - 단순한 렌더링 파이프라인을 사용하며, 계산량이 적음.
  - 머티리얼 및 셰이더와 호환성이 높음.
#### Image vs Raw Image

| **기능**                | **Image**                  | **Raw Image**            |
|--------------------------|----------------------------|--------------------------|
| **사용 가능한 이미지 타입** | Sprite                   | Texture (Default, RT 등) |
| **9-Slicing 지원**       | 지원                      | 미지원                   |
| **Mask와 호환성**         | 완벽 지원                 | 제한적                   |
| **커스텀 셰이더/머티리얼** | 제한적                   | 지원                     |
| **Render Texture 지원**  | 미지원                   | 지원                     |
| **UI 요소 용도**         | 버튼, 배경, 슬라이더 등    | 동적 출력, 고급 효과      |

- Image는 UI 디자인 요소에 적합하며, 간단하고 효율적으로 사용 가능합니다.
- Raw Image는 동적 콘텐츠나 렌더 텍스처를 처리하거나, 셰이더 효과를 적용할 때 적합합니다.




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

#### 플레이어가 벽에 닿으면 계속 점프 가능함
캡슐 콜라이더 아래에 점프 가능여부 확인하는 작은 네모 콜라이더 만들면 됨

#### Navmesh Bake 안 보임
- Bake 하는 방법을 못 찾겠음 : Navmesh Surface 추가
- Bake 했는데 안 보임 : 우측 하단 AI Navigation > Surfaces > Show Navmesh 체크

#### Raycast 안됨
- 렌더 텍스쳐를 Output Texture에 넣으면 마우스 Raycast 작동 안 함. 셰이더 쓰셈.

### 🏷️ UI
#### 9-slice 적용 안됨
UI element의 Image - Image Type을 sliced로 바꾼다

### 🏷️ 협업
#### 깃 pull 할 때마다 메타파일 갱신
1. 애셋 직렬화 방식 : Project Settings - Editor - Asset Serialization - Force Text 통일
2. Project Settings - Editor - Version Control - Visible Meta Files 통일

