---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

## 1 Helm Charts 在线部署
!!! ms-abstract ""
    ```sh
    kubectl create ns ms
    helm repo add bitnami https://charts.bitnami.com/bitnami
    helm repo add metersphere https://metersphere.github.io/helm-chart/
    # 从 chart 仓库中更新本地可用chart的信息
    helm repo update  
    helm install metersphere metersphere/metersphere -n ms
    ```

## 2 Helm Charts 离线部署
!!! ms-abstract ""
    
    - **导入镜像**<br>
    下载 MeterSphere 最新版本的离线安装包并且解压，将安装包里 `image` 目录下的镜像 tar 包上传到 kubernetes 的镜像库里或者手动 load 到 kubernetes 各个宿主机节点上。<br>
    MeterSphere 离线安装包下载链接: https://community.fit2cloud.com/#/products/metersphere/downloads<br>
    
    - **下载离线 Chart 包**<br>
    helm-chart 安装包下载链接: https://github.com/metersphere/helm-chart/releases,如：https://github.com/metersphere/helm-chart/releases/download/metersphere-2.3.0/metersphere-2.3.0.tgz
    
    - **进行安装**<br>
    ```sh
    helm install metersphere metersphere-2.3.0.tgz -n ms

    # 根据需要修改 values.yml 文件配置后安装
    helm install metersphere metersphere-2.3.0.tgz -f metersphere/values.yml -n ms
    ```

## 3 Helm Charts 在线升级
!!! ms-abstract ""
    ```sh
    helm repo update  # 从 chart 仓库中更新本地可用chart的信息
    helm upgrade metersphere metersphere/metersphere -n ms
    ```

## 4 Helm Charts 离线升级
!!! ms-abstract ""

    - **导入新版本镜像**<br>
    下载 MeterSphere 最新版本的离线安装包并且解压，将安装包里 `image` 目录下的镜像 tar 包上传到 kubernetes 的镜像库里或者手动 load 到 kubernetes 各个宿主机节点上。 <br>
    MeterSphere 离线安装包下载链接: https://community.fit2cloud.com/#/products/metersphere/downloads
    
    - **下载最新离线 Chart 包**<br>
    helm-chart 安装包下载链接: https://github.com/metersphere/helm-chart/releases  <br>
    如：https://github.com/metersphere/helm-chart/releases/download/metersphere-2.3.0/metersphere-2.3.0.tgz
    
    - **进行升级**<br>
    ```sh
    helm upgrade metersphere metersphere-2.3.0.tgz -n ms

    # 根据需要修改 values.yml 文件配置后升级
    helm upgrade metersphere metersphere-1.0.10.tgz -f metersphere/values.yml -n ms
    ```

## 5 values.yaml
!!! ms-abstract ""
    以下 values.yaml 内容对应版本为 v2.3.0，最新的 values.yaml 可到 github 上 metersphere helm-chart 仓库中查找对应版本的 values.yaml，例如：v2.9.1 版本 value.yaml 文件为 https://github.com/metersphere/helm-chart/blob/metersphere-2.9.1/charts/metersphere/values.yaml

```sh
ingress: # 不使用 ingress 可以关闭
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
  imageTag: v2.3.0     # 安装的版本号
  imagePullPolicy: Always  # 镜像拉取策略
  properties: |-
    ## DATABASE
    spring.datasource.url=jdbc:mysql://{{.Values.mysql.host}}:{{.Values.mysql.port}}/metersphere?autoReconnect=false&useUnicode=true&characterEncoding=UTF-8&characterSetResults=UTF-8&zeroDateTimeBehavior=convertToNull&useSSL=false&allowPublicKeyRetrieval=true
    spring.datasource.username={{.Values.mysql.username}}
    spring.datasource.password={{.Values.mysql.password}}
    ## redis
    spring.session.store-type=redis
    spring.redis.host={{.Values.redis.host}}
    spring.redis.port={{.Values.redis.port}}
    spring.redis.database={{.Values.redis.database}}
    spring.redis.password={{.Values.redis.password}}
    ## KAFKA
    kafka.partitions=1
    kafka.replicas=1
    kafka.topic={{.Values.kafka.metricTopic}}
    kafka.bootstrap-servers={{.Values.kafka.host}}.{{.Release.Namespace}}:{{.Values.kafka.port}}
    kafka.log.topic={{.Values.kafka.logTopic}}
    kafka.test.topic={{.Values.kafka.testTopic}}
    kafka.report.topic={{.Values.kafka.reportTopic}}
    tcp.mock.port=10000
    ## minio
    minio.endpoint=http://{{.Values.minio.host}}:{{.Values.minio.port}}
    minio.access-key={{.Values.minio.username}}
    minio.secret-key={{.Values.minio.password}}
    ## JMETER
    jmeter.image={{ .Values.common.imagePrefix }}{{.Values.jmeter.image}}:{{.Values.jmeter.imageTag}}
    jmeter.pod.threads.limit=500
    ## K8S
    k8s.node-controller-image={{ .Values.common.imagePrefix }}{{.Values.nodeController.image}}:{{.Values.common.imageTag}}
    ## spring cloud
    eureka.client.service-url.defaultZone=http://{{.Values.eureka.host}}:{{.Values.eureka.port}}/eureka/
    logger.sql.level=info
apiTest:  # 接口测试模块,可以修改为false,启动时不再安装接口测试模块
  enabled: true
  image: api-test
  replicas: 1

performanceTest: # 性能测试模块,可以修改为false,启动时不再安装性能测试模块
  enabled: true
  image: performance-test
  replicas: 1

systemSetting: # 系统设置模块,可以修改为false,启动时不再安装系统设置模块
  enabled: true
  image: system-setting
  replicas: 1

projectManagement: # 项目管理模块,可以修改为false,启动时不再安装项目管理模块
  enabled: true
  image: project-management
  replicas: 1

reportStat:  # 报告管理模块,可以修改为false,启动时不再安装报告管理模块
  enabled: true
  image: report-stat
  replicas: 1

testTrack: # 测试跟踪模块,可以修改为false,启动时不再安装测试跟踪模块
  enabled: true
  image: test-track
  replicas: 1

gateway: # 网关,可以修改为false,启动时不再安装
  enabled: true
  image: gateway
  replicas: 1

eureka: # 服务注册中心,可以修改为false,启动时不再安装
  enabled: true
  image: eureka
  host: metersphere-eureka
  port: 8761
  replicas: 1

dataStreaming: 
  enabled: true
  image: data-streaming
  replicas: 1
  properties: |-
    ## DATABASE
    spring.datasource.url=jdbc:mysql://{{.Values.mysql.host}}:{{.Values.mysql.port}}/metersphere?autoReconnect=false&useUnicode=true&characterEncoding=UTF-8&characterSetResults=UTF-8&zeroDateTimeBehavior=convertToNull&useSSL=false&allowPublicKeyRetrieval=true
    spring.datasource.username={{.Values.mysql.username}}
    spring.datasource.password={{.Values.mysql.password}}
    ## KAFKA
    kafka.partitions=1
    kafka.replicas=1
    kafka.topic={{.Values.kafka.metricTopic}}
    kafka.bootstrap-servers={{.Values.kafka.host}}:{{.Values.kafka.port}}
    kafka.log.topic={{.Values.kafka.logTopic}}
    kafka.test.topic={{.Values.kafka.testTopic}}
    kafka.report.topic={{.Values.kafka.reportTopic}}
    jmeter.report.granularity=5000
    ## minio
    minio.endpoint=http://{{.Values.minio.host}}:{{.Values.minio.port}}
    minio.access-key={{.Values.minio.username}}
    minio.secret-key={{.Values.minio.password}}
nodeController:
  enabled: true
  image: node-controller
  replicas: 1
  properties: |-
    ## TBD
jmeter:
  image: jmeter-master
  imageTag: 5.4.3-ms5-jdk11

logPersistence:
  enabled: true
  accessModes: ReadWriteOnce
  size: 10Gi

dataPersistence:
  enabled: true
  accessModes: ReadWriteOnce
  size: 10Gi

mysql:  # 引用外部数据库时，可以修改为false,启动时不再安装mysql
  enabled: true
  image: mysql
  imageTag: "8.0.30"
  host: metersphere-mysql
  port: 3306
  username: root
  password: Password123@mysql
  persistence:
    enabled: true
    accessModes: ReadWriteOnce
    size: 20Gi
minio:
  enabled: true
  image: minio
  imageTag: "latest"
  username: admin
  password: Password123@minio
  host: metersphere-minio
  port: 9000
  persistence:
    enabled: true
    accessModes: ReadWriteOnce
    size: 20Gi
redis:   # 引用外部redis时，可以修改为false,启动时不再安装redis
  enabled: true
  image: redis
  imageTag: "6.2.6"
  password: Password123@redis
  host: metersphere-redis
  port: 6379
  database: 1
  persistence:
    enabled: true
    accessModes: ReadWriteOnce
    size: 10Gi
kafka:   # 引用外部kafka时，可以修改为false,启动时不再安装kafka
  enabled: true
  fullnameOverride: metersphere-kafka
  host: metersphere-kafka
  port: 9092
  metricTopic: JMETER_METRICS
  logTopic: JMETER_LOGS
  testTopic: LOAD_TESTS
  reportTopic: JMETER_REPORTS
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
  extraEnvVars:
    - name: FORMAT_MESSAGES_PATTERN_DISABLE_LOOKUPS
      value: "true"
zookeeper:
  enabled: true
```

### 5.1 引用外部 Kafka
!!! ms-abstract ""
    ```sh
    vim values.yaml
    将 values.yaml 中 zookeeper.enabled 和 kafka.enabled 改为 false
    common.kafka.host、common.kafka.port 改为外部 kafka 的地址和端口
    ```

### 5.2 引用外部 MySQL
!!! ms-abstract ""
    ```sh
    vim values.yaml
    将 values.yaml 中 mysql.enabled 改为 false
    common.host.host、common.host.port、common.host.username、common.host.password 改为外部 mysql 的地址、端口及用户名、密码
    ```

### 5.3 引用外部 Redis
!!! ms-abstract ""
    ```sh
    vim values.yaml
    将 values.yaml 中 redis.enabled 改为 false
    common.redis.host、common.redis.port、common.redis.password 改为外部 redis 的地址、端口和密码
    ```

### 5.4 使用修改后的 value.yaml 部署 
!!! ms-abstract ""
    ```sh
    helm -n ms install metersphere ./metersphere-2.3.0.tgz -f values.yaml
    ```

### 5.5 创建 Node Port 访问方式
!!! ms-abstract ""
    使用命令 kubectl get svc -n ms 可查看 metersphere-gateway 所占用的端口号。如果不使用 ingress 的访问方式，可以创建一个 nodeport。

    ```sh
    vi ms-gateway-nodeport.yaml
    
    apiVersion: v1
    kind: Service
    metadata:
      name: metersphere-gateway-nodeport
      namespace: ms
    spec:
      ports:
        - name: metersphere-gateway
          protocol: TCP
          port: 8000
          targetPort: 8000
          nodePort: 30801
      type: NodePort
      selector:
        app: metersphere-gateway
    
    kubectl create -f ms-gateway-nodeport.yaml 
    ```

    访问 MeterSphere 页面: http://nodeIP:30801
