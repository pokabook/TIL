# Env

### Env

- 개별 컨테이너에 설정해야하는 내용을 환경 변수로 전달
- Pod 정의 파일에 환경 변수를 지정하거나 설정 파일을 마운트하여 전달
    - 예) Timezone, DB 접속 정보 등

### YAML 구조

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: nginx-env
spec:
  containers:
    - name : nginx-env
      image: nginx
      ports:
        - containerPort: 8080
      env:
        - name: APP_COLOR
          value: pink
```