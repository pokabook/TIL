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

![image 14.png](https://file.notion.so/f/s/a49fff26-025f-441c-b165-e5a447d96716/image_14.png?id=223a5850-067d-4d27-863d-20cb96edefe1&table=block&spaceId=ca1f5917-2d21-4982-9954-5f23844805f2&expirationTimestamp=1685580316017&signature=6K8AyIwbzivDJmIctBKUNmA-CiZ0HnAoWpLP4JZCIe8&downloadName=image+14.png)

**Kinesis Data Firehose**

- 스트리밍 **ETL**(extract, transform, and load) 솔루션
- 스트리밍 데이터를 AWS 데이터 스토어와 분석 도구에 로드
- 스트리밍 데이터를 캡처하고 변환한 후 **S3**, **Redshift**, **OpenSearch Service**, **Datadog**로 로드하여 비즈니스 인텔리전스 도구 및 대시보드를 통해 거의 실시간으로 분석
- 거의 실시간 서비스
- 데이터 스토리지가 없음 (데이터를 저장하지 않음)

![Untitled](https://file.notion.so/f/s/2a91aea4-f058-4ba0-aef8-1188168aa893/Untitled.png?id=12892817-8f7e-4736-aeb9-8d08307f15c9&table=block&spaceId=ca1f5917-2d21-4982-9954-5f23844805f2&expirationTimestamp=1685580367333&signature=8kR9BUW2bKJ0bnRKwBnoiEfEFPkcs9-IoKJR6dMyivM&downloadName=Untitled.png)


**Kinesis Data Analytics**

- `SQL` 또는 `Apache Flink`를 사용하여 실시간으로 스트리밍 데이터를 변환하고 분석
- `Apache Flink`는 데이터 스트림을 처리를 위한 오픈 소스 프레임워크 및 엔진
- **Kinesis Data Streams** 및 **Kiensis Data Firehose** 스트리밍 소스로부터의 데이터 수집 가능

![Untitled](https://file.notion.so/f/s/44d7cd88-5cb1-42cf-8d96-ce252629f06c/Untitled.png?id=fbf445f1-ab43-4884-a045-72d7a5d9fc17&table=block&spaceId=ca1f5917-2d21-4982-9954-5f23844805f2&expirationTimestamp=1685580381952&signature=rVG2zvelf3RpwjqOe9I5pkj3Y3fYy0CfvDBPBDIQ2o0&downloadName=Untitled.png)

**Kinesis Video Streams**

- 디바이스에서 라이브 비디오를 스트리밍하거나 실시간 비디오 처리, 배치 지향 비디오 분석 또는 기계 학습 등을 위한 애플리케이션을 구축하는데 사용할 수 있음
- 수백만 개의 소스에서 방대한 양의 라이브 비디오 데이터를 캡처할 수 있음
- 오디오 데이터, 열 화상 이미지, 깊이 데이터, RADAR 데이터 등과 같은 비 비디오 시간 직렬화 데이터를 보낼 수 있음

![Untitled](https://file.notion.so/f/s/ff7210ae-d456-4b51-a08c-7582cedd2c8f/Untitled.png?id=b76b62f0-12a7-4741-8d33-4ec84d453d9e&table=block&spaceId=ca1f5917-2d21-4982-9954-5f23844805f2&expirationTimestamp=1685580395525&signature=LuF8sF-nzt5vb1e5L8j_LGnOT9yNe7ELMWEo452miTg&downloadName=Untitled.png)