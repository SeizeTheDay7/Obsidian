
- [[#📌 팁|📌 팁]]
- [[#⚙️ 설정|⚙️ 설정]]
	- [[#⚙️ 설정#🏷️ World Settings|🏷️ World Settings]]
- [[#🖱️ 조작|🖱️ 조작]]
	- [[#🖱️ 조작#🏷️ Selection Mode|🏷️ Selection Mode]]
	- [[#🖱️ 조작#🏷️ Material Editor|🏷️ Material Editor]]
	- [[#🖱️ 조작#🏷️ Landscape Mode|🏷️ Landscape Mode]]
- [[#🖥️ Script|🖥️ Script]]
	- [[#🖥️ Script#클래스|클래스]]
		- [[#클래스#클래스 추가 후 C++ 프로젝트 리컴파일|클래스 추가 후 C++ 프로젝트 리컴파일]]
	- [[#🖥️ Script#UPROPERTY()|UPROPERTY()]]
	- [[#🖥️ Script#UFUNCTION()|UFUNCTION()]]
- [[#📄 Manual|📄 Manual]]
	- [[#📄 Manual#🏷️ Selection Mode|🏷️ Selection Mode]]
		- [[#🏷️ Selection Mode#Light|Light]]
			- [[#Light#Sky Light|Sky Light]]
		- [[#🏷️ Selection Mode#Visual Effects|Visual Effects]]
			- [[#Visual Effects#Post Process Volume|Post Process Volume]]
			- [[#Visual Effects#Exponential Height Fog|Exponential Height Fog]]
	- [[#📄 Manual#🏷️ Landscape Mode|🏷️ Landscape Mode]]
	- [[#📄 Manual#🏷️ Blueprint|🏷️ Blueprint]]
	- [[#📄 Manual#🏷️ 디버그 명령어|🏷️ 디버그 명령어]]
- [[#🧾 주제별|🧾 주제별]]
	- [[#🧾 주제별#기본 Lighting 세팅|기본 Lighting 세팅]]
	- [[#🧾 주제별#Static Light Bake|Static Light Bake]]
- [[#🦫 디버깅|🦫 디버깅]]
	- [[#🦫 디버깅#🏷️ Selection Mode|🏷️ Selection Mode]]
		- [[#🏷️ Selection Mode#기본 씬 열었는데 GPU Usage Max|기본 씬 열었는데 GPU Usage Max]]
	- [[#🦫 디버깅#🏷️ Material Editor|🏷️ Material Editor]]
		- [[#🏷️ Material Editor#Static Switch 이름 변경이 안됨|Static Switch 이름 변경이 안됨]]


## 📌 팁
---




## ⚙️ 설정
---

- Auto Exposure 설정 : 좌측 상단 세번째 버튼 > Game Settings
- Nanite 확인 : Viewmode > Nanaite Visualization > Mask
- Nanite 활성화 : 해당 애셋 가서 우클릭 > Nanaite

- 시작 맵 설정 : 우측 상단 Settings > Project Settings > Maps * Modes > Default Maps

- 블루프린트 흐름 디버깅 보는 법 : 중앙 상단 드롭다운

### 🏷️ World Settings

- Static Lighting Level Scale x Indirect Lighting Quality = 1 이 되도록 설정해라
- 시작 캐릭 지정 : GameMode > Gamemode Override

## 🖱️ 조작
---

- Content Drawer 열기/닫기 : Ctrl + Space
- 디버그 명령어 입력 : 백틱

### 🏷️ Selection Mode

- 카메라 이동 속도 조절 : 우클 + 스크롤
- 시점 위치 북마크 : Ctrl + 0,1,2, ... (숫자 누르면 해당 위치로 감)
- 게임에서 보이는 화면 : G
- 게임 플레이 안 끄고 빠져나오기 : Shift + F1

- 해당 애셋 들어있는 폴더 : Ctrl + B
- 해당 애셋 바로 열기 : Ctrl + E

- 오브젝트 바닥에 붙이기 : End
- 오브젝트 바로 복사하면서 이동 : Alt + 이동
- 오브젝트 이동하면서 시점 따라가기 : Shift + 이동
- 오브젝트 기준 카메라 이동 : F > Alt > 좌클하며 드래그

- point light 추가 : L 누르고 좌클
- Directional Light 회전 : Ctrl + L 누르고 마우스 이동

### 🏷️ Material Editor

- 연결 옮기기 : Ctrl + 연결 부분 누르며 드래그
- 모든 연결 끊기 : Alt 누르며 연결 부분 좌클

- Value 1 Parameter 추가 : S 누르며 좌클
- Multiply 추가 : M 누르며 좌클
- Lerp 추가 : L 누르며 좌클
- Constant3 추가 : 3 누르며 좌클

### 🏷️ Landscape Mode

`[`, `]` : 브러시 크기 확대/축소


## 🖥️ Script
---

### 클래스

- ACharacter 클래스와 AActor, APawn의 차이점 : ACharacter 클래스는 애니메이션을 지원함, 기본적으로 SkeletalMesh, Movement, Capsule 콜라이더 컴포넌트가 포함됨.

GameInstance
* **게임 전체에서 단 하나**만 존재.
* 레벨을 바꿔도 유지됨.
* 클라이언트에만 존재함.
* **Persistent 데이터 저장용** (예: 설정, 세션 정보, 사용자 데이터).
* 주로 `Init()` 함수에서 초기화.
* 🧩 예: 로그인 정보 저장, 게임 설정 저장, 서버 목록 관리

GameModeBase
* **게임 규칙, 흐름을 관리**하는 클래스.
* 서버에만 존재하며, 클라이언트는 접근 불가.
* 어떤 Pawn을 스폰할지, 언제 게임을 시작할지 등의 로직 포함.
* 🧩 예: 게임 시작 조건, 팀 자동 배정, 승리 조건 정의

GameStateBase
* **게임의 상태를 클라이언트와 동기화**하는 역할.
* 서버에서 생성되어 클라이언트로 **Replicate**됨.
* 점수, 경기 시간, 팀 상태 등 **모든 플레이어가 알아야 하는 공용 정보**를 저장.
* 🧩 예: 남은 시간, 팀 점수, 현재 라운드

PlayerController
* **각 플레이어에게 하나씩 생성**됨.
* 키보드/마우스 입력을 받아 Pawn에 전달.
* HUD 표시, UI 조작 등 **플레이어 인터페이스 관련 처리** 담당.
* 🧩 예: 캐릭터 이동 입력, 스킬 키 처리, HUD 표시, 카메라 컨트롤

#### 클래스 추가 후 C++ 프로젝트 리컴파일
- 기본 : 엔진 에디터 우측 하단의 `Recompiles and reloads ...` 버튼
- 클래스 추가/삭제로 인해 작업이 안된다면 : 에디터 닫고 비쥬얼 스튜디오에서 프로젝트나 솔루션 빌드
- 파일 탐색기에서 수동으로 소스 파일 삭제했다면 : 리컴파일 하기 전에 파일 탐색기에서 `프로젝트 이름.uproject` 파일을 우클릭해서 나오는 메뉴에서 `Generate Visual Studio project files` 선택

### 문법

#### UPROPERTY()

| 지정자                           | 설명                                                                       |
| ----------------------------- | ------------------------------------------------------------------------ |
| `BlueprintAssignable`         | 이 델리게이트 프로퍼티는 블루프린트의 커스텀 이벤트 함수에 할당될 수 있다                                |
| `BlueprintAuthorityOnly`      | 이 델리게이트 프로퍼티는 `BlueprintAuthorityOnly` 태그를 가진 이벤트만 받는다                   |
| `BlueprintReadOnly`           | 이 프로퍼티는 블루프린트에서 읽기만 가능하다                                                 |
| `BlueprintReadWrite`          | 이 프로퍼티는 블루프린트에서 읽고 쓰기가 가능하다                                              |
| `Category = "name1\|name2.."` | 블루프린트 에디터에서 이 프로퍼티의 카테고리를 지정할 수 있다. `\|`를 구분 문자로 사용해 중첩된 카테고리를 정의할 수 있다. |
| `EditAnywhere`                | 에디터의 모든 곳에서 이 프로퍼티를 편집할 수 있다                                             |
| `VisibleAnywhere`             | 이 프로퍼티는 에디터에서 표시되지만 읽기만 가능하다                                             |

| 메타 키                            | 설명                                                     |
| ------------------------------- | ------------------------------------------------------ |
| `AllowPrivateAccess`            | 이 프라이빗 프로퍼티는 블루프린트에서 접근 가능하다                           |
| `DisplayName = "Property Name"` | 이 프로퍼티는 에디터에서 코드가 생성한 이름 대신 `"Property Name"` 값으로 표시된다 |
- private이면 `AllowPrivateAccess`를 붙여줘야 지정자 설정해서 에디터나 블루프린트에서 접근 가능

#### UFUNCTION()

| 지정자                           | 설명                                                                    |
| ----------------------------- | --------------------------------------------------------------------- |
| `BlueprintCallable`           | 이 함수는 블루프린트 또는 레벨 블루프린트에서 실행할 수 있다                                    |
| `BlueprintPure`               | 이 함수는 소유한 오브젝트의 상태를 변경하지 않으며, 실행 핀 없이 노드를 생성한다                        |
| `BlueprintImplementableEvent` | 이 함수는 블루프린트에서 구현할 수 있다 (C++에서는 정의하지 않음)                               |
| `BlueprintNativeEvent`        | 이 함수는 블루프린트에서 오버라이드될 수 있다 (C++ 기본 구현 제공 가능)                           |
| `Category = "name1\|name2.."` | 블루프린트 에디터에서 이 함수의 카테고리를 지정할 수 있다. `\|`를 구분 문자로 사용해 중첩된 카테고리를 정의할 수 있다 |

|메타 키|설명|
|---|---|
|`DisplayName = "Property Name"`|이 함수는 에디터에서 코드 이름 대신 `"Property Name"`으로 표시된다|

#### Template 함수

```cpp
template <typename T>
T Add<T>(T a, T b)
{
	return a + b;
}
template <typename T>
T Subtract<T>(T a, T b)
{
	return a - b;
}

float f = calculator.Add<float>(1.5f, 2.0f);
float i = calculator.Subtract<int>(3, 2);
```


## 📄 Manual
---

### 🏷️ Selection Mode

- Map은 File > New Level로 만들어야 Level Template 사용 가능
- Engine Content 보는 법 : Content Drawer > 우측 상단 Settings > Show Engine Content
- 3D Model Import할 때 필요 없으면 Import Material 끄기

#### Light

##### Sky Light
- Sky Light  추가
- Visual Effects > Sky Atmosphere 추가
- Directional Light 추가
- Details > Affects World 체크 해제 후 다시 체크

#### Visual Effects
##### Post Process Volume
- 적용 범위 global로 : Details > Post Process Volume Settings > Infinite Esxtent (Unbound)
- 그림자 노이즈 없애기 : Details > Lumen Global Volume > Final Gather Quality 증가
##### Exponential Height Fog
- Start Distance 멀리 놓아야 가까운 곳에 fog 안 생김


### 🏷️ Landscape Mode

- Landscape 새로 만들 때 크기 참고 : [링크](https://dev.epicgames.com/documentation/en-us/unreal-engine/landscape-technical-guide-in-unreal-engine)


### 🏷️ Blueprint

- 블루프린트 오브젝트 parameter 노출 : Details > Insatnce Editable, Exposure on Spawn 체크
- 맵 에디터에서 오브젝트를 선택한 후 돌아와서 우클하면 해당 오브젝트와 관련된 노드 추가 가능


### 🏷️ 디버그 명령어

플레이 모드에서 백틱으로 열고 입력하는 명령어들

- t.Maxfps : 최대 fps 설정. 0이면 기본 값으로 돌아감.


## 🧾 주제별
---

### 기본 Lighting 세팅

- Directional Light 추가
- Visual Effect > Sky Atmosphere 추가
- Sky Light 추가
- Visual Effect > Volumetric Cloud 추가
- Visual Effect > Exponential Height Fog 추가
- PostProcess Volume 추가
  - Lens > Exposure > Metering Mode : Manual , Exposure Compensation : 11
  - Post Process Volume Settings > Infinite Extent (Unbound) 체크

### Static Light Bake

- Static Light Bake 설정 : Project Settings > Engine > Rendering > Allow Static Lighting
- Build Lighting 설정 : Build > Lighting Quality > Medium 이상 설정
- Bake할 때 Lightmap density 확인 : Viewmode > Optimization viewmodes > Lightmap density
- Lightmap density 올리기 : viewmode 바꾼 상태에서 오브젝트 클릭 > Details > Lighting > Overrides Light Map Res 증가
- Ambient Occlusion 그림자하고 겹치니까 Post Process Volume > Details > Rendering Features > Ambient Occlusion > Intensity > 0





## 🦫 디버깅
---

### 🏷️ Editor

#### 기본 씬 열었는데 GPU Usage Max

- 실시간 렌더 끄기 : 뷰포트 왼쪽 상단 메뉴 → `Real-Time` 체크 해제
- 프레임 제한 : `Edit > Project Settings > Engine > General Settings` 에서 `Use Fixed Frame Rate` 활성화, `Fixed Frame Rate` 값을 60 또는 그 이하로 설정
- 뷰포트 설정 낮게 : `씬 좌측 상단 Settings > Engine Scalability Settings > Low`
- 나나이트 끄기 : `Static Mesh 에디터 > 우측 세부 설정에서 Nanite Settings > Enable Nanite 체크 해제`
- 루멘 끄기 : `Edit > Project Settings > Dynamic Global Illumination Method, Reflection Method 변경`

#### 껏다 다시 켰더니 클래스 반영이 안됨
Edit > Editor Preferences > Live coding 검색 후 끄기
에디터 끄고 리빌드


### 🏷️ Selection Mode




### 🏷️ Material Editor

#### Static Switch 이름 변경이 안됨
그거 말고 노드 이름이 Static Switch Parameter인 걸로 고르셈
