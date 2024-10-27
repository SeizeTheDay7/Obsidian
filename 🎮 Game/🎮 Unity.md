- [[#⚙️ 설정|⚙️ 설정]]
	- [[#⚙️ 설정#빠르게 재생|빠르게 재생]]
	- [[#⚙️ 설정#애셋 직렬화 방식 통일|애셋 직렬화 방식 통일]]
- [[#💾 개념|💾 개념]]
- [[#📋 정보|📋 정보]]
- [[#🦫 디버깅|🦫 디버깅]]
		- [[#애셋 직렬화 방식 통일#Cinemachine 따라가기 덜덜 떨림|Cinemachine 따라가기 덜덜 떨림]]





## ⚙️ 설정
---

### 🏷️ 성능

#### 수정 후 빠르게 재생
Edit → Project Settings → Editor → Enter Play Mode Options


### 🏷️ 디버그

#### 애셋 직렬화 방식 통일
Edit - Project Settings - Editor - Asset Serialization - Force Text로 바꾸기





## 💾 개념
---
### .meta 파일
컴포넌트 간의 연결과 같은 메타 정보들을 담고 있다.
유니티 에디터에서 파일 위치나 이름 바꾼거 아니면 이거 때문에 정보 소실.

깃허브에 커밋할 때 .meta 빠뜨리면 안되고
외부에 깃 말고 보낼 땐 .unitypackage로 만들어라.





## 📋 정보
---
### 🏷️ Script

#### public vs [SerializeField]
둘 다 Inspector 창에서 수정이 가능하지만, 
SerializeField는 외부 스크립트에서 수정할 수 없는 캡슐화가 이루어진다.

#### private void vs void
접근 제한자는 생략해도 되지만 가독성을 위해 명시적으로 추가하는게 좋다.

### 🏷️ UI
#### EventSystem
UI 추가하면 Canvas와 함께 씬에 추가되는 요소.
사용자 입력과 UI 요소를 이어주는 오브젝트이다.
EventSystem을 사용하면 입력 설정을 변경할 수 있다.

#### Rect Transform







## 🦫 디버깅
---

### Cinemachine 따라가기 덜덜 떨림
플레이어 오브젝트에 있는 `Rigidbody2D` 컴포넌트에서 
`Interpolation`을 `Interpolate`로 설정

### 깃 pull 할 때마다 메타파일 갱신

1. 애셋 직렬화 방식 : Project Settings - Editor - Asset Serialization - Force Text 통일
2. Project Settings - Editor - Version Control - Visible Meta Files 통일

