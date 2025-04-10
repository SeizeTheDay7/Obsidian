



## 🦫 디버깅
---

### 🏷️ Editor

#### 기본 씬 열었는데 GPU Usage Max

1. **에디터 뷰포트 리얼타임 활성화**
   - 언리얼은 기본적으로 뷰포트에 실시간 렌더링이 켜져 있다. 아무것도 하지 않아도 GPU는 계속 씬을 렌더링한다.
   - ▶ **해결 방법**: 뷰포트 왼쪽 상단 메뉴 → `Real-Time` 체크 해제

2. **프레임 제한 없음**
   - 기본 상태에서는 프레임 제한이 없어서 GPU가 가능한 한 최대 프레임으로 렌더링을 시도한다.
   - ▶ **해결 방법**: `Edit > Project Settings > Engine > General Settings` 에서 `Use Fixed Frame Rate` 활성화, `Fixed Frame Rate` 값을 60 또는 그 이하로 설정

3. **편집기 스케일러가 ‘에픽’으로 설정되어 있음**
   - 고품질 뷰포트 설정일 경우 GPU 부하가 크다.
   - ▶ **해결 방법**: `씬 좌측 상단 Settings > Engine Scalability Settings > Low` 로 수동 설정
