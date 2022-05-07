## helm部署MeterSphere

### helm 在线部署

```sh
kubectl create ns ms
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add metersphere https://metersphere.github.io/helm-chart/
helm repo update  # 从 chart 仓库中更新本地可用chart的信息
helm install metersphere metersphere/metersphere -n ms
```
### helm 离线部署

导入镜像

下载 MeterSphere 最新版本的离线安装包并且解压，将安装包里 `image` 目录下的镜像tar包上传到kubernetes的镜像库里或者
手动load到kubernetes各个宿主机节点上。

!!! tip ""
    MeterSphere 离线安装包下载链接: https://community.fit2cloud.com/#/products/metersphere/downloads

下载离线chart包

!!! tip ""
    helm-chart 安装包下载链接: https://github.com/metersphere/helm-chart/releases

如：https://github.com/metersphere/helm-chart/releases/download/metersphere-1.1.0/metersphere-1.1.0.tgz

安装
```sh
helm install metersphere metersphere-1.0.10.tgz -n ms
```
### helm 在线升级

```sh
helm repo update  # 从 chart 仓库中更新本地可用chart的信息
helm upgrade  metersphere metersphere/metersphere -n ms
```

### helm 离线升级

导入新版本镜像

下载 MeterSphere 最新版本的离线安装包并且解压，将安装包里 `image` 目录下的镜像tar包上传到kubernetes的镜像库里或者手动load到kubernetes各个宿主机节点上。

!!! tip ""
    MeterSphere 离线安装包下载链接: https://community.fit2cloud.com/#/products/metersphere/downloads

下载最新离线chart包

!!! tip ""
    helm-chart 安装包下载链接: https://github.com/metersphere/helm-chart/releases

如：https://github.com/metersphere/helm-chart/releases/download/metersphere-1.1.0/metersphere-1.1.0.tgz

升级
```sh
helm upgrade metersphere metersphere-1.0.10.tgz -n ms
```
### values.yaml
```sh
ingress:    # 不使用 ingress 可以关闭
  enabled: true        
  host: ms-dev.apps.metersphere.com
  annotations: {}
    ## example for ingress annotions.
    # kubernetes.io/ingress.class: nginx
    # kubernetes.io/tls-acme: "true"      
  https:
    enabled: false
    secretName: ""

common:
  imagePrefix: "registry.cn-qingdao.aliyuncs.com/metersphere/"
  imagePullSecrets: nil
  storageClass: default
  imageTag: v1.20.0-lts
  imagePullPolicy: Always
  mysql:        # 数据库相关配置
    host: metersphere-mysql
    port: 3306
    username: root
    password: Password123@mysql
  redis:        # Redis相关配置
    host: metersphere-redis
    port: 6379
    password: Password123@redis
    database: 1
  kafka:        # Kafka相关配置
    host: metersphere-kafka 
    port: 9092
    metricTopic: JMETER_METRICS
    logTopic: JMETER_LOGS
    testTopic: LOAD_TESTS
    reportTopic: JMETER_REPORTS

server:
  enabled: true
  image: metersphere
  replicas: 1
  properties: |-
    ## DATABASE
    spring.datasource.url=jdbc:mysql://{{.Values.common.mysql.host}}:{{.Values.common.mysql.port}}/metersphere?autoReconnect=false&useUnicode=true&characterEncoding=UTF-8&characterSetResults=UTF-8&zeroDateTimeBehavior=convertToNull&useSSL=false
    spring.datasource.username={{.Values.common.mysql.username}}
    spring.datasource.password={{.Values.common.mysql.password}}
    
    ## redis
    spring.session.store-type=redis
    spring.redis.host={{.Values.common.redis.host}}
    spring.redis.port={{.Values.common.redis.port}}
    spring.redis.database={{.Values.common.redis.database}}
    spring.redis.password={{.Values.common.redis.password}}

    ## KAFKA
    kafka.partitions=1
    kafka.replicas=1
    kafka.topic={{.Values.common.kafka.metricTopic}}
    kafka.bootstrap-servers={{.Values.common.kafka.host}}.{{.Release.Namespace}}:{{.Values.common.kafka.port}}
    kafka.log.topic={{.Values.common.kafka.logTopic}}
    kafka.test.topic={{.Values.common.kafka.testTopic}}
    kafka.report.topic={{.Values.common.kafka.reportTopic}}
    tcp.mock.port=10000

    ## JMETER
    jmeter.image={{ .Values.common.imagePrefix }}{{.Values.jmeter.image}}:{{.Values.jmeter.imageTag}}
    jmeter.pod.threads.limit=500

    ## K8S
    k8s.node-controller-image={{ .Values.common.imagePrefix }}{{.Values.nodeController.image}}:{{.Values.common.imageTag}}

    logger.sql.level=info
    
dataStreaming:
  enabled: true
  image: ms-data-streaming
  replicas: 1
  properties: |-
    ## DATABASE
    spring.datasource.url=jdbc:mysql://{{.Values.common.mysql.host}}:{{.Values.common.mysql.port}}/metersphere?autoReconnect=false&useUnicode=true&characterEncoding=UTF-8&characterSetResults=UTF-8&zeroDateTimeBehavior=convertToNull&useSSL=false
    spring.datasource.username={{.Values.common.mysql.username}}
    spring.datasource.password={{.Values.common.mysql.password}}

    ## KAFKA
    kafka.partitions=1
    kafka.replicas=1
    kafka.topic={{.Values.common.kafka.metricTopic}}
    kafka.bootstrap-servers={{.Values.common.kafka.host}}:{{.Values.common.kafka.port}}
    kafka.log.topic={{.Values.common.kafka.logTopic}}
    kafka.test.topic={{.Values.common.kafka.testTopic}}
    kafka.report.topic={{.Values.common.kafka.reportTopic}}
    jmeter.report.granularity=5000

nodeController:
  enabled: true
  image: ms-node-controller
  replicas: 1
  properties: |-
    ## TBD

jmeter:
  image: jmeter-master
  imageTag: 5.4.3-ms5-jdk11

logPersistence:
  enabled: false
  accessModes: ReadWriteOnce
  size: 10Gi

dataPersistence:
  enabled: true
  accessModes: ReadWriteOnce
  size: 10Gi

mysql:      
  enabled: true     # 引用外部数据库时，可以修改为false,启动时不再安装mysql
  image: mysql
  imageTag: "5.7.25"
  password: Password123@mysql
  persistence:
    enabled: true
    accessModes: ReadWriteOnce
    size: 20Gi
redis:
  enabled: true     # 引用外部redis时，可以修改为false,启动时不再安装redis
  image: redis
  imageTag: "6.2.6"
  password: Password123@redis
  persistence:
    enabled: true
    accessModes: ReadWriteOnce
    size: 10Gi
kafka:
  enabled: true     # 引用外部kafka时，可以修改为false,启动时不再安装kafka
  image:
    registry: registry.cn-qingdao.aliyuncs.com/metersphere
    repository: kafka
    tag: 2.8.1
  fullnameOverride: metersphere-kafka
  persistence:
    enabled: false
  logPersistence:
    enabled: false
  logFlushIntervalMessages: _10000
  logFlushIntervalMs: 1000
  logRetentionBytes: _1073741824
  logRetentionCheckIntervalMs: 300000
  logRetentionHours: 168
  logSegmentBytes: _1073741824
  maxMessageBytes: _1000012
  livenessProbe:
    initialDelaySeconds: 20
    periodSeconds: 15
    timeoutSeconds: 15
  readinessProbe:
    initialDelaySeconds: 20
    periodSeconds: 15
    timeoutSeconds: 15
  externalAccess:
    enabled: true
    service:
      type: NodePort
      useHostIPs: true
    autoDiscovery:
      enabled: true
  serviceAccount:
    create: true
  rbac:
    create: true
  zookeeper:
    enabled: true
    logLevel: ERROR
    persistence:
      enabled: false
    fullnameOverride: metersphere-zookeeper
    image:
      registry: registry.cn-qingdao.aliyuncs.com/metersphere
      repository: zookeeper
      tag: 3.7.0
  extraEnvVars:
    - name: FORMAT_MESSAGES_PATTERN_DISABLE_LOOKUPS
      value: "true"
zookeeper:      # 引用外部kafka时，可以修改为false,启动时不再安装zookeeper
  enabled: true
```

### 引用外部Kafka
```sh
vim values.yaml
将 values.yaml 中 zookeeper.enabled 和 kafka.enabled 改为 false
common.kafka.host、common.kafka.port 改为外部 kafka 的地址和端口
```

### 引用外部 MySql
```sh
vim values.yaml
将 values.yaml 中 mysql.enabled 改为 false
common.host.host、common.host.port、common.host.username、common.host.password 改为外部 mysql 的地址、端口及用户名、密码
```

### 引用外部 Redis
```sh
vim values.yaml
将 values.yaml 中 redis.enabled 改为 false
common.redis.host、common.redis.port、common.redis.password 改为外部 redis 的地址、端口和密码
```

### 创建一个nodeport的访问方式
如果不使用 ingress 的访问方式，可以创建一个nodeport
```sh
vi ms-server-nodeport.yaml

apiVersion: v1
kind: Service
metadata:
  name: metersphere-server-nodeport
  namespace: ms
spec:
  ports:
    - name: metersphere-server
      protocol: TCP
      port: 8081
      targetPort: 8081
      nodePort: 30801
  type: NodePort
  selector:
    app: metersphere-server

kubectl create -f ms-server-nodeport.yaml 
```

访问mstersphere页面
http://nodeIP:30801