# EFS (Elastic File System)

### EFS

![image](https://github.com/pokabook/TIL/assets/103029701/d84ea89b-793b-40a7-961d-62836dfec89a)


- 리눅스 환경의 EC2 인스턴스에서 연결하기 위한 네트워크 파일 스토리지
- 여러 가용영역에 있는 수십~수백대의 EC2 연결 가능
- 파일 스토리지 서비스
- NFS(Network File System) 버전 4 지원
- 공유 스토리지 (동시 액세스 가능)
- Storage 자동 스케일 업
- Peta Byte까지 데이터 저장 가능
- 다양한 AWS 서비스 마운트 지원
- Provisioned Throughput 모드 지원
- Bustring 기능을 지원하여 잦은 읽고 쓰기를 할 시 성능저하
- 보안그룹을 통해 인스턴스에 연결
- Linux 방식의 On-premise 서버에서도 연결 가능
- KMS를 이용하여 암호화 가능

### 스토리지 클래스

- EFS 수명주기 관리 정책 또는 EFS 지능형 계층화(Intelligent-Tiering)을 사용하여 자주 사용하지 않는 데이터를 다른 스토리지 클래스로 자동 전화 가능
- 표준 스토리지(Standard): 3개의 가용영역에 데이터 저장, 자주 액세스하는 파일을 저장하는 데 사용
- 표준 IA(Standard Infrequent Access): 3개의 가용영역에 데이터 저장, 자주 액세스하지 않는 파일을 저장하는 데 사용
- One Zone: 1개의 가용영역에 데이터 저장, 자주 액세스하는 파일을 저장하는 데 사용
- One Zone IA(One Zone Infrequent Access): 1개의 가용영역에 데이터 저장, 자주 액세스하지 않는 파일을 저장하는 데 사용

### 성능 모드

- 기본 범용 성능 모드
  - 일반적인 I/O 성능
- 최대 I/O 성능 모드
  - 높은 성능의 처리가 필요한 빅데이터 분석 애플리케이션 등에 사용
 
### 처리량 모드

- 파일 시스템의 처리량 (MiB/s)
- 기본 버스트 처리량 모드
  - 파일 용량이 커짐에 따라 자동으로 처리량을 확장
- 프로비저닝된 모드
  - 저장된 데이터의 양과 상관없이 고정으로 처리량을 지정
