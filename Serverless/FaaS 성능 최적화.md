# FaaS 성능 최적화

### Cold Start Delay 줄이기

![img](https://github.com/pokabook/TIL/blob/main/Serverless/image/Cold-Start.png?raw=true)

- **Full Cold Start**
    - Zip 파일로 부터 코드를 불러옴
    - 새로운 메모리나 런타임을 구성
- **Partial Cold Start**
    - Java, Golang 같은 런타임을 실행
- **Warm Start**
    - 실제 코드가 실행

### 실행 환경의 메모리 증가시키기

![img](https://github.com/pokabook/TIL/blob/main/Serverless/image/Memory-Up.png?raw=true)

- 메모리가 크면 클수록 컴퓨팅 파워도 그에 비례해서 할당됨
- 임계값을 찾아서 사용하는 것이 중요
- 단 메모리를 올릴경우 **비용이 증가한다**는 것을 알아둬야만 함

### Provisioned Concurrency 활성화

![img](https://github.com/pokabook/TIL/blob/main/Serverless/image/Provisioned-Concurrency.png?raw=true)

- 미리 인스턴스를 초기화 해두고 대기시켜두는 것
- 미리 대기시켜두기 때문에 어떠한 리퀘스트가 없어도 비용이 발생함
