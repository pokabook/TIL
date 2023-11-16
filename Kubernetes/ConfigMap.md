# ConfigMap (CM)

### ConfigMap

- 워크로드에 필요한 설정 정보를 **Key-Value** 형태로 저장할 수 있는 데이터 오브젝트
- 간단한 환경변수부터 nginx.conf와 같은 설정 파일도 저장 가능

### YAML 구조

- **ConfigMap**
    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
    	name: test-config
    data:
    	APP_COLOR: blue
    	APP_MODE: prod
    ```
- **ConfigMap** 전체를 **injection**
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
    				- configMapRef:
    						name: test-config
    ```
    
- **ConfigMap** 일부를 **injection**
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
    				- name: APP_COLOR
    					valueFrom:
    						configMapKeyRef:
    							name: test-config
    							key: APP_COLOR
    ```
- 파일을 담은 **ConfigMap**
    ```yaml
    apiVersion: v1
    data:
      nginx.conf: |
        user       www www;  ## Default: nobody
        worker_processes  5;  ## Default: 1
        error_log  logs/error.log;
        pid        logs/nginx.pid;
        worker_rlimit_nofile 8192;
    
    		...
    kind: ConfigMap
    metadata:
      annotations:
        kubectl.kubernetes.io/last-applied-configuration: |
          {"kind":"ConfigMap","apiVersion":"v1","metadata":{"name":"test3-config","creationTimestamp":null},"data":{"nginx.conf":"user       www www;  ## Default: nobody\nworker_processes  5;  ## Default: 1\nerror_log  logs/error.log;\npid        logs/nginx.pid;\nworker_rlimit_nofile 8192;\n\nevents {\n  worker_connections  4096;  ## Default: 1024\n}\n\nhttp {\n  include    conf/mime.types;\n  include    /etc/nginx/proxy.conf;\n  include    /etc/nginx/fastcgi.conf;\n  index    index.html index.htm index.php;\n\n  default_type application/octet-stream;\n  log_format   main '$remote_addr - $remote_user [$time_local]  $status '\n    '\"$request\" $body_bytes_sent \"$http_referer\" '\n    '\"$http_user_agent\" \"$http_x_forwarded_for\"';\n  access_log   logs/access.log  main;\n  sendfile     on;\n  tcp_nopush   on;\n  server_names_hash_bucket_size 128; # this seems to be required for some vhosts\n\n  server { # php/fastcgi\n    listen       80;\n    server_name  domain1.com www.domain1.com;\n    access_log   logs/domain1.access.log  main;\n    root         html;\n\n    location ~ \\.php$ {\n      fastcgi_pass   127.0.0.1:1025;\n    }\n  }\n\n  server { # simple reverse-proxy\n    listen       80;\n    server_name  domain2.com www.domain2.com;\n    access_log   logs/domain2.access.log  main;\n\n    # serve static files\n    location ~ ^/(images|javascript|js|css|flash|media|static)/  {\n      root    /var/www/virtual/big.server.com/htdocs;\n      expires 30d;\n    }\n\n    # pass requests for dynamic content to rails/turbogears/zope, et al\n    location / {\n      proxy_pass      http://127.0.0.1:8080;\n    }\n  }\n\n  upstream big_server_com {\n    server 127.0.0.3:8000 weight=5;\n    server 127.0.0.3:8001 weight=5;\n    server 192.168.0.1:8000;\n    server 192.168.0.1:8001;\n  }\n\n  server { # simple load balancing\n    listen          80;\n    server_name     big.server.com;\n    access_log      logs/big.server.access.log main;\n\n    location / {\n      proxy_pass      http://big_server_com;\n    }\n  }\n}\n"}}
      creationTimestamp: "2023-07-02T03:03:44Z"
      name: test3-config
      namespace: default
      resourceVersion: "834953"
      uid: a61ae148-0cac-4aa0-b2f8-dd6e13f50977
    ```
    
    - **ConfigMap** 전체를 **injection**
        ```yaml
        apiVersion: v1
        kind: Pod
        metadata:
        	name: myapp
        spec:
        	containers:
        		- name: myapp
        			image: nginx
        			volumeMounts:
        			- name: config-volume
        				mountPath: /config
        		volumes:
        		- name: config-volume
        			configMap:
        				name: test3-config
        ```
        
    
    - **ConfigMap** 일부를 **injection**
        ```yaml
        apiVersion: v1
        kind: Pod
        metadata:
        	name: myapp
        spec:
        	containers:
        		- name: myapp
        			image: nginx
        			volumeMounts:
        			- name: config-volume
        				mountPath: /config
        		volumes:
        		- name: config-volume
        			configMap:
        				name: test3-config
        				items:
        				- key: nginx.conf
        					path: nginx-sample.conf
        ```
