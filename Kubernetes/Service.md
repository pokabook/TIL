# Service

### Service
- Pod들을 통해 실행되고 있는 애플리케이션을 네트워크에 노출시키는 가상의 컴포넌트
- Pod 집합과 같은 어플리케이션에 접근 경로나 Service Discovery를 제공
- Pod를 외부 네트워크에 연결하고 Pod로의 연결을 로드밸런싱하는 네트워크 오브젝트
- ``서비스이름.네임스페이스.svc.cluster.local`` 이라는 FQDN이 생성

### Pod 지정 방법

- Service에 연결되는 Pod는 Label Selector를 통해 정의

![image](https://github.com/pokabook/TIL/assets/103029701/28e7ac3b-1813-4696-9045-32bd1b9a4d85)

- Pod YAML
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
        name: nginx
        labels:
            app.kubernetes.io/name: proxy
    spec:
        containers:
        - name: nginx
            image: nginx:stable
            ports:
            - containerPort: 80
                name: http-web-svc
    ```
- Service YAML
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
        name: nginx-service
    spec:
        selector:
            app.kubernetes.io/name: proxy
        ports:
        - name: name-of-service-port
            protocol: TCP
            port: 80
            targetPort: 80
    ```

### Type - ClusterIP

<image src="https://github.com/pokabook/TIL/assets/103029701/e1f5fcca-3aac-4ed3-a608-643601e292f7" width=300, height=300>

- Kubernetes 클러스터 내부에서만 통신이 가능한 Internal Network IP가 할당
- Service <-> Pod 간 통신은 kube-proxy가 담당
- 보통 서비스 디버깅이나 테스트시 사용

### Type - ClusterIP YAML 구조

```yaml
apiVersion: v1
kind: Service
metadata:
	name: back-end
spec:
	type: ClusterIP
	ports:
	- targetPort: 80
		port: 80
	selector:
		app: myapp
		type: back-end
```

### Type - Loadbalancer

<image src="https://github.com/pokabook/TIL/assets/103029701/4a3310dd-54f3-49df-8d40-a2ca2f40bca6" width=300, height=300>

- 클라우드 공급자의 로드밸런서를 이용해 Service를 외부로 노출
- 외부 로드밸런서를 사용하기 때문에 SPOF에 강함
- L4 or L7 레이어를 통해 Service 노출

### Type - Loadbalancer YAML 구조

```yaml
apiVersion: v1
kind: Service
metadata:
	name: mytest-service
spec:
	type: LoadBalancer
	ports:
	- targetPort: 80
		port: 80
		NodePort: 30008
	selector:
		app: myapp
		type: proxy
```

### Type - NodePort

<image src="https://github.com/pokabook/TIL/assets/103029701/4cd8a514-3d84-4190-b560-70d6b7fc54ee" width=300, height=300>

- NAT를 이용해 클러스터를 내 Node의 고정된 Port를 갖는 IP로 Service를 노출
- 외부 트래픽을 서비스에 전달하는 가장 기본적인 방법
- 클러스터외부에서 접근은 ``NodeIP:NodePort``
- Port의 사용 범위 ``30000 ~ 32767``

### Type - NodePort YAML 구조

```yaml
apiVersion: v1
kind: Service
metadata:
	name: back-end
spec:
	type: NodePort
	port:
	- targetPort: 80
		port: 80
		NodePort: 30008
	selector:
		app: myapp
		type: front-end
```