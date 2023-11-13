# Kubernetes

### Kubernetes 

- 컨테이너화된 워크로드와 서비스를 관리하기 위한 오픈소스
- 구글에서 개발
- https://kubernetes.io/

### 사용하는 이유

- 완전 오픈소스, 가장 풍부한 에코시스템
- everything as code를 구현 가능
- 어디서나 구동 가능 (on-premise, private/public cloud, local 등등)
- 넘쳐나는 쿠버네티스 레퍼런스

### Kubernetes 오브젝트

![image](https://github.com/pokabook/TIL/assets/103029701/5d5ece5a-7155-4292-bacb-62431efa3823)


- kubernetes 시스템 내에서 영속성을 가지는 오브젝트
- 클러스터의 의도한 상태를 나타내기 위해 오브젝트를 이용
- status 필드는 kubernetes 시스템과 컴포넌트에 의한 오브젝트의 현재 상태를 나타냄
- **Kubernetes Control Plane**은 이 status를 사용자가 의도한 상태와 일치시키기 위해 끊임없이 관리

### 의도한 상태란

- 오브젝트에 대한 기본적인 정보와 의도한 상태를 기술한 오브젝트 spec을 제시
- 오브젝트 생성을 위한 **kubernetes API** 요청은 **`JSON`** 형식 정보를 포함
- 대부분의 경우 정보를 **`YAML`** 파일로 **kubectl**에 제공
- **kubcetl**은 API 요청이 이루어질 때 **`JSON`** 형식으로 정보를 변환

### YAML 기본 구조

```yaml
apiVersion: apps/v1
kind: Deployment
metadata: 
	name: nginx-deployment
spec:
	selector:
		matchLabels:
			app: nginx
	replicas: 2
	teample:
		metadata:
			labels:
				app: nginx
		spec:
			containers:
			- name: nginx
				image: nginx:1.14.2
				ports:
				- containerPort: 80
```

- **apiVersion** : string
    - api의 버전
- **kind** : string
    - 만들고자하는 오브젝트의 종류
- **metadata** : dictionary
    - 오브젝트의 부여할 이름 등
- **spec** : dictionary
    - 만들고자 하는 오브젝트의 어떤 의도한 상태를 기술
- **status** : dictionary
    - 오브젝트의 실제 상태를 기술
    - **Kubernetes Control Plane**은 오브젝트의 실제 상태를 의도한 상태에 일치시키기 방향으로 동작