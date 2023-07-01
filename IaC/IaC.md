# IaC (Infrastructure as Code)

### 코드형 인프라 (Infrastructure as Code)

- 수동 프로세스가 아닌 코드를 통해 인프라를 관리하고 프로비저닝 하는 것
- 어플리케이션 코드와 인프라 구성을 위한 코드 사이의 경계가 허물어짐

### 장점

- 매번 동일한 환경을 프로비저닝하도록 보장 (일관성)
    - 개발 / 테스트 / 운영으로 동일한 구조의 VPC를 3개 운영
    - 조직 / 팀별로 다수 계정 사용
    - 조직 내 가이드(거버넌스, 보안)를 위한 템플릿 형태로 사용 가능
- Git 과 같은 버전 관리 시스템 사용 가능
    - 버전 관리
    - 협업 가능
- 오류 감소(Human Error)

### 단점

- 프레임워크에 따라서 일부코드로 관리가 되지 않는 영역 존재
- Best Practice 에 대한 자료가 부족
    - 다중 계정 운영 방식, 망분리(ISMS), 협업 등등
- 권한 제어의 어려움
    - DevOps vs Backend 개발자의 차이 (Elastic Beanstalk)
    - 다중 계정 간의 VPC Peering, 공통 리소스 공유 (EC2 이미지)
- 코드화의 어려움
    - AWS 공식 문서(콘솔, AWSCLI) → 코드화

### 종류

- AWS
  - CloudFormation / SAM
  - CDK
- Open Source
  - Terraform
  - CDKTF
  - Ansible- agent ❌
  - Chef - agent ⭕️
  - Puppet - agent ⭕️
  - Serverless Framework
