1. 노말맵 파일(.exr)은 Texture Type을 Normal map으로 바꿔야 한다
2. V를 누르면 정점을 따라 스내핑 배치 가능



**Cinemachine 따라가기 덜덜 떨림**
플레이어 오브젝트에 있는 `Rigidbody2D` 컴포넌트에서 `Interpolation`을 `Interpolate`로 설정하면 된다

**'Vector2' is an ambiguous reference between 'UnityEngine.Vector2' and 'System.Numerics.Vector2'**
using System.Numerics; 삭제하기

**탑뷰 오브젝트 순서 정렬**
```C#
public class Ysort : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        var spriteRenderer = GetComponent<SpriteRenderer>();
        spriteRenderer.sortingOrder =
            -(int)(transform.position.y);
    }
}
```

```c#
Using the generic type 'IEnumerator<T>' requires 1 type argument CS0305
```

using System.Collections; 추가

스크립트 상에서 Debug.Break() 호출하면 에디터 일시정지됨
보통 디버그 레이캐스트 그리고 바로 사라질때 쓰거나 
한프레임씩 인스펙터 값 확인할때 유용함

일시정지 후 맨 오른쪽 버튼이 한프레임씩 진행하는거


 **GameObject의 특성**
 - GameObject는 클래스이다. 객체가 아니다.
 - Hierarchy 창에 계층구조를 이루는 게임 오브젝트 객체들을 의미한다.
 - 스크립트에서 GameObject를 쓰는 이유는 다른 게임오브젝트를 호출하기 위함이다.
**gameObject의 특성**
- gameObject는 클래스가 아니다. 객체이다.
- C# 스크립트 생성후 유니티 Hierarchy내 임의의 게임오브젝트로 스크립트를 Add Component하는데,  이 과정은 일반적인 객체 생성 과정인  GameObject gameObject = new GameObject(); 명령어를 자동 선언한 것이나 마찬가지이므로 선언하지 않아도 gameObject는 스크립트로 바로 참조가 가능하다.
- **쉽게 말하면, 해당 컴포넌트에 할당된 자기 자신이다.**
- 스크립트에서 gameObject를 사용하면, 해당 게임 오브젝트를 호출한다.

**아무 키나 누르면 작동** : Input.anyKeyDown

**상하좌우 키입력**
movement.x = Input.GetAxisRaw("Horizontal");
movement.y = Input.GetAxisRaw("Vertical");

**부모 함수에 대한 상대 좌표**
transform.localPosition


## 설정
---

Edit → Project Settings → Editor → Enter Play Mode Options



## ㅇㅇ



## ㅇㅇ