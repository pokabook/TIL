# Elasticache

### Elasticache

- 완전관리형 In-Memory Cache 서비스
- **Elasticache for Redis**
- **Elasticache for Memcached**
- 고가용성 캐시 서비스 구성
- 관리 부담 감소 사용 편의성
- 빠른 응답이 필요한 애플리케이션에 사용
- 기존의 DB와 연결하여 DB 응답 성능을 개선하기 위해 사용
- **ElasticCache**를 사용하기 위해서는 애플리케이션의 코드 변경이 필요
- 세션 스토어, 게임 리더보드, 스트리밍 및 분석과 같이 내구성이 필요하지 않는 기본 데이터 스토어로 사용
- **Memcached**는 멀티스레드 지원
- **Redis**는 싱글스레드만 지원

### Vs RDS Read Replica

- **RDS** **Read Replica**
    - 영구적인 데이터 저장
    - 데이터가 계속 변경되는 쿼리의 읽기 성능 향상에 적합
- **ElasticCache**
    - RAM과 같이 빠른 하드웨어에 일시적으로 저장
    - 지연시간을 줄이는 목적으로 주로 사용
    - 속도는 빠르지만 저장할 수 있는 공간에 제약이 있음
    - 변경이 없는 동일한 데이터를 계속 읽는 경우의 성능 향상에 적합

### Elasticache for Redis의 3가지 클러스터 형태

![elasticre](https://github.com/pokabook/TIL/assets/103029701/0844f489-e1aa-43f5-a77d-b87ca9da8e05)

- **싱글 클러스터**
  - `Replication` ❌
  - `Data Partitioning` ⭕️
  - `Scaling` Up / Down
  - `Multi-AZ` ❌
- **클러스터 모드 비활성**
  - `Replication` ⭕️ (최대 5개)
  - `Data Partitioning` ❌
  - `Scaling` Up / Down
  - `Multi-AZ` 최소 1개 Replica 필요
- **클러스터 모드**
  - `Replication` ⭕️
  - `Data Partitioning` ⭕️
  - `Scaling` In / Out
  - `Multi-AZ` ⭕️
