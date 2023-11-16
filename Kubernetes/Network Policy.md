# Network Policy

### Network Policy

![image](https://github.com/pokabook/TIL/assets/103029701/aa6514ba-f0ab-468a-8000-22a6deb7430d)

- **Pod** 내부로 들어오거나 외부로 나가는 트래픽을 허용하고 거부하는 정책을 설정할 수 있는 오브젝트
- 기본적으로 Whitelist 형식
- **CNI**를 사용하는 것이 전제

### YAML 구조

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata: db-policy
spec:
	podSelector:
		matchLabels:
			role: db
	policyTypes:
	- Ingress
	- Egress
	ingress:
	- from:
		- podSelector:
				matchLabels:
					name: api-pod
			namespaceSelector:
				matchLabels:
					name: prod
		- ipBlock:
				cidr: 192.168.5.10/32
		ports:
		- protocol: TCP
			port: 3306
	egress:
	- to:
		- ipBlock:
				cidr: 10.0.0.9/32
		ports:
		- protocol: TCP
			port: 80
```