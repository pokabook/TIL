# FSx

### FSx for Lustre

![image](https://github.com/pokabook/TIL/assets/103029701/d4d6b0cc-8bc8-4070-8f57-cd2d4ee75015)

- 리눅스 환경을 위한 고성능 병렬 스토리지 시스템
- 분산파일 시스템(DFS, Distributed File System)
- 머신 러닝, 빅데이터 등의 고성능 컴퓨팅에 사용(HPC, High Performance Computing)
- Amazon S3 버킷과 통합 구성하여 같이 사용 가능
- On-premise 서버에서 엑세스 가능

##### 파일 시스템 배포 옵션

- 스크래치 파일 시스템(Scratch File System)
  - 임시 스토리지 및 단기 데이터 처리를 위한 시스템
  - 데이터는 복제되지 않으며 파일 서버에 장애 발생시에도 교체 되지 않음
- 지속적 파일 시스템(Persistent File System)
  - 장기 스토리지 및 워크로드를 위한 시스템
  - 데이터가 여러 가용영역에 자동으로 복제되어 가용성이 높음
  - 파일 서버 장애 발생시 자동으로 교체됨
 
### FSx for Windows File Server

![image](https://github.com/pokabook/TIL/assets/103029701/11019ab6-6382-4055-84be-0caeb0c5cf7a)

- 윈도우 서버에 구축되는 파일 공유 서비스
- SMB 프로토콜을 이용하기에 윈도우, 리눅스 OS에서 액세스 가능
- 사용자 액세스 제어를 위해 AD(Active Directory) 서비스와 통합 가능
- On-premise 서버에서 액세스 가능
