# Kinesis

### Kinesis

---
- 실시간 스트리밍 데이터를 쉽게 수집, 처리 및 분석 하는 서비스
- 비디오, 오디오, 애플리케이션 로그, 웹 사이트 클릭 스트림 및 IoT 텔레메트리 데이터와 같은 실시간 데이터를 수집
- 데이터가 수신되는 대로 처리 및 분석

### 서비스 유형

**Kinesis Data Streams**

- 데이터 스트림을 캡처, 처리 및 저장할 수 있는 스트리밍 데이터 서비스
- 실시간 서비스
- **DynamoDB**, **Aurora**, **CloudWatch** 및 **IoT Core**와 같은 AWS 서비스의 기존 리소스에서 데이터를 보낼 수 있음
- 스트리밍 데이터를 **Lambda**, **Kinesis Data Analytics**, **Kinesis Data firehose** 등으로 전송
- 데이터 스토리지가 있음 (1 ~ 365 일 사이의 기간으로 데이터를 보관)

![Kinesis-Data-Streams](https://github.com/pokabook/TIL/assets/103029701/4f16d62b-daa7-4c8e-a01c-82d59183b4aa)

**Kinesis Data Firehose**

- 스트리밍 **ETL**(extract, transform, and load) 솔루션
- 스트리밍 데이터를 AWS 데이터 스토어와 분석 도구에 로드
- 스트리밍 데이터를 캡처하고 변환한 후 **S3**, **Redshift**, **OpenSearch Service**, **Datadog**로 로드하여 비즈니스 인텔리전스 도구 및 대시보드를 통해 거의 실시간으로 분석
- 거의 실시간 서비스
- 데이터 스토리지가 없음 (데이터를 저장하지 않음)

![Kinesis-Data-Firehose](https://github.com/pokabook/TIL/assets/103029701/fd90d8a4-a357-4ec8-a04a-df8e4a007b8e)

**Kinesis Data Analytics**

- `SQL` 또는 `Apache Flink`를 사용하여 실시간으로 스트리밍 데이터를 변환하고 분석
- `Apache Flink`는 데이터 스트림을 처리를 위한 오픈 소스 프레임워크 및 엔진
- **Kinesis Data Streams** 및 **Kiensis Data Firehose** 스트리밍 소스로부터의 데이터 수집 가능

![Kinesis-Data-Analytics](https://github.com/pokabook/TIL/assets/103029701/4a0e7fe8-1438-4bce-8777-91ed2d82acc3)

**Kinesis Video Streams**

- 디바이스에서 라이브 비디오를 스트리밍하거나 실시간 비디오 처리, 배치 지향 비디오 분석 또는 기계 학습 등을 위한 애플리케이션을 구축하는데 사용할 수 있음
- 수백만 개의 소스에서 방대한 양의 라이브 비디오 데이터를 캡처할 수 있음
- 오디오 데이터, 열 화상 이미지, 깊이 데이터, RADAR 데이터 등과 같은 비 비디오 시간 직렬화 데이터를 보낼 수 있음

![Kinesis-Video-Streams](https://github.com/pokabook/TIL/assets/103029701/e30f9a50-936f-4f40-b401-f9b867fdd3b9)
