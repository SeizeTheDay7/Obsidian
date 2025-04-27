
## 📌 팁
---




## ⚙️ 설정
---

- Auto Exposure 설정 : 좌측 상단 세번째 버튼 > Game Settings



## 🖱️ 조작
---

- Content Drawer 열기/닫기 : Ctrl + Space

### 🏷️ Level Editor

- 카메라 이동 속도 조절 : 우클 + 스크롤
- 게임 화면 : G

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



## 📄 Manual
---

- Map은 File > New Level로 만들어야 Level Template 사용 가능
- Engine Content 보는 법 : Content Drawer > 우측 상단 Settings > Show Engine Content
- 3D Model Import할 때 필요 없으면 Import Material 끄기

### Sky Light
- Sky Light  추가
- Visual Effects > Sky Atmosphere 추가
- Directional Light 추가
- Details > Affects World 체크 해제 후 다시 체크

### Post Process Volume

- 적용 범위 global로 : Details > Post Process Volume Settings > Infinite Esxtent (Unbound)



## 🦫 디버깅
---

### 🏷️ Level Editor

#### 기본 씬 열었는데 GPU Usage Max

- 실시간 렌더 끄기 : 뷰포트 왼쪽 상단 메뉴 → `Real-Time` 체크 해제
- 프레임 제한 : `Edit > Project Settings > Engine > General Settings` 에서 `Use Fixed Frame Rate` 활성화, `Fixed Frame Rate` 값을 60 또는 그 이하로 설정
- 뷰포트 설정 낮게 : `씬 좌측 상단 Settings > Engine Scalability Settings > Low`
- 나나이트 끄기 : `Static Mesh 에디터 > 우측 세부 설정에서 Nanite Settings > Enable Nanite 체크 해제`
- 루멘 끄기 : `Edit > Project Settings > Dynamic Global Illumination Method, Reflection Method 변경`

#### 그림자 노이즈 없애기
Post Process Volume > Details > Lumen Global Volume > Final Gather Quality 증가


### 🏷️ Material Editor

#### Static Switch 이름 변경이 안됨
노드 이름이 Static Switch Parameter인 걸로 고르셈