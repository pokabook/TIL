# Node (Worker Node)

### Node 

- 워크로드가 돌아가는 컨테이너를 배치하는 물리(가상) 머신
- control plane에 의해 관리
- 일반적인 운영환경에서는 multi node로 운영
- 각 노드는 kubelet / container-runtime / kube-proxy가 포함

### Node의 상태

![image](https://github.com/pokabook/TIL/assets/103029701/97c3170c-6513-45ca-a394-6b85ce588f97)

- Node의 condition 필드에서 확인 가능