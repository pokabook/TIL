# WAF (Web Application Firewall)

### WAF (Web Application Firewall)

![WAF](https://github.com/pokabook/TIL/assets/103029701/cfba18bc-f81d-48a7-8181-874420e9a065)

- HTTP / HTTPS 트래픽을 모니터링하고 차단함으로써 고객의 웹 어플리케이션을 보호하는 도구
- 관리형 웹 방화벽 서비스
- OWASP TOP 10 (SQL Injection, XSS 등) 대응
- **Cloudfront** / **ALB** 배포
- AWS 관리 규칙 / 사용자 지정 규칙
- IP / 국가 / 헤더 / 문자열 / 요청 길이 기반 차단
- 실시간 웹 보안 모니터링 (**Cloudwatch**)
- AWS 서비스를 활용한 로그통합 (**Kinesis Data Firehose** 및 **S3**)

### WAF Architecture

![WAF-Architecture](https://github.com/pokabook/TIL/assets/103029701/45a844b5-e9b1-4e06-b73d-9d6b05491eba)