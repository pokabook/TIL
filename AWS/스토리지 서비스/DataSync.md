# DataSync

### DayaSync

![image](https://github.com/pokabook/TIL/assets/103029701/08824d10-4c83-4b99-a1ad-48605f92c898)

- On-premise와 AWS간 또는 AWS 스토리지 서비스 간 데이터 전송 및 복제를 자동화하는 서비스
- SMB나 NFS 프로토콜을 사용하는 On-premise 서버의 파일을 AWS의 S3, EFS, FSx 서비스로 전송
- On-premise 데이터를 Amazon S3, Amazon EFS, AMazon FSx로 마이그레이션하거나 S3 Glacier로 아카이빙을 위해 사용
- AWS 서비스 내의 스토리지 내의 데이터 이동을 위해 사용
- 전송 중 및 전송 종료 시 데이터 무결성 확인 및 암호화 가능
- 전송은 시간별, 일별, 주별 등 예약된 일정에 따라 자동으로 이루어짐

---

### VS Snowball Edge

- 오프라인 데이터 전송
- 전송대역폭이 제한
- 연결이 안정적이지 못한 경우에 사용

##### DataSync

- 온라인으로 데이터를 전송하는데 사용

---

### VS Storage Gateway

- 초기 마이그레이션 이후 Storage Gateway의 파일 게이트웨이 구성을 사용하여 마이그레이션된 데이터 및 On-premise 파일 기반 애플리케이션의 지속적인 액세스를 유지

##### DataSync

- 초기 데이터를 Amazon S3로 마이그레이션

---

### VS S3 Transfer Acceleration

- S3로의 대용량 파일 전송을 위해 더 높은 처리량을 사용할 경우 사용

---

### VS Transfer Family

- SFTP, FTPS 및 FTP 프로토콜을 사용하여 Amazon S3 및 Amazon EFS와 파일 전송을 하려는 경우 사용

##### DataSync

- NFS 서버, SMB 파일 공유, 자체 관리형 객체 스토리지, AWS Snowcone, Amazon S3, Amazon EFS 및 Amazon FSx 간에 데이터 전송을 가속화 및 자동화하려는 경우 사용
