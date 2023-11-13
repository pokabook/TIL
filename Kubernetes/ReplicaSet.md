# ReplicaSet

### ReplicaSet

- Pod의 레플리카를 생성하고 지정한 Pod 수를 유지하는 리소스
- 기존 ReplicaSet Controller에서 ReplicaSet으로 변경
- 가용성을 위한 오브젝트

### YAML 구조

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myapp-replicaset
  labels:
    app: myapp
    type: front-end
spec:
  template:
    metadata:
      name: myapp-prod
      labels:
        app: myapp
        type: front-end
    spec:
      containers:
        - name: nginx-container
          image: nginx
  replicas: 3
  selector:
    matchLabels:
      type: front-end
```
- 어떤 Pod가 해당 ReplicaSet에 할당되는지를 나타냄
    ```yaml
    selector:
        matchLabels:
            type: front-end
    ```
- Pod의 metadata 이하를 그대로 가져옴
    ```yaml
    metadata:
			name: myapp-prod
			labels:
				app: myapp
				type: front-end
		spec:
			containers:
			- name: nginx-container
				image: nginx
    ```