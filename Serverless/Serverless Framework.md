# Serverless Framework

### Serverless Framework

- **Serverless** 서비스와 연결되는 서비스를 구성하고 각 환경에 맞게 작성한 코드를 쉽게 배포하고 관리하기 위한 프레임워크
- js, python, go, ruby, C# 등 다양한 언어와 다양한 **CSP** 지원
- 다양한 Plugin 지원과 YAML 파일 하나로 통합 관리 및 배포 가능


### Service

- 여러 functions 이나 resource를 하나로 묶어 둔 개념

### Provider

- 구성하는 환경에 대한 설정
- 어떤 환경인지, 어떤 언어와 runtime을 사용하는지, 어떤 **IAM Role**을 사용하는지 등을 적어서 사용

### Plugin

- **Serverless** 기능을 확장할 때 많이 사용되는 기능
- **Datadog**과 연동을 하는 경우 Serverless Plugin Datadog 라는 plugin 사용

### Package

- 배포시에 어떤 것들이 포함될지 결정하는 요소

### Functions

- **Lambda**가 동작할 때, 실제로 동작하는 binary나 method를 지정

### Resource

- Lambda가 동작할 때 trigger가 되거나 함께 사용하는 AWS 서비스들
