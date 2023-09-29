# JMeter

### JMeter

---

- Apache 재단에서 오픈소스로 만든 JAVA 기반의 성능 테스트 툴
- 생성된 `.jmx` 파일을 이용하여 CLI로 실행도 가능
- HTTP, HTTPS, FTP, JDBC, LDAP 등 다양한 프로토콜을 지원
- `HTML`, `JSON`, `XML` 등 다양한 리포트 형식을 지원
- 다양한 플러그인을 지원하고 유지/보수 등이 활발

![image](https://github.com/pokabook/TIL/assets/103029701/2a40a66f-f9c4-45d7-95ab-ae8d35461cf8)

### 구조

---

- **Thread Group**
  - 몇 개의 스레드가 동시에 요청을 보낼지 설정 하는 곳
- **Sampler**
  - 어떤 유저가 해야하는 액션
- **Listner**
  - 응답을 받았을 때 취하는 동작
- **Configuration**
  - Sampler 또는 Listener가 사용할 설정 값
- **Assertion**
  - 응답 결과의 성공 여부를 판단하는 조건
- **Logic Controller**
  - 특정한 작업을 반복하거나 분기 역할
- **Timer**
  - 쓰레드가 만들어 내는 요청들 사이에 특정 시간만큼 딜레이를 주는 역할
