- [[#튜토|튜토]]
	- [[#튜토#연결 생성|연결 생성]]
	- [[#튜토#플레이어 생성|플레이어 생성]]
	- [[#튜토#클라 검증 이동|클라 검증 이동]]
	- [[#튜토#개체 스폰/디스폰|개체 스폰/디스폰]]
- [[#Communication|Communication]]
	- [[#Communication#SyncTypes|SyncTypes]]
	- [[#Communication#Remote Procedure Calls|Remote Procedure Calls]]
	- [[#Communication#Broadcasts|Broadcasts]]
	- [[#Communication#Reliable and Unreliable|Reliable and Unreliable]]
- [[#Remote Procedure Calls (RPCs)|Remote Procedure Calls (RPCs)]]
	- [[#Remote Procedure Calls (RPCs)#ServerRpc|ServerRpc]]




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
- `NetwrokBehaviour` 상속받은 스크립트를 플레이어에 붙여서 큐브 생성 로직 추가
  - `NetworkObject`가 fishnet의 `ServerManager`에게 이 물체 스폰하라는 뜻. 서버가 연결된 모든 클라와 나중에 연결된 클라에게 이 오브젝트 복사본을 생성하라고 지시한다.
- Rigidbody 추가하면 완벽하게 큐브 위치 sync되진 않음. `Spawn()` 때 FishNet이 자동으로 sync해준 이후로 sync하지 않았기 때문.
- `OnStartServer` 메서드에 코루틴 호출해서 시간 지나면 오브젝트 없어지게 함. `OnStartServer`는 오브젝트가 네트워크에 초기화될 때 서버에서 호출됨. Despawn()은 서버에서 호출해야 함.

### SyncVar로 색깔 싱크
- `public readonly SyncVar<Color>` 변수 선언. readonly지만 get set 가능.
- `color.OnChange`에 색깔 바꾸는 메서드 구독.



## Communication
---

서버와 클라 사이 통신 방법 정리

### SyncTypes

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

### Remote Procedure Calls

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

### Broadcasts

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

### Reliable and Unreliable

Reliable : 순서대로 도착하는 것이 보장됨.
Unreliable : 대역폭은 적게 쓰지만, 순서도 도착도 보장은 안됨.


## SyncTypes
---

- 서버가 값을 바꾸면 네트워크에 있는 클라들에 자동으로 싱크함.
 - SyncVar, SyncDictionary, SyncList, custom SyncTypes 등 여러 종류가 있다.
 - SyncType 값 변경하면 바꾼 놈만 간다. 예를 들어, SyncList에 값 10개 있고 하나 추가했으면 추가한 하나만 보내진다.
 - SyncType들은 custom 자료형에 대해 자동으로 직렬화해준다.
 
 - SyncVar는 `OnDestroy` 이전에 초기화되므로, 거기서 접근 못 함.
 - `Awake`에서 SyncType 변경하면 서버와 클라 모두에 영향 미쳐서 별도 싱크 필요 없음. 초기화 이후에 싱크 맞추고 싶으면 `OnStartServer` 사용.
-  SendRate를 0f로 설정하면 SyncType들을 매 network tick에 보낼 수 있게 한다.

### Host Client Limitations

클라와 서버를 동일 빌드에서 돌리면 약간의 제한이 발생함.
호스트 클라일 때 `asServer` 인자가 false면 이전값이 null이나 현재값으로 찍힐 수 있다.

```cs
// This example assumes you are acting as the host client.
// We will imagine previous value was 10, and next is 20.
private void _mySyncVar_OnChange(int prev, int next, bool asServer)
{
    // Only run the logic using the previous value if being called
    // with asServer true, or if only the client is started.
    if (asServer || base.IsClientOnlyStarted)
        DoSomething(prev, next);
}
```


## Remote Procedure Calls (RPCs)
---

- RPCs는 보내진 객체와 같은 객체에 도착하는 통신이다.
- ServerRpc, ObserversRpc, TargetRpc 세 종류가 있다.
- RPCs는 객체에 종속되어 있기 때문에, `NetworkBehaviour`를 상속받은 스크립트에서만 호출 가능하다.

### ServerRpc

- 클라가 서버에서 로직을 실행할 수 있게 한다.
- 클라가 ServerRpc 메서드를 호출하면, 메서드를 실행할 데이터가 서버에 보내진다.
- ServerRpc를 사용하기 위해선 클라가 활성화돼있고, 메서드는 ServerRpc Attribute를 갖고 있어야 한다.

```csharp
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

- 기본적으론 객체의 owner만 ServerRpc를 보낼 수 있다. 
- RequireOwnership을 false로 설정하면 다른 클라도 호출 가능하다.
- RPC 호출할 때 마지막 인자로 NetworkConnection type을 null로 두면 어떤 연결이 RPC를 호출하고 있는지 확인 가능. 그럼 NetworkConnection 인자에 자동으로 어떤 클라가 ServerRpc 호출중인지 채워진다.

```csharp
[ServerRpc(RequireOwnership = false)]
private void RpcSendChat(string msg, NetworkConnection conn = null)
{
    Debug.Log($"Received {msg} on the server from connection {conn.ClientId}.");
}
```

### ObserversRpc

- 서버가 클라에서 로직을 실행할 수 있게 한다.
- 관찰 중인 클라만 받아서 로직을 실행할 수 있다.
- 옵저버들은 `Network Observer` 컴포넌트를 사용하여 설정한다.
- ObserverRpc를 사용하려면 `ObserverRpc` attribute를 붙여야 한다.

```csharp
private void FixedUpdate()
{
    RpcSetNumber(Time.frameCount);
}

[ObserversRpc]
private void RpcSetNumber(int next)
{
    Debug.Log($"Received number {next} from the server.");
}
```

- `ObserverRpc` attribute의 BufferLast를 true로 설정하면 ObserversRpc를 통해 전송된 최신 값들이, 새로 접속한 클라에게도 자동으로 전달되도록 설정할 수 있다.
```cs
[ObserversRpc(ExcludeOwner = true, BufferLast = true)]
private void RpcSetNumber(int next)
{
    //This won't run on owner and will send to new clients.
    Debug.Log($"Received number {next} from the server.");
}
```
(owner에는 안 보내고 새 클라에 보내는 예제)

### TargetRpc

- 특정 클라에서 로직을 돌리게 한다. `TargetRpc` attribute를 붙이면 된다.
- TargetRpc를 보낼 때 첫 번째 인자는 반드시 `NetworkConnection`이어야 한다. 이 연결이 데이터가 가는 곳이다.

```cs
private void UpdateOwnersAmmo()
{
    /* Even though this example passes in owner, you can send to
    * any connection that is an observer. */
    RpcSetAmmo(base.Owner, 10);
}

[TargetRpc]
private void RpcSetAmmo(NetworkConnection conn, int newAmmo)
{
    //This might be something you only want the owner to be aware of.
    _myAmmo = newAmmo;
}
```

### Multi-Purpose Rpc

- 하나의 메서드가 TargetRpc와 ObserversRpc 둘 다 여야 할 때 사용한다.

```cs
[ObserversRpc][TargetRpc]
private void DisplayChat(NetworkConnection target, string sender, string message)
{
    Debug.Log($"{sender}: {message}."); //Display a message from sender.
}

[Server]
private void SendChatMessage()
{
    //Send to only the owner.
    DisplayChat(base.Owner, "Bob", "Hello world");
    //Send to everyone.
    DisplayChat(null, "Bob", "Hello world");
}
```

### Channels

- `Channeltype`을 rpc의 마지막 인자로 넣어서 reliable 또는 unreliable하게 호출 가능하다.
- 추가된 Channel 인자로 어떤 채널에 데이터가 도착할지 알 수도 있다.

```cs
private bool _reliable;
private void FixedUpdate()
{
    //Reliable or unreliable can be switched at runtime!
    _reliable = !_reliable;
    
    Channel channel = (_reliable) ? Channel.Reliable : Channel.Unreliable;
    RpcTest("Anything", channel);
}

/* This example uses ServerRpc, but any RPC will work.
* Although this example shows a default value for the channel,
* you do not need to include it. */
[ServerRpc]
private void RpcTest(string txt, Channel channel = Channel.Reliable)
{
    if (channel == Channel.Reliable)
        Debug.Log("Message received! I never doubted you.");
    else if (channel == Channel.Unreliable)
        Debug.Log($"Glad you got here, I wasn't sure you'd make it.");
}
```

- 만약 ServerRpc이고 NetworkConnection을 기본값 null로 사용하고 있다면 Channel 인자는 끝에서 두 번째 NetworkConnection 전에 반드시 들어가야 한다.

```cs
/* Example of using Channel with a ServerRpc that
* also provides the calling connection. */
[ServerRpc(RequireOwnership = false)]
private void RpcTest(string txt, Channel channel = Channel.Reliable, NetworkConnection sender = null)
{
    Debug.Log($"Received on channel {channel} from {sender.ClientId}.");
}
```

### RunLocally

- 모든 RPC type들은 RunLocally 필드를 사용할 수 있다.
- RunLocally가 true면 메서드가 보내질 때, 호출한 쪽에서도 실행된다.

```cs
//Keeping in mind all RPC types can use RunLocally.
[ServerRpc(RunLocally = true)]
private void RpcTest()
{
    //This debug will print on the server and the client calling the RPC.
    Debug.Log("Rpc Test!");
}
```

### DataLength

- 데이터 엄청 많이 보내려면 데이터의 RPC attribute에서 최대 크기를 설정해야 한다. 그래야 resizing이랑 allocation을 방지해서 퍼포먼스 좋아짐.

```cs
//This implies we know the data will never be larger than 3500 bytes.
//If the data is larger then a resize will occur resulting in garbage collection.
[ServerRpc(DataLength = 3500)]
private void ServerSendBytes(byte[] data) {}
```

