# Storage Gateway

### Storage Gateway

- On-premise 데이터 센터의 데이터와 AWS 클라우드의 스토리지를 연결하는 서비스
- 하이브리드 클라우드 스토리지라고도 부름 (On-premise 인프라 + Cloud 인프라)
- On-premise의 데이터를 AWS 클라우드로 실시간으로 전송 및 저장 가능
- On-premise에 로컬캐시 기능을 통해 자주 사용하는 데이터 보관 가능
- 파일 백업, 클라우드 파일저장소, 재해복구 저장소의 용도로 사용
- On-premise 저장 공간과 관련 비용 절감 효과
- 4가지 유형이 존재

### S3 FileGateway
![image](https://github.com/pokabook/TIL/assets/103029701/16fb79e8-42e7-4996-8e6f-f99aa91a7a8d)

- On-premise와 S3간에 파일 단위로 전송하는 게이트웨이
- NFS, SMB 프로토콜을 이용하여 S3에서 객체를 저장하고 검색 가능
- Active Directory(AD) 통합하여 인증된 사용자만 액세스 하도록 구성 가능

### FSx FileGateway
![image](https://github.com/pokabook/TIL/assets/103029701/e5c34c5a-6610-4188-8459-f136752c87ac)

- On-premise와 Amazon FSx for Windows File Server 간에 파일 단위로 전송하는 게이트웨이
- SMB 프로토콜을 이용하여 FSx for Windows File Server 내의 파일을 저장하고 검색 가능
- Active Directory(AD) 서비스와 통합하여 인증된 사용자만 엑세스 하도록 구성 가능

### Volume Gateway
![image](https://github.com/pokabook/TIL/assets/103029701/6557cb94-cfb9-4676-b7d3-12518c9419f0)

- iSCSI 연결을 사용하여 On-premise 애플리케이션에 블록 스토리지를 제공
- On-premise의 서버에서 블록 스토리지 볼륨을 iSCSI 디바이스로 연결 가능
- 볼륨 데이터는 S3에 저장되며 볼륨을 EBS 스냅샷으로 저장 및 AWS Backup 서비스로 백업 가능
- 두 가지 볼륨 모드
  - 캐싱 볼륨: 기본데이터는 S3에 저장하고 자주 액세스하는 일부 데이터만 로컬 캐싱에 저장, 캐시를 통해 액세스 시간 감소
  - 저장 볼륨: 모든 데이터를 로컬에 저장 후 AWS에 비동기식 백업, 로컬에 백업 세트가 저장된 효과

### Tape Gateway
![image](https://github.com/pokabook/TIL/assets/103029701/9467423d-3d5e-4215-ad37-55333bfadaab)

- On-premise의 테이프 백업 애플리케이션과 S3 간의 전송을 위한 게이트웨이
- 기존의 On-premise 테이프 백업 장치 구성을 변경하지 않아도 AWS S3로 백업 가능
- S3 Glacier(S3 Glacier Flexible Retrieval) 또는 S3 Glacier Deep Archive 로 백업을 하여 저장 비용 최소화 가능
