# NACL과 Security Group

### NACL과 Security Group

![nacl&sg.png](https://static.javatpoint.com/tutorial/aws/images/aws-nacl-vs-security-group.png)

**Security Group**
---
- 인스턴스 수준 적용
- In / Out traffic White list
- 하나의 EC2 인스턴스 ENI에 5개까지 보안그룹 연결 가능
- 상태저장(statefull) : 들어오는 곳의 상태를 저장하기 때문에 트래픽을 반환할 때 들어온 곳으로 반환한다
- 모든 규칙 평가 적용
- 연결된 경우에만 적용
- 

 **Network ACL**
---
- 서브넷 수준 적용
- 서브넷 내부와 외부의 트래픽을 제어하는 방화벽
- In / Out traffic White / Black list
- 하나의 NACL은 여러 서브넷과 연결 가능
- 상태 비저장(stateless)
- 번호가 낮은 규칙기준 우선순위 적용
- 서브넷 내의 모든 인스턴스 적용