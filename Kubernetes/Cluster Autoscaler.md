# Cluster Autoscaler (CA)

### Cluster Autoscaler

- 수요에 따라 Kubernetes Node를 자동으로 추가하는 기능
    - 리소스 부족으로 pod의 Node 할당이 pending 될 때 (scale-out)
    - 미사용 Node가 있을 때 (scale-in)
- 각 cloud provider 마다 각자의 cluster autoscaling 방법이 있음

### Cluster Autoscaler on AWS

![image](https://github.com/pokabook/TIL/assets/103029701/ef547d4d-9636-4b78-8334-164c58be8e53)

- AWS EC2 Autoscaling Group의 기능을 이용하여 Cluster Autoscaler 구현
- Cluster Autoscaler가 Deployment 형태로 기동되어 EC2 Autoscaling Group과 상호작용