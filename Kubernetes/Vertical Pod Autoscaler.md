# Vertical Pod Autoscaler (VPA)

### Vertical Pod Autoscaler

![image](https://github.com/pokabook/TIL/assets/103029701/f82b1147-e039-4ced-a65b-3e5825db851e)

- 컨테이너에 할당하는 CPU / 메모리 리소스의 할당을 자동으로 스케일링 해주는 오브젝트
- 서비스 적용 전 Pod resource request에 어떤 값이 적정한지 명확하지 않을 때 유용
- **VPA** > **HPA** > **CA** 순으로 스케일링 동작

### YAML 구조

- **VPA**

    ```yaml
    apiVersion: autoscaling.k8s.io/v1beta2
    kind: VerticalPodAutoscaler
    metadata:
        name: nginx-vpa
        namespace: vpa
    spec:
        targetRef:
            apiVersion: "apps/v1"
            kind: Deployment
            name: nginx
        updatePolicy:
            updateMode: "Auto"
        resourcePolicy:
            containerPolicies:
            - containerName: "nginx"
                minAllowed:
                    cpu: "250m"
                    memory: "100Mi"
                maxAllowed:
                    cpu: "500m"
                    memory: "600Mi"
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
                            cpu: "180m"
                            memory: "1Gi"
                        limits:
                            cpu: "600m"
                            memory: "100Mi"
        replicas: 3
        selector:
            matchLabels:
                type: front-end
    ```