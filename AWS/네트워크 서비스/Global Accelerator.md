# Global Accelerator

### Global Accelerator

- 가장 가까운 위치로 트래픽을 라우팅하여 인터넷 대기시간을 줄이고 전송 성능을 향상하는 서비스

### 미사용 시

![image](https://github.com/pokabook/TIL/assets/103029701/56753c9d-b6ea-4a0e-ad5d-48106c6f26ca)

- **Global Accelerator**를 미사용시 서버로부터 지리적으로 먼 사용자는 많은 인터넷 라우팅을 하여 속도가 느림

### 사용 시

![image](https://github.com/pokabook/TIL/assets/103029701/112b4b39-c47f-45e1-bdcd-c36e1807d01b)

- **Global Accelerator**를 사용하면 사용자는 가까운 거리의 Edge Location으로 라우팅하고 Edge Location과 서버는 AWS 전용 네트워크 연결로 전송속도가 빠름

### 고정 Anycast IP 주소
![test](https://github.com/pokabook/TIL/assets/103029701/e8377843-3a51-4192-8bb5-aa3ef6d736de)

- **Global Accelerator**에는 2개의 **Anycast** 퍼블릭 고정 IP가 생성됨 (IP 주소 연결 방식)
- **EIP**, **EC2** 인스턴스, **ALB**, **NLB** 등의 AWS **Endpoint**를 연결하여 사용 가능
- 애플리케이션의 Health Check 기능을 통해 하나의 서버 장애 발생시 다른 서버로 라우팅 가능

### Vs CloudFront

- **CloudFront**
    - 변화하는 동적인 IP 주소 세트를 사용
    - 전 세계에 분포된 Edge Location을 사용
    - Edge Location을 콘텐츠를 캐시하는데 사용
    - HTTP 프로토콜을 처리하는데 적합
    - 캐시 가능한 콘텐츠(이미지, 비디오)와 동적인 콘텐츠(API 가속화 및 동적 사이트 제공)의 성능 개선
- **Global Accelerator**
    - 고정된 IP 주소를 사용
    - 전 세계에 분포된 엣지 로케이션을 사용
    - 엣지 로케이션을 가장 가까운 리전의 엔드포인트로 최적화된 경로를 찾는데 사용
    - TCP, UDP 프로토콜을 처리하는데 적합
    - TCP 또는 UDP를 사용하는 광범위한 애플리케이션의 성능을 개선
    - Non-HTTP를 사용하는 게임(UDP), 미디어, VoIP, 모바일 앱, IoT 등의 다양한 애플리케이션의 성능을 향상
    - 고정 IP 주소가 필요한 HTTP에 사용