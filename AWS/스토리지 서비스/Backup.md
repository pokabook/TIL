# Backup

### Backup

- 중앙 집중식 백업 관리 서비스
- 백업 일정 관리, 보존관리, 백업 모니터링, 수명주기관리, 액세스 정책, 암호화 등의 기능을 사용할 수 있음
- 교차리전 백업, 교차계정 백업 지원
- 리소스 태그 기반으로 백업 정책 구성 가능
- 백업대상으로는 FSx, EFS, Storage Gateway(Volume Gateway), EBS, DynamoDB, RDS, Aurora, EC2, VMware 가상머신 등이 존재
- 리소스들에 대한 백업 데이터는 S3에 저장됨

![image](https://github.com/pokabook/TIL/assets/103029701/b8e83835-9032-4f33-8082-f2da5278d298)

- 백업 볼트(Backup Vault)
  - 백업을 구성하는데 사용하는 컨테이너
  - 백업 암호화를 위해 KMS 키 설정 가능
- 백업 계획(Backup Plan)
  - 리소스들을 백업할 시기와 방법을 정의
  - 백업 규칙과 백업할 리소스들의 집합
- 백업 규칙(Backup Rule)
  - 백업 빈도, 백업 기간, 수명 주기, 백업 볼트 등을 지정
- 리소스(Resource)
  - 백업할 대상
  - 백업 계획 생성 후 따로 리소스를 할당 해줘야 함
  - 태그 또는 리소스 ID로 할당이 가능
