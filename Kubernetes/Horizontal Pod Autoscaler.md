# Horizontal Pod Autoscaler (HPA)

### Horizontal Pod Autoscaler

![image](https://github.com/pokabook/TIL/assets/103029701/c5f64b3b-78e8-4163-866a-acc2025ba8da)

- **Deployment** / **ReplicaSet**의 레플리카 수를 CPU / 메모리 부하 등에 따라 자동으로 스케일 해주는 오브젝트
- **Pod**의 Resource Requests를 기준으로 동작
- metric server에서 가져온 각 **Pod**의 1분 평균값

### Horizontal Pod Autosacler의 기준

- cpu (**resource**)
- memory (**resource**)
- packets-per-second (**pod**)
- requests-per-second (**ingress**)

### Cluster Autoscaler와의 상호작용

- 컨테이너(**Pod**)의 로드가 증가하면 **HPA**는 우선 클러스터에 충분한 공간이 있든 없든 새 **replica**를 생성
- 리소스가 충분하지 않은 경우 **CA**는 **HPA**에서 생성한 **Pod**가 실행될 노드를 새로 기동
- 반대로 로드가 감소하면 HPA는 일부 **replica**를 삭제하고 결과적으로 활용되지 않는 노드가 생기면 **CA**가 이러한 노드를 종료

### YAML 구조

- **HPA**
    
    ```yaml
    apiVersion: autoscaling/v2
    kind: HorizontalPodAutoscaler
    metadata:
    	name: sample-hpa
    spec:
    	scaleTargetRef:
    		apiVersion: apps/v1
    		kind: Deployment
    		name: myapp-deploy
    	minReplicas: 1
    	maxReplicas: 10
    	metrics:
    	- type: Resource
    		resource:
    			name: cpu
    			target:
    				type: Utilization
    				averageUtilization: 50
    ```
- **Deployment**
    
    ```yaml
    apiVersion: apps/v1
    kind: Deployment
    ...
    spec:
    	template:
    		metadata:
    			name: myapp-deploy
    		spec:
    			containers:
    			- name: nginx
    				image: nginx
    				resources:
    					requests:
    						cpu: 1
    						memory: "1Gi"
    					limits:
    						cpu: 3
    						memory: "2Gi"
    	replicas: 3
    	selector:
    		matchLabels:
    			type: front-end
    ```