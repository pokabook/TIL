# Deployment

### Deployment

![image](https://github.com/pokabook/TIL/assets/103029701/c4bb4530-1b6b-4a05-8d6a-0092a70a9f8a)

- 복제된(replicated) 애플리케이션(Pod)을 관리하는 오브젝트
- 롤링 업데이트나 롤백 등을 구현하는 리소스

### YAML 구조

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
  labels:
    app: myapp
    type: front-end
spec:
  template:
    metadata:
      labels:
        app: myapp
        type: front-end
    spec:
      containers:
        - name: nginx-container
          image: nginx:1.22
  replicas: 3
  strategy:
    type: RollingUpdate
  selector:
    matchLabels:
      type: front-end
```

### 배포 전략

- **recreate**
    - 모든 Pod를 삭제하고 다시 생성
    - DownTime 생김
    - 변환이 빠르고 비용이 효율적

- **rollingupdate**
    - DownTime이 없음
    ```yaml
    spec:
        rollingUpdate:
            maxUnavailable: 0% # 업데이트 중에 동시에 정지가 가능한 pod 수
            maxSurge: 25% # 업데이트 중에 동시에 생성할 수 있는 최대의 pod 수
    ```