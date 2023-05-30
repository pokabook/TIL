# Well-Architected Framework

### Well-Architected Framework

---

- AWS가 지금까지의 경험을 바탕으로 만들어둔 5가지 설계 원칙

![well-architected-framework.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F50cbf501-7f6a-45cb-abbf-5cf288d079ee%2FUntitled.png?table=block&id=90b2b630-a5d1-4810-ac36-ee3ea8942ea2&spaceId=ca1f5917-2d21-4982-9954-5f23844805f2&width=2000&userId=467b3a39-e763-4668-abf0-2feb9074a9e6&cache=v2)

### 운영 우수성

---

- 운영하기 수월하도록 설계를 해야한다
- 운영 작업을 코드로 수행 (IaC)
- 변경작업을 최소 단위로 나누어 수행
- 롤백을 고려한 변경작업 수행
- 운영 프로세스를 자주 개선
- 장애를 시나리오 만들기
- 모든 장애 리뷰 및 레슨런 하기

### 보안

---

- 시스템의 모든 접근에 대한 추적 및 기록 (Cloudtrail, Guard Duty)
- 보안을 위한 자동화 구현 설계
- 모든 데이터를 보호하도록 설계 (전송 중인 데이터, 정적 데이터)
- 보안 이벤트를 준비 (침입탐지, ddos 등)
- 모든 계층 (OSI 7 Layer) 에 대해 보안을 적용
![security.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8d264176-6ce0-4d96-a68c-5aa905e2906a%2FUntitled.png?table=block&id=2b05e0ea-e0af-4532-bb99-d2409d693453&spaceId=ca1f5917-2d21-4982-9954-5f23844805f2&width=2000&userId=467b3a39-e763-4668-abf0-2feb9074a9e6&cache=v2)

### 안전성

---

- 장애에 대한 자동 복구 구축
- 장애 복구 훈련 수행
- 가용성을 높이기 위한 수평 확장 설계
- 스펙을 추측하지 않고 확장 가능하도록 설계
- 운영 자동화의 지속적 변경 관리

### 성능효율성

---

- 최신 기술을 습득하고 적용
- 주기적인 프로토타입 진행
- 빠른 글로벌 접근 가능한 설계 (cloudfront, route53)
- 서버리스 아키텍처 활용 (Lambda, Fargate, S3)

### 비용최적화

---

- 알맞는 가격 약정 채택
- 리소스 Right Sizing 분석
- 클라우드 마이그레이션을 통해 온프레미스 운영비용 최소화
- 관리형 서비스를 사용하여 운영비용 최소화
- 지속적인 월 비용 분석을 통한 비용 최적화 수행