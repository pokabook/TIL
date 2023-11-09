# Organization

### Organization

- 여러 AWS 계정을 조직에 통합하고 중앙에서 관리할 수 있는 계정 관리 서비스
- 계정 및 리소스 접근제어 관리와 통합 결제 기능을 활용
    - 통합 결제를 통한 기업의 예산 관리, 보안 및 규정 준수 요구 사항을 충족

### Multi-Account

![Multi-Account](https://github.com/pokabook/TIL/assets/103029701/31dc30b5-bbdf-4bb1-8bc3-8419f78332a7)

> **SCP (Service Control Policy)**
>
- OU 또는 AWS account를 대상으로 적용이 가능
- 하위 OU에 상속됨
- OU들에 다르게 적용 가능

> **OU (Organization Unit)**
>
- AWS Account들의 그룹 단위
- 하위 OU를 가질 수 있음
- 하나의 AWS 계정은 오직 하나의 OU에만 속할 수 있음

> **Management Account**
>
- OU를 생성한 계정
- 다른 AWS Account를 초대하거나 OU에서 포함시키거나 제거 가능
- 오직 하나의 마스터 / 루트 계정만이 존재
- SCP의 영향을 받지 않음

> **Account**
>
- OU에 초대 받은 AWS 계정
