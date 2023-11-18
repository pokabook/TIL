# Kube-scheduler

### Kube-scheduler

![image](https://github.com/pokabook/TIL/assets/103029701/6150cf7b-6125-42fb-acd6-a7c9c22a9252)

- 클러스터 안에서 자원 할당이 가능한 노드 중 알맞은 노드를 선택하는 역할
- 점수를 부여하여 선택하는 방식
- Label / Selector / Affinity / Taint / Toleration 기능과 함께 동작

### Pod 스케줄링의 필요성 (예시들)

- 머신러닝 워크로드를 돌리는 특정 pod는 GPU가 탑재된 node에서만 돌아야 한다
- consumer들은 네트워크 intensive 하므로 전용 node group을 쓰고싶다
- 팀별로 node를 나눠서 사용하고 싶다

### Pod 스케줄링 분류 - 사용자가 특정 노드에 Pod를 배치하고 싶을 경우

- NodeSelector
    - 노드에는 `Label`을 할당하고, 파드에는 `NodeSelector` 필드를 추가하여 특정 노드에서 
    구동되도록 함
    - `NodeSelector`는 여러 값을 할당하거나 not 예외처리를 하거나 하는등을 하기는 어려움
- Node Affinity
    - 여러 advanced 할당을 할 수 있는 만큼 문법이 다소 복잡
-  Node Anti-Affinity, Inter Pod Affinity, Inter Pod Anti-Affinity 등 다양하게 존재

### Pod 스케줄링 분류 - 관리자가 특정 노드에는 pod가 배치되는 것을 막고 싶은 경우

- 어떤 pod가 어떤 node에 스케줄링 될 수 있는지를 제한
- 쿠버네티스의 **control node**에는 pod가 스케줄링되지 않도록 `taint`가 되어있음
- Taint
    - Node가 가지게 되는 성격 (ex. taint: blue)
- Tolerations
    - Pod가 가지게 되는 taint에 대한 toleration (ex. toleration: blue)