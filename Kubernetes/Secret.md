# Secret

### Secret

- 워크로드에 필요한 민감 정보를 **Key-Value** 형태로 저장할 수 있는 데이터 오브젝트
- **base64** 인코딩 상태로 저장

### YAML 구조

---

- **Secret**
    
    ```yaml
    apiVersion: v1
    kind: Secret
    metadata: test-secret
    data:
    	DB_Host: XXXXX
    	DB_User: XXXXX
    	DB_Password: XXXXX
    ```
- **Secret** 전체를 **injection**
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
    	name: myapp
    spec:
    	containers:
    		- name: myapp
    			image: nginx
    			ports:
    				- containerPort: 8080
    			envFrom:
    				- secretKeyRef:
    						name: test-secret
    ```
- **Secret** 일부를 **injection**
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
    	name: myapp
    spec:
    	containers:
    		- name: myapp
    			image: nginx
    			ports:
    				- containerPort: 8080
    			env:
    				- name: DB_Password
    					valueFrom:
    						secretKeyRef:
    							name: test-secret
    							key: DB_Password
    ```

### 주의점

![image](https://github.com/pokabook/TIL/assets/103029701/667988c4-24a0-4a57-9b4c-5906267f03a9)

- secret과 cm 모두 etcd에 저장되기 때문에 kubernetes master에 엑세스 가능한 사람은 모두 확인할 수 있다