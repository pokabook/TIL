# Ingress

### Ingress
- Service Type은 아니지만 Service 앞에서 smart router 및 entry point 역할을 하는 오브젝트
- 외부에서 접근 가능한 URL, Load Balancing, SSL, Termination 등을 통해 Service에 대한 HTTP 기반 접근
- 클러스터에 하나 이상의 실행 중인 Ingress Controller가 필요(aws-lb-controller, nginx ingress)

### Ingress Controller란
- Kubernetes나 다른 컨테이너 환경에서 reverse proxy 혹은 loadbalancer 역할을 하는 리소스
- Service Ingress 리소스가 동작하려면 클러스터에 Ingress Controller가 있어야함
- kube-controller-manager 바이너리의 일부로 실행되는 다른 유형의 컨트롤러와 달리 Ingress Controller는 클러스터와 함께 자동으로 시작되지 않음

### 사용하는 이유

![image](https://github.com/pokabook/TIL/assets/103029701/bde5159f-ec03-4a7e-a6e2-ce489daafec3)

- 대외 webapp을 만들었다고 가정하면 NodePort를 이용하여 서비스를 노출하면 사용자가 30000 이상의 포트 넘버를 기억하고 접근해야함
- 일반적으로는 proxy를 두고 30 → 3xxxx로 포워딩을 하는 layer를 생성

### Ingress On AWS

![image](https://github.com/pokabook/TIL/assets/103029701/8960bacc-e140-48bb-9c2e-1ccec5a511ee)

- IP → ClusterIP
- Instance → NodePort
- default는 instance 모드

### YAML 구조

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
	namespace: app
	name: ingress-myapp
	annotations:
		alb.ingress.kubernetes.io/scheme: internet-facing
		alb.ingress.kubernetes.io/target-type: ip
spec:
	ingressClassName: alb
	rules:
	- http:
			paths:
			- path: /
				pathType: Prefix
				backend:
					service:
						name: service-2048
						port:
							number: 80
```