# Pod

### Pod

- 최소단위 쿠버네티스 객체
- Docker 컨테이너와 다르게 Pod는 하나 이상의 컨테이너를 포함 가능
- 애플리케이션 컨테이너(하나 또는 다수), 스토리지, 네트워크 등의 정보를 포함

### 디자인 패턴

![image](https://github.com/pokabook/TIL/assets/103029701/9fb38761-3c1c-4e28-a156-96a3497b261a)

- Sidecar
    - 로깅을 하는 전용 컨테이너를 띄울 때 자주 사용
- Adapter
    - 외부 접속을 위한 인터페이스 제공해주기 위해 구성
- Ambassador
    - 메인 컨테이너를 대신하여 외부 시스템과의 통신을 중재해주는 서브 컨테이너가 필요할 때 사용

### YAML 구조

- 포트 할당
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata: 
        name: myapp-prod
        namespace: app
        labels:
            app: myapp
            type: front-end
    spec:
        containers:
        - name: nginx-container
            image: nginx
            ports:
            - continaerports: 8080
    ```
- 멀티 컨테이너
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata: 
        name: myapp-prod
        namespace: app
        labels:
            app: myapp
            type: front-end
    spec:
        containers:
        - name: nginx-container
            image: nginx
        - name: redis-container
            image: redis:3.2
    ```
- toleration이 있는 경우
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata: 
        name: myapp-prod
        namespace: app
        labels:
            app: myapp
            type: front-end
    spec:
        containers:
        - name: nginx-container
            image: nginx
        tolerations:
        - key: "app"
            operator: "Equal"
            value: "blue"
            effect: "NoSchedule"
    ```
- nodeAffinity가 있는 경우
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata: 
        name: myapp-prod
    spec:
        continers:
        - name: nginx
            image: nginx
        affinity:
            nodeAffinity:
                requiredDuringSchedulingIgnoreDuringExecution:
                    nodeSelectorTerms:
                    - matchExpressions:
                        - key: size
                            operator: In(|NotIn|Exists)
                            value:
                            - Large
                            - Medium
    ```
- Resource Requirement가 있는 경우
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
        name: myapp-pod
    spec:
        containers:
        - name: nginx
            image: nginx
            resources:
                requests:
                    cpu: 1000m
                    memory: "1Gi"
                limits:
                    cpu: 3000m
                    memory: "2Gi"
    ```
    - Resource 정의가 없는 경우 제한없이 CPU / MEM 사용
    - limit을 넘어서는 경우 **k8s**는 cpu throttle을 하고 memory의 경우에는 limit을 넘어 쓸 수 있지만 지속되면 terminate 시켜버림