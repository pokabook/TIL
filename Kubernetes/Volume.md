# Volume

### Volume

- 스토리지 볼륨을 추상화하여 Pod와 느슨하게 결합시킨 리소스
- 오브젝트의 형태가 아닌 Pod 내에서 정의
- 다양한 플러그인들이 존재
    - hostPath
    - nfs
    - iscsi
    - cephfs
    - emptyDir

### 예시

---

- **emptyDir**

    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
        name: test-pd
    spec:
        containers:
        - image: registry.k8s.io/test-webserver
            name: test-container
            volumeMounts:
            - mountPath: /cache
                name: cache-volume
        volumes:
        - name: cache-volume
            emptyDir:
                sizeLimit: 500Mi
    ```

-  **hostPath**

    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
        name: test-pd
    spec:
        containers:
        - image: registry.k8s.io/test-webserver
            name: test-container
            volumeMounts:
            - mountPath: /test-pd
                name: test-volume
        volumes:
        - name: test-volume
            hostPath:
                path: /data
                type: Directory
    ```

### 한계

- 컨테이너 자신만 접근 가능한 비영구적 볼륨이기 때문에 컨테이너가 재시작할 때 유지 할 수 없음
- **Kubernetes** 클러스터 레벨에서 볼륨을 관리하기 어려움
- **Volume**이 변경될 때 마다 해당 **Volume**을 사용하는 모든 **Pod**의 설정 변경 필요

### Persistent Volume (PV)

- 영속성을 갖고 있는 **Volume** 오브젝트
- 추상화된 가상의 **Volume** 오브젝트로 별도로 정의 및 생성하여 **Pod**와 연결

### Persistent Volume Claim (PVC)

- **PV**를 요청하는 오브젝트
- 용량, label 등을 기반으로 PV에 대한 요청이 들어오면 스케줄러가 현재 가지고 있는 PV에서 적당한 볼륨을 할당


### Storage Class

- 사용할 스토리지의 클래스를 정의
- 각 프로바이더가 제공하는 볼륨의 종류에 따라 고유한 파라미터를 가짐

- **AWS EBS**

    ```yaml
    apiVersion: storage.k8s.io/v1
    kind: StorageClass
    metadata:
        name: slow
    provisioner: kubernetes.io/aws-ebs
    parameters:
        type: io1
        iopsPerGB: "10"
        fsType: ext4
    ```

- **Azure Disk**

    ```yaml
    apiVersion: storage.k8s.io/v1
    kind: StorageClass
    metadata:
        name: slow
    provisioner: kubernetes.io/azure-disk
    parameters:
        skuName: Standard_LRS
        location: eastus
        storageAccount: azure_storage_account_name
    ```

### Dynamic Provisioning

- on-demand로 스토리지 볼륨을 자동 생성할 수 있는 메커니즘
- **StorageClass**를 기반으로 동작하여 관리자가 필요한 **StorageClass**를 정의하여 동적생성 할 때 필요한 파라미터를 **volume provisioner**에 전달
- **StorageClass**에 정의한 **PV**가 없는 경우 동적으로 **PV**를 생성하여 **PVC**에 할당

### Life Cycle

![image](https://github.com/pokabook/TIL/assets/103029701/25540355-4559-4fc7-a3b0-eba86fb42f88)