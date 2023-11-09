# KMS (Key Management Service)

### KMS (Key Management Service)

![image](https://github.com/pokabook/TIL/assets/103029701/3501082d-75cf-43f6-9c96-89e822a5e0b4)

- AWS에서 제공하는 암호화 키를 생성 및 관리하는 서비스
- 리소스 데이터 암호화 / 복호화
- 디지털 서명 및 확인
- **EBS**, **S3**, **RDS** 등의 AWS 서비스 데이터 암호화에 **KMS** 사용
- 감시를 위해 **CloudTrail**, **Cloudwatch** 등과 통합되어 모든 키 사용에 관한 로그를 제공
- 키를 자동교체 하는 기능 지원

### 암호화

- 데이터를 도난이나 해킹으로부터 보호하기 위한 방법
- **전송중 암호화** : 네트워크로 전송하는 트래픽을 암호화
- **서버측 암호화** : 서버에 저장된 데이터를 암호화
- **클라이언트측 암호화** : 데이터를 보내기전에 암호화

![KMS-encryption](https://github.com/pokabook/TIL/assets/103029701/611cd74c-5922-4750-9e72-5d854725d176)

### 3가지 키 지원 방식

- **AWS managed key**
    - AWS 에서 default로 제공
    - AWS 서비스가 고객의 계정에서 고객 대신 생성, 관리 및 사용하는 **KMS** 키
    - 키 정책, 삭제 등의 제어 권한이 없거나 제한이 있음
    - 사용자가 직접적으로 제어 불가능
- **Customer managed key**
    - 사용자가 직접 키를 생성, 소유 및 관리하는 AWS 계정의 **KMS** 키
    - **IAM** 을 통해 권한 부여
    - 가장 많이 사용하는 방식
- **AWS owned keys**
    - AWS 서비스가 여러 AWS 계정에서 사용하기 위해 소유하고 관리하는 **KMS** 키 모음

### 다중 리전 키 (Multi-Region Keys)

![Multi-Region-Keys](https://github.com/pokabook/TIL/assets/103029701/e420ec54-362b-4a6b-a06e-88e1ecfc3a0f)

- 여러 리전에서 동일한 키를 가지고 있는 것
- 다중 리전 키의 각 세트에는 동일한 키 구성 요소와 키 ID가 있으므로 **KMS**를 다시 암호화하거나 크로스 리전 호출을 수행하지 않고 하나의 AWS 리전에서 데이터를 암호화 하고 다른 AWS 리전에서 복호화 가능
- 동일한 키를 사용하면 다른 리전의 데이터를 서로 다른 키로 다시 암호화 할 필요가 없음
- **DynamoDB** 글로벌 테이블 및 **DynamoDB** 암호화, 멀티 리전의 복제된 **S3** 버킷의 암호화 등에 사용 가능
