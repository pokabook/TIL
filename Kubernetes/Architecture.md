# Architecture

### Architecture

![image](https://github.com/pokabook/TIL/assets/103029701/7946d597-cba4-496c-a9b8-0bd883df0e60)

- **Control Plane (Master Node)**
    - Kubernetes 전체를 통제한다.
    - kube-apiserver
    - etcd
    - kube-schuler
    - kube-controller-manager (cloud-controller-manager)
- **Data Plane (Worker Node)**
    - 실제 사용자의 애플리케이션을 배포한다.
    - kubelet
    - kube-proxy
    - container-runtime