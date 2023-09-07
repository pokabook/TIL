# EBS (Elastic Block Storage Service)

### EBS

![image](https://github.com/pokabook/TIL/assets/103029701/4fa90c37-8cc5-4b3a-bee4-a46c633069e5)

- 블록 스토리지 서비스
- EC2에 Attach 및 Detach하여 사용가능
- SSD/HDD 볼륨
- 간편한 스냅샷 백업
- 99.999% 내구성
- 탄력적 확장 가능
- 축소 불가능
- EC2 인스턴스 시작 시 AMI가 설치되는 EBS 루트(부트) 볼륨이 생성됨
- 여러 개의 EBS 볼륨을 생성하여 EC2에 추가 연결 가능
- EBS와 EC2는 동일한 가용영역에 있어야 연결 가능
- 스냅샷 기능을 통해 EBS 볼륨 백업 가능
- 수명 주기 관리자(Data Life Cycle Manager) 정책을 통해 스냅샷 생성 일정을 자동화 가능
- KMS를 이용하여 EBS 볼륨 암호화 가능

### EBS 볼륨 타입

![image](https://github.com/pokabook/TIL/assets/103029701/c85ef32d-a1c2-47c0-93e3-9043b5ab969f)

- 볼륨 유형에 따라 제공되는 용량(크기), IOPS, 최대 처리량이 다름
- 부트 볼륨은 범용 SSD, 프로비저닝된 SSD만 지원
- EBS 다중 연결은 프로비저닝된 SSD만 지원

### EBS 다중연결(EBS Multi-Attach)

- 하나의 EBS 볼륨을 여러 EC2에 동시에 연결하는 기능
- 동일한 가용영역 내에서만 연결 가능
- 모든 EC2 유형이 연결 가능하지 않고 Nitro 기반의 Linux 인스턴스만 연결 가능
- 모든 EBS 볼륨 유형이 연결 가능하지 않고 프로비저닝 된 IOPS SSD만 지원
- 동시에 최대 16대의 EC2 인스턴스 연결 가능
- 여러 EC2 인스턴스에서 하나의 EBS 볼륨에 동시 쓰기 작업이 필요한 클러스터링 된 Linux 애플리케이션에서 사용

### EBS 스냅샷(Snapshots)

- EBS 볼륨의 데이터를 백업하는 기능
- 백업된 스냅샷을 다른 가용영역 또는 리전에 복사 가능
- 스냅샷을 커스텀 AMI 이미지로 만들 수 있음
- 백업된 스냅샷을 가지고 새로운 EC2 인스턴스를 생성 가능
- **EBS Snapshot Archive**
  - 자주 액세스하지 않는 스냅샷을 저렴한 아카이브 스토리지 계층에 보관
  - 90일 이상 저장할 계획이며 액세스할 필요가 거의 없는 스냅샷에 최대 75% 비용이 저렴 (최소 과금 기간 90일)
- **Recycle Bin for EBS Snapshot**
  - 실수로 삭제한 스냅샷을 휴지통에 보관해서 복구 가능
  - 삭제된 파일은 1일부터 365일까지 보관 설정 가능
- **EBS Fast Snapshot Restore-FSR**
  - 지연시간을 최소화하여 빠르게 스냅샷으로부터 EBS 볼륨을 복원하는 기능
 
### 암호화되지 않은 EBS 볼륨 암호화

1. EBS 볼륨 스냅샷을 생성
2. EBS 볼륨 스냅샷을 복사한 후 스냅샷을 암호화 후 암호화된 스냅샷으로부터 새 EBS 보륨 생성 또는 암호화 되지 않은 스냅샷에 새 EBS 볼륨을 생성할 때 암호화 선택
3. 새 EBS 볼륨을 EC2 인스턴스에 연결
