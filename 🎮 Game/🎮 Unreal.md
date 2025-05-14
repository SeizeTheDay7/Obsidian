- [[#📌 팁|📌 팁]]
- [[#⚙️ 설정|⚙️ 설정]]
	- [[#⚙️ 설정#🏷️ World Settings|🏷️ World Settings]]
- [[#🧱 Build|🧱 Build]]
	- [[#🧱 Build#Build Workflow|Build Workflow]]
	- [[#🧱 Build#빌드 관련 폴더|빌드 관련 폴더]]
	- [[#🧱 Build#Visual Studio|Visual Studio]]
- [[#🖱️ 조작|🖱️ 조작]]
	- [[#🖱️ 조작#🏷️ Selection Mode|🏷️ Selection Mode]]
	- [[#🖱️ 조작#🏷️ Material Editor|🏷️ Material Editor]]
	- [[#🖱️ 조작#🏷️ Landscape Mode|🏷️ Landscape Mode]]
- [[#🖥️ Script|🖥️ Script]]
	- [[#🖥️ Script#클래스|클래스]]
		- [[#클래스#클래스 추가 후 C++ 프로젝트 리컴파일|클래스 추가 후 C++ 프로젝트 리컴파일]]
	- [[#🖥️ Script#문법|문법]]
		- [[#문법#UPROPERTY()|UPROPERTY()]]
		- [[#문법#UFUNCTION()|UFUNCTION()]]
		- [[#문법#Template 함수|Template 함수]]
- [[#📘 Blueprint|📘 Blueprint]]
	- [[#📘 Blueprint#🏷️ Animation Blueprint|🏷️ Animation Blueprint]]
- [[#🧑‍💻 Editor|🧑‍💻 Editor]]
	- [[#🧑‍💻 Editor#🏷️ Selection Mode|🏷️ Selection Mode]]
		- [[#🏷️ Selection Mode#Light|Light]]
			- [[#Light#Sky Light|Sky Light]]
		- [[#🏷️ Selection Mode#Visual Effects|Visual Effects]]
			- [[#Visual Effects#Post Process Volume|Post Process Volume]]
			- [[#Visual Effects#Exponential Height Fog|Exponential Height Fog]]
	- [[#🧑‍💻 Editor#🏷️ Landscape Mode|🏷️ Landscape Mode]]
- [[#📦 Asset|📦 Asset]]
	- [[#📦 Asset#Animation Sequence|Animation Sequence]]
- [[#🦫 디버깅|🦫 디버깅]]
	- [[#🦫 디버깅#🏷️ Editor|🏷️ Editor]]
	- [[#🦫 디버깅#🏷️ Script|🏷️ Script]]
	- [[#🦫 디버깅#🏷️ Blueprint|🏷️ Blueprint]]
- [[#🔧 Task Based|🔧 Task Based]]
	- [[#🔧 Task Based#기본 Lighting 세팅|기본 Lighting 세팅]]
	- [[#🔧 Task Based#Static Light Bake|Static Light Bake]]
	- [[#🔧 Task Based#Enhanced Input Component|Enhanced Input Component]]
- [[#🛠️ TroubleShooting|🛠️ TroubleShooting]]
	- [[#🛠️ TroubleShooting#🏷️ Editor|🏷️ Editor]]
		- [[#🏷️ Editor#기본 씬 열었는데 GPU Usage Max|기본 씬 열었는데 GPU Usage Max]]
		- [[#🏷️ Editor#끄고 빌드하고 다시 켜도 반영이 안됨|끄고 빌드하고 다시 켜도 반영이 안됨]]
	- [[#🛠️ TroubleShooting#🏷️Blueprint|🏷️Blueprint]]
	- [[#🛠️ TroubleShooting#🏷️ Selection Mode|🏷️ Selection Mode]]
	- [[#🛠️ TroubleShooting#🏷️ Material Editor|🏷️ Material Editor]]
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


## 🧱 Build
---

### 폴더 추가하고 반영하기 (하면 안됨)

선요약 : 폴더 추가하지 말고 visual studio에선 필터로 관리해라

**폴더**는 **탐색기**에서 만들어야되고, 
**클래스**는 **에디터**에서 등록해야 되고, 
**visual studio**에서 할 수 있는건 **코드 편집**밖에 없다.
파일을 다른 폴더로 옮기는 건 에디터에서 안 해도 된다.

폴더 만들고 파일 옮긴 후엔
해당 언리얼 프로젝트 폴더 가서
sln 삭제한 후에 `Generate Visual Studio project files`
(추가로 만진게 있거나 이상해졌다면 `Intermediate`, `Binaries`까지 삭제)
빌드까지 한 후에 에디터 열기

를 하면 안되는 이유 : include 경로는 자동으로 업데이트되지 않음. 이를 해결하려면 resharper 같은 유료 툴을 써야 함.

### Build Workflow
- 헤더 파일이나 생성자 건드린게 아니라면 Live Coding 이용
- BP로 프로토타이핑 한 후에 C++ 작성
- 에디터 켜지 말고 IDE에서 Game을 직접 실행해보기
- "Preview Blueprint Header in C++" 기능으로 BP에서 C++ 전환 (없어졌다는 얘기가 있다?)
- - 헤더 파일에서 불필요하게 다른 클래스를 `#include`하지 말고, 포인터나 참조만 쓸 거라면 `class Foo;` 같은 전방 선언으로 대체.

### 빌드 관련 폴더

프로젝트 루트 폴더에 있다

`Binaries/`
- 빌드된 실행 파일(`.exe`), DLL 파일, Hot Reload DLL, 로그 파일 등을 포함
- 삭제 후에는 반드시 재빌드해야 실행 가능

`Intermediate/`
- 빌드 중간 결과물, PCH(Precompiled Header), UHT(UnrealHeaderTool) 결과, 프로젝트 캐시 저장
- 삭제하면 빌드 시간이 늘어나지만, 깨끗한 재빌드가 가능

### Visual Studio

빌드 옵션
- **DebugGame**: 엔진 코드는 최적화, 게임 모듈은 디버깅 포함 빌드. 게임만 디버깅할 때 사용.
- **DebugGame Editor**: DebugGame과 동일한데, Unreal Editor를 실행할 수 있도록 설정돼있어 에디터에서 게임 코드 디버깅할 때 사용. (라고는 하는데, 해봤더니 런처로 열면 반영 안됨)
- **Development**: 엔진, 게임 코드 대부분 최적화. 기본적인 디버깅 가능하지만 일부 최적화로 인해 디버깅 안 될수도 있다. 일반적인 개발 및 테스트에 적합.
- **Development Editor**: Development와 동일하지만 Unreal Editor 실행 가능.
- **Shipping**: 엔진, 게임 코드 모두 최대한의 최적화. 디버깅은 불가능하지만 최상의 성능.





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

- Navmesh 보이게 하거나 숨기기 : P
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

| 접두어 | 의미                  | 예시                               |
| --- | ------------------- | -------------------------------- |
| `U` | UObject 기반 클래스      | `UActorComponent`, `UStaticMesh` |
| `A` | Actor 기반 클래스        | `ACharacter`, `AWeapon`          |
| `F` | 구조체 (`struct`)      | `FVector`, `FName`, `FTransform` |
| `I` | 인터페이스 (`interface`) | `IInteractable`, `IDamageable`   |
| `E` | 열거형 (`enum`)        | `EWeaponType`, `EMovementMode`   |
| `T` | 템플릿 클래스 (컨테이너)      | `TArray`, `TMap`, `TSet`         |

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

#### Overlap

```cpp
void AWeapon::BeginPlay()
{
	Super::BeginPlay();
	
	OnActorBeginOverlap.AddDynamic(this, &AWeapon::OnWeaponBeginOverlap);
}
```

`OnActorBeginOverlap`은 델리게이트 변수라서 직접 호출하거나 편집 불가.
BeginPlay()에서 OnActorBeginOverlap에 특정 함수를 바인딩해주면 충돌할 때 그 함수 호출


```cpp
UFUNCTION()
void OnWeaponBeginOverlap(AActor* OverlappedActor, AActor* OtherActor);
```

OverlappedActor : overlap 당한 액터 (이 함수 갖고 있는 놈)
OtherActor : overlap 한 액터 (와서 충돌한 놈)


#### AddDynamic

UFUNCTION 핸들러를 런타임 델리게이트에 리플렉션 기반으로 바인딩.  
블루프린트와의 연결, GC 관리가 필요할 때 필수.  
그냥 핸들러 바인딩이라고 보면 되지만, 리플렉션 시스템 때문에 일반 C++ 델리게이트보다 더 무겁다.

### 자료형

#### FString, FText, FName

| 타입        | 특징                           | 예시                                           |
| --------- | ---------------------------- | -------------------------------------------- |
| `FString` | 일반 문자열 (변경 가능, 메모리 많이 씀)     | `FString MyName = "Hello";`                  |
| `FText`   | 로컬라이징 지원 문자열 (UI 텍스트 전용)     | `FText MyText = FText::FromString("Hello");` |
| `FName`   | 고정 이름 (빠르고 메모리 효율 높음, 변경 불가) | `FName MyTag = "EnemyTag";`                  |
`FName`은 문자열을 직접 비교하지 않고, 내부적으로 **이름 해시 테이블의 인덱스(정수)로 비교**
소켓 이름 지정할 때 `FName` 사용

#### FAttachmentTransformRules

액터 또는 컴포넌트를 다른 컴포넌트에 부착(Attach)할 때 부착 방식(트랜스폼 동기화 방식)을 정의하는 구조체

| 옵션                              | 의미                                        |
| ------------------------------- | ----------------------------------------- |
| `KeepRelativeTransform`         | 현재 상대 트랜스폼을 유지하면서 부착. (기존 위치 그대로 유지)      |
| `KeepWorldTransform`            | 현재 월드 트랜스폼 유지. (월드 좌표에서 그대로 유지됨)          |
| `SnapToTargetNotIncludingScale` | 대상 소켓의 위치, 회전만 따라감. 스케일은 현재 스케일 유지.       |
| `SnapToTargetIncludingScale`    | 대상 소켓의 위치, 회전, 스케일까지 모두 따라감. (가장 강력한 동기화) |




## 📘 Blueprint
---

- 블루프린트 오브젝트 parameter 노출 : Details > Insatnce Editable, Exposure on Spawn 체크
- 맵 에디터에서 오브젝트를 선택한 후 돌아와서 우클하면 해당 오브젝트와 관련된 노드 추가 가능

### 🏷️ Animation Blueprint

- State Machine에서 조건을 설정해놓으면 State Machine이 조건을 매 틱 보고 변화를 감지해줌

워크 플로우
- c++로 만든 애니메이션 인스턴스 부모 클래스로 하는 Animation Blueprint를 만든다
- Skeleton을 선택한다
- 상태에 따른 State를 추가한다.
- 필요하다면 AnimGraph에 State machine을 추가한다.
- 각 State에 대응하는 애니메이션을 State 안에 추가한다
- Transition을 설정하고, Transition 안에 Transition 조건을 추가한다.
- 필요하다면 각 애니메이션에 설정했던 이벤트들을 별도로 작성한 핸들러 함수와 연결한다.

## 🧑‍💻 Editor
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

#### Actor

- Generate Overlap Events가 2개의 액터 모두에 켜져 있어야 Overlap 이벤트 발생.
- Simulation Generates Hit Events가 2개의 액터 모두에 켜져 있어야 Hit 이벤트 발생.

##### Collision presets
- Custom: 개발자가 모든 콜리전 설정을 변경할 수 있다
- NoCollision: 충돌 발생 안 함
- BlockAll: 씬의 모든 액터와 Hit. OnActorHit와 OnComponentHit 이벤트 발생.
- OverlapAll: 씬의 모든 액터와 Overlap. BeginOverlap과 EndOverlap 이벤트 발생.
- BlockAllDynamic: BlockAll과 동일하지만 pawn, camera, vehicle에만 적용.
- OverlapAllDynamic: OverlapAll과 동일하지만 pawn, camera, vehicle에만 적용.
- OverlapOnlyPawn: OverlapAll과 동일하지만 pawn에만 적용.




### 🏷️ Landscape Mode

- Landscape 새로 만들 때 크기 참고 : [링크](https://dev.epicgames.com/documentation/en-us/unreal-engine/landscape-technical-guide-in-unreal-engine)


## 📦 Asset
---

### Animation Sequence
- 왼쪽에 있는 노티파이 트랙 추가는 노티파이가 아니라 노티파이가 들어갈 수 있는 영역을 추가하는 것
- Animation Track에 노티파이를 추가하려면 해당 노티파이와 같은 높이에서 트랙에 우클릭


## 🦫 디버깅
---

### 🏷️ Editor

- 재생 버튼 옆에 점 세 개 누르면 플레이어 캐릭터 없이 Simulate만 하거나 Standalone으로 실행할수도 있다.

**플레이 모드에서 백틱으로 열고 입력하는 명령어들**
- t.Maxfps : 최대 fps 설정. 0이면 기본 값으로 돌아감.

### 🏷️ Script

```cpp
GEngine->AddOnScreenDebugMessage(0, 5.f, FColor::Green, TEXT("첫 번째 메시지"));
GEngine->AddOnScreenDebugMessage(1, 5.f, FColor::Red, TEXT("두 번째 메시지"));
```

첫번째 인자를 -1로 두면 새로운 메시지가 계속 생성됨

### 🏷️ Blueprint

- 각 노드에 breakpoint 추가하고 게임 실행하면 해당 노드에서 게임이 멈춘다.
- isValid 노드를 쓰거나 Get 노드를 우클하여 Convert To Validated Get으로 바꾼 다음 Is Not Valid에 print string 노드 달아놓기
- Tools > Blueprint Debugger에서 특정 Blueprint Class의 현황을 볼 수 있다. 특정 노드의 특정 점을 우클하고 Watch This Value를 선택하면 Blueprint Debugger에서 해당 변수가 눈에 띄도록 별도로 등록된다.


## 🔧 Task Based
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

### Enhanced Input Component

1. Input Action 애셋을 생성하고 트리거를 지정한다. 
  - 지정 안 해도 기본으로 Pressed 트리거처럼 동작하긴 함
2. Input Mapping Context 애셋 (기본은 IMC_Default) 에 Input Action 애셋을 할당하고 키도 할당한다.
3. 헤더 파일에서 Input Mapping Context 애셋과 Input Action 애셋을 선언한다 
  - 블루프린트나 details에 할당된다.
  - BP_~PlayerController의 Default Mapping Context에서 Input Mapping Context 애셋이 할당되어 있는 것을 찾을 수 있다.
4. Input Mapping Context를 Subsystem->AddMappingContext(); 해준다
5. 각각의 Input Action 애셋을 EnhancedInputComponent->BindAction(); 해준다.
  - 여기서 ETriggerEvent는 트리거의 정확한 조건을 지정한다.
  - pressed면 started랑 triggered의 발동 조건이 똑같다.

| 이벤트         | 설명                   | 실행 조건                           |
| ----------- | -------------------- | ------------------------------- |
| `Started`   | 입력이 시작됨          | 키를 누른 순간 / 입력 발생                |
| `Triggered` | 트리거 조건이 충족됨      | `Hold`나 `Tap` 등의 조건이 충족된 순간 |
| `Completed` | 입력이 정상적으로 끝남     | 조건 충족 후, 키를 놓았을 때           |
| `Canceled`  | 조건 충족 전에 입력이 중단됨 | 예: `Hold` 도중 너무 빨리 뗀 경우         |


## 🛠️ TroubleShooting
---
### 🏷️ Editor

#### 기본 씬 열었는데 GPU Usage Max

- 실시간 렌더 끄기 : 뷰포트 왼쪽 상단 메뉴 → `Real-Time` 체크 해제
- 프레임 제한 : `Edit > Project Settings > Engine > General Settings` 에서 `Use Fixed Frame Rate` 활성화, `Fixed Frame Rate` 값을 60 또는 그 이하로 설정
- 뷰포트 설정 낮게 : `씬 좌측 상단 Settings > Engine Scalability Settings > Low`
- 나나이트 끄기 : `Static Mesh 에디터 > 우측 세부 설정에서 Nanite Settings > Enable Nanite 체크 해제`
- 루멘 끄기 : `Edit > Project Settings > Dynamic Global Illumination Method, Reflection Method 변경`

#### 끄고 빌드하고 다시 켜도 반영이 안됨
Development Editor로 하셈
DebugGame Editor로 하면 에디터에 반영 안됨


### 🏷️Blueprint

- BlendSpace1D 노드는 Content Drawer에서 만들어야 State Machine의 각 State에서 추가하여 사용할 수 있다.
- Animation Blueprint에서 Blend Space 1D 쓸 때 우클릭해서 Variable을 Bind해줘야 함

### 🏷️ Selection Mode




### 🏷️ Material Editor

#### Static Switch 이름 변경이 안됨
그거 말고 노드 이름이 Static Switch Parameter인 걸로 고르셈
