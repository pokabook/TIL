# Terraform

### Terraform

- HashiCorp사에서 Go언어 기반으로 개발한 HCL 언어로 코드 작성
- 별도의 서버 구성이 필요 없는 클라이언트 기반 아키텍처만 지원
- AWS, Azure, GCP, NCloud, Datadog 등 다양한 Provider 지원
- IaC 도구 중 인프라 프로비저닝 용도로 사용
- 프로비저닝과 인프라 재사용에 용이

### 장점

- 콘솔에 로그인할 서버 운영 및 관리가 모두 자동화 가능
- 사람이 수동으로 작업하는 것보다 빠르게 배포 가능함
- 일관성을 보장
- 유효성 검증을 통해 문제가 발생하는것을 어느 정도 예방 가능

### 단점 

- AWS 설정을 **Terraform**으로 한번에 migration 하기 어려움
- 배포 전략이 제한적
- 러닝 커프 (Learning Curve)
    - HCL 문법
- plan과 apply 명령어의 차이
    - plan에선 성공하지만 현재 state에 따라서 apply는 실패할 수 있음
- 프로젝트 규모가 커질수록 배포시 점점 더 느려짐

### Terraform Life Cycle

- **Init**
  - `terraform init` 
  - 테라폼 구동을 위한 초기화
- **Plan**
  - `terraform plan`
  - 현재 상태 → 원하는 상태로 구성
  - 예상되는 변경점을 미리 확인해보는 단계
- **Apply**
  - `terraform apply`
  - 실행하는 단계
  - 선후관계를 명시하지 않아도 알아서 순차적, 병렬적으로 실행됨
  - 일부 명시해야 하는 경우도 존재
- **Destory**
  - `terraform destory` 
  - 제로의 상태로 돌아오는 과정 (삭제)

### Terraform Flow

![img](https://github.com/pokabook/TIL/blob/main/IaC/image/Terraform-Flow.png?raw=true)

1. Terraform 구성 소스
   - 현재 관리자가 작성 혹은 수정하고 있는 코드
2. Terraform State
   - 가장 최근에 배포한 테라폼 코드 형상
3. 실제 인프라
   - 실제로 Cloud 환경에 배포되어 있는 인프라

### 디렉토리 레이아웃

```
.
├── backend.tf
├── main.tf
├── modules
├── outputs.tf
├── provider.tf
└── variables.tf
```

- main.tf : 프로비저닝할 리소스를 정의
- variables.tf : 소스코드에 사용할 변수들을 정의
- outputs.tf : 소스코드에 대한 실행 결과를 정의 및 출력
- modules : 리소스를 모듈화 한 단위
- backend.tf : 형상 관리를 하기 위한 설정을 정의
- provider.tf : 리소스 제공자와 버전 등을 정의

### 상태 관리

- Terraform은 인프라나 설정에 대해서 무조건 state(상태)로 저장함
- state는 기본적으로 terraform.tfstate 라는 로컬 파일에 저장됨
  - backend가 remote 인 경우에는 환경마다 다름
- state는 terraform 으로 선언된 설정과 실제 인프라 객체를 매핑하기 위해 존재함
- state가 없으면 terraform으로 인프라 관리를 할 수 없음

### state 파일 분리

- 여러 개의 환경을 관리할 때 locking이 발생하여 수정을 못하는 경우가 발생
  - A가 운영환경에 배포하는 동안 locking이 발생하여 B는 개발환경에서 테스트가 불가능함
- 환경별로 상태 파일을 분리가 필요
  - 디렉토리를 분리(환경별로 root module 생성)
  - workspace 분리

    ```
    .
    ├── .dev
    │   └── main.tf
    ├── .prd
    │   └── main.tf
    └── .test
        └── main.tf
    ```

### 문제점

- state 파일이 저장된 위치의 성능에 따라서 terraform 성능에 영향이 발생함
- `plan` / `apply` 실행시 매번 로컬에 저장된 state와 API로 호출된 값을 비교
- `-refresh=fasle` 옵션을 통해서 로컬에 저장된 state만으로 비교 가능
- remote backend 사용시 환경에 따라서 추가 지연 발생 가능
- **S3**를 사용할 시 생기는 문제점
  - 하나의 terraform module을 여러명이서 관리할 때는 state 파일을 공유해야함
  - S3와 같은 파일시스템을 사용할 경우엔 동시에 동일한 state 파일에 접근한다면 충돌이 발생
  - state 파일도 손상되고 인프라 설정도 꼬이게 됨
  - state locking 하기 위해서 **DynamoDB**설정도 추가가 필요함
