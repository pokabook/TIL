# Athena

### Athena

---
- 표준 SQL을 사용해 **S3**에 저장된 데이터를 분석할 수 있는 쿼리 서비스
- **Athena**로 데이터를 로드 할 필요 없이 **S3**에 저장된 데이터를 직접 사용
- CSV, JSON, ORC, Avro, Parquet와 같은 다양한 종류의 데이터 형식을 지원
    - **S3**에 CSV 데이터 파일을 저장하여 **Athena**를 사용해 SQL 쿼리를 하는 비용 효율적인 솔루션 구축
- Athena 연합 쿼리를 사용하여 CloudWatch Logs, DynamoDB, DocumentDB, RDS, JDBC 호환 관계형 데이터 베이스와 같은 데이터 원본에 저장된 데이터에 대해 SQL 쿼리 수행 가능
- QuickSight와 통합하여 쿼리된 데이터를 시각화 할 수 있음