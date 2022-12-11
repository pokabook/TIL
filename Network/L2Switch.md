# L2 스위치

![Untitled](https://media.discordapp.net/attachments/901506770457989150/1051563683534344202/Untitled.png)

# 스위치란?

> 여기서 말하는 스위치는 2계층에서 쓰는 L2이다.
네트워크 망에서 가장 핵심장비이며 2계층 주소인 MAC 주소를 기반으로 동작한다.
> 


&nbsp;

# 역할

### **네트워크의 중재자**

네트워크 중간에서 패킷을 받아 목적지에게만 전송한다.

### **동시 통신, 패킷 충돌X**

여러 장비가 서로 간섭 및 패킷 충돌 없이 동시에 통신하도록 도와준다.

### **네트워크 효율성 ↑**

통신을 위해 기다리거나 충돌로 인해 대기하는 문제를 방지하여 네트워크 전체의 통신 효율성이 향상된다.

### **장비의 위치를 파악하고 통신 시작시 자신이 알고 있는 위치로 패킷 전송**

이를 위해서 **MAC 주소 테이블**을 가지고 있다.

스위치는 전송하려는 패킷의 헤더 안에 잇는 MAC 주소를 확인하고 **MAC 주소 테이블**
 에서 해당 주소가 어느 포트에 있는지 확인해 해당 패킷을 그 포트로만 전송한다.

&nbsp;
# 동작 방식

![https://postfiles.pstatic.net/MjAxODEwMjlfMjA5/MDAxNTQwODIwMTA2NTM3.gCVNU4mB9P46EubPKaGZifW5J4Xp7nvnVTffQ49MPdQg.Iivzc5gikUMCqcK4m5_qggFhL5V69a_8GFaP5Q2_3f8g.PNG.djg04115/%EB%8F%84%ED%91%9C1.png?type=w773](https://postfiles.pstatic.net/MjAxODEwMjlfMjA5/MDAxNTQwODIwMTA2NTM3.gCVNU4mB9P46EubPKaGZifW5J4Xp7nvnVTffQ49MPdQg.Iivzc5gikUMCqcK4m5_qggFhL5V69a_8GFaP5Q2_3f8g.PNG.djg04115/%EB%8F%84%ED%91%9C1.png?type=w773)

- **Flooding**
    
    플러딩은 스위치에 연결된 모든 포트로 패킷을 전달하는 방식을 말한다.
    
    스위치는 처음 부팅하면 **MAC 주소 테이블**에 네트워크 관련 정보가 아무것도 없어 허브처럼 동작한다. 허브는 패킷이 들어온 포트를 제외하고 모든 포트로 패킷을 전달하는데 이러한 동작을 플러딩이라고 한다.
    
    - MAC 주소 테이블에는 언제 정보가 쌓이나?
        
        💡 패킷이 스위치에 들어오면 해당 패킷의 MAC 주소를 보고 이를 학습해 MAC 주소 테이블에 저장한다.
    
    - MAC 주소를 학습한다는 의미
    
        💡 스위치는 **MAC 주소 테이블**을 만들고 유지를 하는데 이 과정을 **Address Learning**이라고 한다.
    
- **Address Learning**
    
    스위치가 목적지 포트로 적확히 포워딩하려면 **MAC 주소 테이블**을 만들고 올바르게 유지해야 하는데 이 과정을 **Address Learning**이라고 한다.
    
    **러닝 과정**
    
    > 예시 : 출발지 MAC (AA-AA-AA), 스위치 Port : 4321
    > 
    > 1. 스위치에 *[ 출발지 MAC (AA-AA-AA), 스위치 Port : 1 ]* 정보를 가진 패킷이 들어왔다.
    > 2. 스위치는 MAC 주소 테이블에 출발지 MAC주소와 포트번호를 기록한다.
    > 3. 기록된 정보를 가지고 스위치 1번 포트에 AA-AA-AA주소를 가진 장비가 붙어 있다는 것을 습득한다.
    
    브로드 캐스트와 멀티 캐스트에 대한 MAC 주소는 학습할 수 없다고 한다. 이유는 브로드캐스트와 멀티캐스트 모두 목적지 MAC 주소 필드를 사용해서라고 한다.
    
    (브로드 캐스트 같은 경우는 주소가 FFFF.FFFFF.FFFF)
    
- **Forwarding**
    
    패킷이 스위치에 들어온 경우 목적지 MAC를 확인한 후 MAC 주소 테이블을 통해 해당 포트로 전송하는 것
    
- **Filtering**
    
    출발지, 목적지가 동일 네트워크 존재 시 다른 네트워크로 전파 차단
    
- **Aging**
    
    MAC 주소 테이블에 저장된 후 Aging이 가동되어 300초 동안 테이블에 저장된 주소의 프레임이 더이상 오지 않으면 테이블에서 삭제한다.
    
Forwarding 과 Filtering은 유니캐스트에 대해서만 작업을 수행한다.

    ❌ Unknown 유니캐스트 : MAC 주소 테이블에 정보가 없으므로 수행 불가능
    ❌ 브로드캐스트, 멀티캐스트 : 출발지 MAC 주소를 사용하지 않으므로 수행 불가능

# 작동 방식

**cut-through**

수신 frame의 목적지 주소만 확인 후 포워딩

- `처리속도 ↑`
- `에러 감지가 어려움`

---

**store-and-forwarding**

수신 frame 전체 수신 및 체크 후 forwarding

- `처리속도 ↓`
- `에러 감지 용이`

---

**Fragment Free**

Frame 앞 64byte만 읽고 에러 처리, 포워딩

- `적당한 처리 속도`
- `적당한 에러 감지`