# Metric Server

### Metric Server

- Kubernetes 클러스터 리소스 샤용량 데이터를 집계하는 역할
- Kubelets에서 리소스 메트릭을 수집하고 이를 Metrics API를 통해 **apiserver**에 노출하여 Horizontal Pod Autoscaler 및 Vertical Pod Autoscaler에서 사용
- 클러스터 내에 Deployment 형태로 설치