# Serverless 모델

### BaaS (Backend as a Service)

- 어플리케이션 개발 시 요구되는 복잡한 Backend 기능들을 개발자가 직접 개발하지 않고 **CSP**가 제공하는 서비스를 이용
- **Firebase**, **Auth0**와 같은 서비스들이 해당함

![img](https://github.com/pokabook/TIL/blob/main/Serverless/image/BaaS.png?raw=true)

### FaaS (Function as a Service)

- 사용자가 사용하는 기능을 함수 단위로 나누어 구현하고 이를 서비스하는 형태
- Event Driven 구조로 많이 작성되며 `ms` 단위와 함수가 돌아가는 환경의 성능 단위로 과금
- **AWS** **Lambda**, **Google Cloud Functions**, **Microsoft Azure Functions**와 같은 서비스들이 해당

![img](https://github.com/pokabook/TIL/blob/main/Serverless/image/FaaS.png?raw=true)
