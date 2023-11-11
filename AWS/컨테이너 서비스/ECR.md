# ECR (Elastic Container Registry)

### ECR

- Docker 등의 컨테이너 이미지를 공유, 배포 등의 관리 서비스
- ECR에 공유된 이미지를 사용하여 ECS, EKS에서 컨테이너를 구성
- ECR에 이미지를 등록하면 S3에 저장됨

### 구성 요소

- **Registry**
    - 각 AWS 계정마다 제공되어 하나 이상의 Repository를 생성하고 이미지를 저장할 수 있는 공간
- **Repository**
    - Docker image, Open Container Initiative(OCI) image ALC OCI 호환 아티팩트를 저장
- 사용자 권한 토큰
    - 클라이언트가 ECR 레지스트리에 AWS 사용자로서 인증을 하고 이미지를 푸시 및 가져올 수 있는 토큰
- **Repository 정책**
    - 레포 및 레포 내 이미지에 대한 엑세스를 제어

### 기능

- **수명 주기 정책 (Lifecycle Policy)**
    - 리포지토리에 있는 이미지의 수명 주기를 관리 (시간, 개수 기준)
- **이미지 스캔**
    - 컨테이너 이미지의 소프트웨어 취약성을 식별
- **교차 리전 및 교차 계정 복제**
- **풀스루 캐시 규칙**
    - 프라이빗 Amazon ECR 레지스트리에 원격 퍼블릭 레지스트리의 리포지토리를 캐시하는 방법을 제공