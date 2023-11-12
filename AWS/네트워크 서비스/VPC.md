# VPC (Virtual Private Network Computing)

### VPC

![image](https://github.com/pokabook/TIL/assets/103029701/1e026186-c3d0-41fd-83a8-2480a1169439)

- AWS 계정의 가상 네트워크
- IPv4 주소 범위를 CIDR 블록 형태로 지정
- CIDR 블록 사이즈는 /16 ~ /28 넷마스크
- VPC 생성 후 CIDR 범위 수정은 불가하나 새 CIDR 블록 추가 가능
- IPv6 주소 범위 지정은 옵션
- IP 대역(CIDR)을 할당하여 가상 사설 네트워크를 구성
- IPv4 / Ipv6 Address Blocks 지원
- 서브넷 / 라우팅 테이블로 서브네팅
- 인터넷 게이트웨이를 연결하여 외부로 인터넷 통신
- VPC Flow Log 활성화하여 트래픽 캡쳐
- 프라이빗 엔드포인트 서비스 제공
- VPC peering / Transit Gateway로 VPC간 연동
- AWS Transit Gateway를 통한 multi-cast

### Subnet

- VPC의 IP 주소 범위
- CIDR 블록 형태로 IP 주소 범위 지정
- CIDR  블록 사이즈는 /16 ~ /28 넷마스크 사용 가능
- 서브넷 생성시 가용영역을 지정하며 1개의 가용영역만 지정 가능
- 서브넷 범위는 VPC의 CIDR 블록 주소 내에서 생성 가능
- 서브넷 끼리의 IP 주소 중첩하여 생성 불가
- 생성된 서브넷의 IPv4 CIDR 블록 주소는 추가하거나 수정이 안되며 삭제 후 새로 생성만 가능
- 서브넷 생성 후 AWS는 네트워킹 목적으로 처음 4개의 IP 주소와 마지막 1개 IP 주소를 예약
    >   - 10.0.0.0/24 서브넷을 생성
    >   - 10.0.0.0 : Network ID
    >   - 10.0.0.1 : Gateway
    >   - 10.0.0.2 : DNS
    >   - 10.0.0.3 : Reserved
    >   - 10.0.0.255 : Broadcast

### Routing Table

![image](https://github.com/pokabook/TIL/assets/103029701/fd3ca2b0-3cc8-446e-86e2-fc20944b9f4d)

- 라우팅 규칙을 통해 네트워크 트래픽이 전송되는 위치를 결정

### Internet Gateway

- VPC와 인터넷 간에 통신을 할 수 있게 함
- 퍼블릿 IPv4가 할당된 인스턴스에 대해 1 : 1 NAT (네트워크 주소 변환)을 수행
- 라우팅 테이블의 대상(Target) 역할
- 트래픽을 인터넷에 전달하기 위해서는 서브넷의 라우팅 테이블에 인터넷 게이트웨이를 대상으로 추가해야함
- VPC에서 인터넷 외부로만 트래픽을 허용하는 송신전용(egress-only) 인터넷 게이트웨이 구성 가능
- Public Subnet: 서브넷이 인터넷 게이트웨이로 바로 연결(라우팅)되는 경우
- Private Subnet: 서브넷이 인터넷 게이트웨이로 바로 연결(라우팅)되지 않는 경우
- Protected Subnet: 서브넷이 아무것에도 연결되어 있지 않는 경우

### Peering

![image](https://github.com/pokabook/TIL/assets/103029701/e3f89985-8b0f-4279-a5e0-96bc67bd8811)

- 서로 다른 VPC끼리 동일한 네트워크에 존재하는 것처럼 통신이 가능
- 계정간 연결, 리전간 연결이 가능
- 대역폭 제한이 없음
- Peering 연결 수 **VPC**당 125개
- Transit Gateway 대비 약 1.5배 저렴
- 서로 연결되어 있지 않으면 통신이 불가능함

### Transit Gateway

![image](https://github.com/pokabook/TIL/assets/103029701/7782431d-0b69-4e5c-8218-4e4c8daa4203)

- 최대 대역폭 50Gbps
- Transit Gateway 당 최대 5000개 **VPC** 연결
- VPC 연결 정책을 중앙에서 관리
- VPN Connection을 통해 On-premise와의 통신을 중앙에서 관리 가능
- Peering 보다 관리적인 측면에서 우수

### PrivateLink

- VPC와 서비스 간에 프라이빗 연결을 제공하는 기술

### 엔드포인트 서비스 (AWS PrivateLink)

- VPC 내에 있는 애플리케이션 또는 서비스
- 다른 AWS 계정의 VPC Endpoint에서 엔드포인트 서비스(AWS PrivateLink)로 연결;//
- 벤더(Service Provider)는 VPC에 애플리케이션을 구성하고 VPC Endpoint 서비스를 구성
- 하나 또는 여러 고객(Consumer) AWS 계정의 VPC Endpoint가 벤더(Service Provider) AWS 계정의 **NLB** 또는 **GWLB**에 연결
- 인터넷을 통하지 않고 AWS 내부 네트워크를 통한 트래픽
- 엔드포인트 서비스 연결시 고객과 벤더의 리전이 같아야 함

### VPC Endpoint

- 인터넷을 통하지 않고 AWS 서비스에 프라이빗하게 연결할 수 있는 VPC의 진입점
    - **Gateway Endpoints**
    - **Interface Endpoints**
    - **Gateway Load Balancer Endpoints**

### VPC Endpoint - Gateway Endpoints

![image](https://github.com/pokabook/TIL/assets/103029701/ad04b004-bf4e-4697-b215-74e3433b3b6e)

- **S3**와 **DynamoDB**에 대한 프라이빗 연결
- 하나의 엔드포인트는 하나의 **VPC**에만 연결 가능
- 엔드포인트는 동알힌 리전에서만 지원
- **VPC** 간에 또는 서비스 간에 엔드포인트를 전송할 수 없음


### VPC Endpoint - Interface Endpoints

![image](https://github.com/pokabook/TIL/assets/103029701/bb44d11b-ffa0-4c4f-b6be-7202632b46c9)

- 서브넷의 IP 주소 범위에서 프라이빗 IP 주소를 사용하는 탄력적 네트워크 인터페이스
- 지원되는 AWS 서비스 또는 VPC 엔드포인트 서비스로 전달되는 트래픽에 대한 진입점 역할
- 엔드포인트는 동일한 리전에서만 지원
- **VPC** 간에 또는 서비스 간에 엔드포인트를 전송할 수 없음

### Gateway Endpoints VS Interface Endpoints for S3

- **Gateway Endpoints**
    - **S3** 퍼블릭 IP 주소를 사용하여 엑세스
    - 온프레미스 엑세스를 허용하지 않음
    - 다른 AWS 리전에서 엑세스를 허용 하지 않음
    - Endpoint 사용 비용 무료

- **Interface Endpoints**
    - **VPC**의 프라이빗 IP 주소를 사용하여 엑세스
    - 온프레미스 엑세스를 허용
    - **VPC** **Peering**, **Transit** **Gateway**를 사용하여 다른 AWS 리전의 VPC에서 엑세스 허용
    - Endpoint 사용 비용 발생

### VPN

![image](https://github.com/pokabook/TIL/assets/103029701/b8b84381-6848-4866-9baa-50ba2f904653)

- 인터넷을 이용하여 가상 사설망(Virtual Private Network)을 구성 하는 것
- VPN 트래픽은 VPN 프로토콜로 보호됨
- IPSec : Site-to-Site VPN 암호화 프로토콜

### VPN - Client VPN

![test](https://github.com/pokabook/TIL/assets/103029701/427d7c3a-4f03-4f69-adfb-17b3a11310a1)

- AWS 리소스와 클라이언트 PC를 연결하는 OpenVPN 기반의 VPN 서비스
- Active Directory 등의 자격증명을 이용해 클라이언트가 VPN에 사용하는 권한을 부여
- 클라이언트는 VPN 접속을 위한 VPN 구성 파일이 담긴 소프트웨어를 설치

### VPN - Site-to-Site VPN (AWS managed VPN)

![image](https://github.com/pokabook/TIL/assets/103029701/066b143a-02f2-4bf3-aab5-07c1762aa56d)

- IPSec 암호화 프로토콜을 사용하여 AWS VPC와 온프레미스간에 프라이빗 네트워크를 구성
- VPC와 연결을 위한 Virtual Private Gateway 및 온프레미스의 Customer Gateway Device의 정보를 구성하기 위한 Customer Gateway를 설정하여 VPN Tunnel 연결을 만듬
- **Direct Connect**의 백업으로 사용 가능
- VPN 터널당 최대 대역폭은 1.25Gbps

### Direct Connect

![image](https://github.com/pokabook/TIL/assets/103029701/2a034316-a58c-4c9b-a41d-60b01d239726)

- AWS와 온프레미스 간에 Direct Connect Location을 통한 전용선을 통해 프라이빗 네트워크 연결 생성
- 포트당 1Gbps, 10Gbps, 100Gbps 연결 속도 사용 가능
- 물리적인 구성을 해야 하기에 설치 시간이 오래 걸림
- VPN보다 가격이 비싸며 인터넷을 통하지 않기에 인터넷 전송 비용이 들지 않음
- 기본적으로 암호화를 지원하지 않음 (암호화를 위해 Direct Connect에 VPN을 구성 가능)
- 트래픽이 인터넷 연결을 사용하는 **Site-to-SIte VPN**보다 안정적