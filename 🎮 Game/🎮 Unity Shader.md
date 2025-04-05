


### 개념

전체 흐름
`struct appdata`는 World Space의 데이터를 들고 있다.
vert 함수는  `struct appdata`를 조작하여 `struct v2f`로 보낸다.

`struct v2f`는 Clipping Space의 데이터를 들고 있다.
frag 함수는 `struct v2f`를 조작하여 최종적으로 렌더링한다.

코드 흐름
```
Shader
 └── Properties         ← 사용자 입력값 정의 (텍스처, 색 등)
 └── SubShader          ← 실제 쉐이더 코드 블록
     └── CGPROGRAM      ← HLSL/Cg 코드 작성 공간
         └── #pragma surface ← 이 쉐이더의 성격 설정
         └── Input / surf()  ← 텍스처 샘플링, 표면 정보 결정
     └── ENDCG
 └── Fallback           ← 이 쉐이더가 안 될 때 대체할 것
```

Surface Shader
- Unity Built-in render pipeline 전용 추상화 시스템
- Unity가 자동으로 라이트 계산, 그림자, 라이트맵 등을 다 처리해준다
- 개발자는 `surf()` 함수만 작성하면 나머지는 Unity가 채워준다.

Surface Shader에서 채워야 하는 것들
- `void surf(Input IN, inout SurfaceOutput o)`
- `IN` : Unity가 자동으로 채워주는 입력값들 (UV, worldPos 등)
- `o` : 직접 설정한 표면 결과 (Albedo, Normal 등)

Illumination Models
- Flat : 폴리곤 별로 normal을 하나로 합쳐 계산
- Gouraud : 폴리곤별로 vertex별 normal을 interpolate하여  계산
- Phong : 픽셀별로 vertex별 normal을 interpolate하여 계산
- 유니티는 기본으로 Phong 사용하지만, Model Import Settings에서 Normal을 Calculate로 바꾸고 Smooth Angle을 0으로 줄이면 Flat해짐

Input
- worldRefl : 내가 보는 방향과 표면의 노멀을 기준으로 계산된 반사 방향
	- worldRefl 이용하려고 할 때 Normal을 수정하면 오류가 생긴다. normal과 worldRefl은 연관돼있기 때문. worldRefl에 INTERNAL_DATA 붙이면 영향 안 받는 별개의 worldRefl 사용 가능.

Buffer
- frame buffer : 스크린에 있는 모든 픽셀의 색깔 정보 담음
- depth buffer (z buffer) : 픽셀의 깊이 정보 담음
  - frame buffer에 그려지기 전에 depth buffer에서 앞에 그려진거 있나 확인
- G-Buffer (Geometry Buffer) : Deffered rendering에 쓰인다.

Rendering Types
- Forward Rendering : Geometry > Vertex Shader > Geometry Shader > Fragment Shader Lighting (픽셀별로 계산됨) > Frame Buffer
- Deferred Rendering : Forward Rendering이랑 거의 똑같은데 Fragment Shader 까지 한 결과물을 한꺼번에 G-Buffer에 넣고 Lighting 얹어서 Frame Buffer에 보냄

Render Queues
- Background : 1000
- Geometry : 2000
- AlphaTest : 2450
- Transparent : 3000
- Overlay : 4000
- Material Inspector에서 설정하거나, 
  Shader에서 `Tags { "Queue" = "Geometry+100" } 으로 설정 가능

시스템 예약 시맨틱(System Semantic)
: 각 셰이더 단계에서 "이 값이 어떤 용도로 쓰이는지" GPU에게 알려준다.

| 시맨틱 | 의미 |
|--------|------|
| `SV_Position` | 정점 셰이더의 출력 위치 (클립 공간) |
| `SV_Target`   | 픽셀 셰이더의 출력 색상 |
| `SV_Depth`    | 픽셀 셰이더가 직접 깊이값을 쓸 때 |
| `SV_VertexID` | 정점 인덱스 |
| `SV_InstanceID` | 인스턴싱된 개체의 ID |

가로, 세로, 높이 순서
world space에선 x,z,y 순이라면
clipping space에서는 x,y,z 순이다.

View Space : 카메라를 원점(0, 0, 0)에 두고, 그 시점에서 본 좌표계

### 구조

SubShader
- 쉐이더의 구현이 들어가는 블록
- 하나의 쉐이더 안에 여러 SubShader 넣을 수 있다
- 그래픽 카드 성능이나 플랫폼에 따라 SubShader 자동 선택
- 일종의 "플랜 A / 플랜 B / 플랜 C" 같은 역할

CGPROGRAM ~ ENDCG
- 이 사이만 실제 쉐이더 코드로 인식된다
- `CGPROGRAM`은 "Cg 언어 프로그램"의 줄임말, 옛날에 쓰던거고, 지금은 HLSL로 컴파일됨.

`#pragma`
- 컴파일러에게 쉐이더 정보 알려주는 지시어
- `surface surf` : surf 함수가 이 쉐이더의 surface 함수다
- `Lambert` : 조명 모델은 Lambert다

surface
- 표면의 재질 정보를 정의하는 함수
- Unity가 각 픽셀마다 해당 함수 호출해서 Albedo, Smootheness, Normal 등 결정
- SurfaceOutput 구조체는 Unity가 조명 계산에 쓰는 표면 정보들 담고 있음

Fallback
- 해당 쉐이더가 지원되지 않을 때, 대신 쓸 기본 쉐이더

### 함수

내적 : dot()
제곱 : pow()
소수 부분만 : frac()

#### tex2D와 tex2DProj의 차이

| 항목 | `tex2D` | `tex2Dproj` |
|------|---------|--------------|
| 입력 타입 | `float2` (UV) | `float4` (투영 좌표) |
| 내부 동작 | 그대로 사용 | `(x / w, y / w)`로 계산 |
| 보간 방식 | 선형 보간 (float2 기준) | **투영 보간** (정점 간의 w 보정 포함) |
| 사용 목적 | 일반적인 UV 샘플링 | GrabPass, Projector, ShadowMap 등 투영 필요 시 |
| 필요 조건 | 일반 텍스처 좌표만 있으면 됨 | 클립 공간 또는 투영 좌표 필요 |
| 예시 사용 | 일반 메시 텍스처, 라이트맵 등 | 화면 왜곡, 그림자 투사, 스크린 공간 이펙트 등 |


### 자료형

Basic Data Types
- float : 32 bit. 정확도 가장 높음. 월드 위치, 텍스쳐 좌표, 계산에 사용됨.
- half : 16 bit. float의 절반 크기. 짧은 벡터, 방향, hdr 컬러에 사용됨.
- fixed : 11bit. 가장 낮은 정확도. 보통의 컬러 연산에 사용됨.
- int : 카운터나 배열 인덱스로 사용됨.

Texture Data Types
- sampler2D : 일반 텍스쳐
- samplerCUBD : 큐브맵 텍스쳐
- 각각의 뒤에 `_half` 붙이면 low precision, `_float` 붙이면 high precision

Packed Array
- 자료형 뒤에 배열의 길이를 붙이면 된다. 예시) `fixed4 colour1 = (0,1,1,0);`
- r,g,b,a 또는 x,y,z,w로 각 요소 접근. 예시) `colour1.r = 1;`
- `colour1.xgb` 이런 식으로 섞어서 쓸 순 없다. `colour1.xzy`는 가능함.
- 서로 다른 크기여도 할당하거나 연산할 수 있다. 예시) `fixed3 colour3; colour3 = colour1.rgb;`
- `fixed3 c = 1;`과 `fixed3 c = (1,1,1);`은 같은 연산이다.
- 연산할 채널과 순서를 마음대로 바꿀 수 있다. 예시) `colour1.rg = colour2.gr;`

Packed Matrices
- 선언 방법 : `float4x4 matrix;`
- 개별 접근 : `float myValue = matrix._m00;`
- chaining 예시 1 : `fixed4 colour = matrix._m00_m01_m02_m04;`
- chaining 예시 2 : `fixed4 colour = matrix[0];`

- `in` : 읽기 전용. 값 받아서 읽기만 가능.
- `out` : 쓰기 전용. 함수 내부에서 초기화해서 밖으로 전달.
- `inout` : 읽기 + 쓰기. 받아온 값 수정해서 돌려보냄.

appdata 구조체 (버텍스 셰이더 입력 데이터)

- `float4 vertex : POSITION;`: 정점의 위치
- `float3 normal : NORMAL;`: 정점의 법선 벡터
- `float4 tangent : TANGENT;`: 정점의 탄젠트 벡터
- `float2 uv : TEXCOORD0;`: 첫 번째 텍스처 좌표
- `float2 uv1 : TEXCOORD1;`: 두 번째 텍스처 좌표
- `float4 color : COLOR;`: 정점의 색상
- appdata_full : 미리 정의된 버텍스 입력 구조체. 직접 필요한거 선언 안해도 됨.


v2f 구조체 (버텍스 셰이더에서 프래그먼트 셰이더로 전달되는 데이터)

- `float4 vertex : SV_POSITION;`: 클립 공간에서의 정점 위치
- `float2 uv : TEXCOORD0;`: 보간된 텍스처 좌표
- `float3 normal : NORMAL;`: 보간된 법선 벡터
- `float4 color : COLOR;`: 보간된 색상
- `UNITY_FOG_COORDS(1);`: 안개 효과를 위한 좌표
- `float3 worldPos : TEXCOORD2;`: 월드 공간에서의 정점 위치