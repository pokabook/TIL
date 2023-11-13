# DaemonSet

### DaemonSet

- 클러스터의 각 노드에 Pod를 하나씩 띄울 때 사용하는 오브젝트
- 로그수집기를 실행하거나 노드를 모니터링하는 모니터링용 데몬 등 클러스터 전체에 항사 실행시켜 두어야 하는 Pod를 실행하는데 사용
- 예시) kube-proxy, fluent-bit 등등

### YAML 구조

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
	name: monitroing-daemon
spec:
	template:
		metadata:
			labels:
				app: monitroing-agent
		spec:
			containers:
			- name: monitoring-agent
				image: nginx
	selector:
		matchLabels:
			app: monitroing-agent
```