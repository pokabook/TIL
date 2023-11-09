# FaaS 성능 최적화

### Cold Start Delay 줄이기

![img](https://github.com/pokabook/TIL/assets/103029701/0d1389a6-f2de-4902-9d64-096108f37024)

- **Full Cold Start**
    - Zip 파일로 부터 코드를 불러옴
    - 새로운 메모리나 런타임을 구성
- **Partial Cold Start**
    - Java, Golang 같은 런타임을 실행
- **Warm Start**
    - 실제 코드가 실행

### 실행 환경의 메모리 증가시키기

![img](https://github.com/pokabook/TIL/assets/103029701/eebb225f-9827-4dee-b903-ac563899dec2)

- 메모리가 크면 클수록 컴퓨팅 파워도 그에 비례해서 할당됨
- 임계값을 찾아서 사용하는 것이 중요
- 단 메모리를 올릴경우 **비용이 증가한다**는 것을 알아둬야만 함

### Provisioned Concurrency 활성화

![img](https://github.com/pokabook/TIL/assets/103029701/f956e57d-6ee2-4906-9418-29d043fe6b55)

- 미리 인스턴스를 초기화 해두고 대기시켜두는 것
- 미리 대기시켜두기 때문에 어떠한 리퀘스트가 없어도 비용이 발생함