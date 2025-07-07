

`NetwrokManager` 
: 연결을 만들고, 세션을 호스팅하고, 클라-서버 통신을 다루는 네트워크 생명주기를 관리한다. `Demos/Prefabs/NetworkManager.prefab`에 프리팹이 있다.

`NetworkHudCanvas`
: 네트워크 연결 빠른 테스트 위해 만들어진 UI. 클라이언트로 시작할지 서버로 시작할지 정하는 버튼이 있다. `NetworkManager`가 로드될 때 어떻게 시작할지 정함. `NetworkManager` 프리팹 아래 자식에 존재. 

## 튜토

### 연결 생성 
- `NetwrokManager` 아래에 있는 `NetworkHudCanvas`에서 Auto Start Type을 Host로 변경

### 플레이어 생성
- 게임 오브젝트 하나 만들고 `NetworkObject` 컴포넌트 추가한 뒤 프리팹화
- `NetworkManager` 오브젝트 > `PlayerSpawner` > Player Prefab에 할당
- 빈 게임 오브젝트를 위치 지정 후 Spawns에 할당
- 플레이하면 1개만 스폰되는게 정상. 빌드 만들어서 켜면 자동으로 연결돼서 2개 스폰됨.

### 클라 검증 이동
- 플레이어에 `NetworkBehaviour` 상속받은 클래스 스크립트 붙여서 움직이게 한다
- 네트워크 오브젝트의 크기, 회전, 위치, 부모 정보를 동기화시키는 `NetworkTransform` 컴포넌트를 플레이어에 추가
- Client Authoritative랑 Synchronize Position enabled 돼있어야 함


### 개체 스폰/디스폰
- FishNet은 모든 network object 프리팹을 `Spawnable Prefabs`라는 배열에 저장함. NetworkManager에 있음.
- 큐브 만들어서 `NetworkObject` 컴포넌트 붙인 다음 프리팹화
- `NetwrokBehaviour` 상속받은 스크립트를 플레이어든 어디든 붙여서 큐브 생성 로직 추가


## 개념

### Communication

서버와 클라 사이 통신 방법 정리

#### SyncTypes

- 객체에 존재하는 데이터 기반 변수 또는 컬렉션.
- 서버에서 값 바꾸면 클라의 해당 객체에 실시간 반영됨.

```csharp
using FishNet.Object;
using FishNet.Object.Synchronizing;

public class Player : NetworkBehaviour
{
    readonly SyncVar<int> _health = new SyncVar<int>(100);

    public void StepOnLego()
    {
        if (!IsServerInitialized)
            return;

        _health. Value -= 10;
    }
}
```

#### Remote Procedure Calls

- 서버랑 클라에서 로직을 실행하기 위해 사용된다.
- states(SyncType)처럼 특정 주기에 제한되지 않는다. 다음 네트워크 틱 또는 최대한 빠르게 전송될 수 있다.
- 반드시 `NetworkBehaviour` 에 존재해야 한다.

```csharp
using FishNet.Object;

public class Player : NetworkBehaviour
{
    [ServerRpc]
    void UpdatePlayerName(string newName)
    {
        print($"Player {OwnerId} has updated their name to {newname}");
    }
}
```

#### Broadcasts

- 객체에 귀속되지 않는다.
- 다양한 작업에 사용할 수 있으며, 일반적으론 서버-클라 간 데이터 묶음을 전달할 때 선호된다.
- 코드의 어디에서든 송수신할 수 있으며, `NetworkBehaviour` 클래스 내에 있을 필요도 없다.

```csharp
using FishNet;
using UnityEngine;

public class ChatSystem : MonoBehaviour
{
    public void SendChatMessage(string text)
    {
        ChatBroadcast msg = new ChatBroadcast()
        {
            Message = text,
            FontColor = Color.white
        };

        InstanceFinder.ClientManager.Broadcast(msg);
    }
}
```

#### Reliable and Unreliable

Reliable : 순서대로 도착하는 것이 보장됨.
Unreliable : 대역폭은 적게 쓰지만, 순서도 도착도 보장은 안됨.


### Remote Procedure Calls

RPCs는 보내진 객체와 같은 객체에 도착하는 통신이다.
ServerRpc, ObserversRpc, TargetRpc 세 종류가 있다.
RPCs는 객체에 종속되어 있기 때문에, `NetworkBehaviour`를 상속받은 스크립트에서만 호출 가능하다.

#### ServerRpc

- 클라가 서버에서 로직을 실행할 수 있게 한다.
- 클라가 ServerRpc 메서드를 호출하면, 메서드를 실행할 데이터가 서버에 보내진다.
- ServerRpc를 사용하기 위해선 클라가 활성화돼있고, 메서드는 ServerRpc Attribute를 갖고 있어야 한다.

```csharp
[ServerRpc]
private void Update()
{
    //If owner and space bar is pressed.
    if (base.IsOwner && Input.GetKeyDown(KeyCode.Space))
        RpcSendChat("Hello world, from owner!");        
}

[ServerRpc]
private void RpcSendChat(string msg)
{
    Debug.Log($"Received {msg} on the server.");
}
```