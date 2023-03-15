## 1 环境要求

!!! info "部署服务器要求"
    * 操作系统: CentOS 7.x / Redhat 7.x
    * CPU/内存: 最低要求 4C8G，推荐 8C16G
    * 磁盘空间: 50G

## 2 下载安装包

请自行下载 MeterSphere 最新版本的离线安装包，并复制到目标机器的 /tmp 目录下。

!!! tip ""
    安装包下载链接: https://community.fit2cloud.com/#/products/metersphere/downloads

## 3 解压安装包

以 root 用户 ssh 登录到目标机器, 并执行如下命令。

```sh
cd /tmp
# 解压安装包
tar zxvf metersphere-offline-installer-v1.20.15-lts.tar.gz
```

## 4 修改安装配置(可选)
### 4.1 解压

在安装包解压后的目录，编辑修改安装参数。

```sh
cd metersphere-offline-installer-v1.20.15-lts
vim install.conf
```
### 4.2 安装配置文件说明

!!! info "安装配置文件说明, 如果无特殊需求可以不进行修改采用默认参数安装（首次安装可修改配置 install.conf 文件中相关配置，修改完后执行 /bin/bash install.sh 命令进行安装，已安装成功如需再修改配置参数，可以直接到 ${MS_BASE}/metersphere/.env 里修改，修改完后执行 msctl reload 即可重新加载配置文件）"
    ```vim
    # 基础配置
    ## 安装路径, MeterSphere 配置及数据文件默认将安装在 ${MS_BASE}/metersphere 目录下
    MS_BASE=/opt
    ## MeterSphere 使用的 docker 网络网段信息
    MS_DOCKER_SUBNET=172.30.10.0/24
    ## 镜像前缀, MeterSphere 相关组件使用的 Docker 镜像前缀, 例如 registry.cn-qingdao.aliyuncs.com/metersphere
    MS_IMAGE_PREFIX=registry.cn-qingdao.aliyuncs.com/metersphere
    ## 镜像标签, MeterSphere 相关组件使用的 Docker 镜像标签
    MS_IMAGE_TAG=v1.19.1
    ## 性能测试使用的 JMeter 镜像
    MS_JMETER_IMAGE=${MS_IMAGE_PREFIX}/jmeter-master:5.4.3-ms4-jdk8
    ## 安装模式
    MS_INSTALL_MODE=allinone
    ## MeterSphere 主程序的 HTTP 服务监听端口
    MS_SERVER_PORT=8081
    ## MeterSphere Node-Controller 组件的 HTTP 服务监听端口
    MS_NODE_CONTROLLER_PORT=8082
    MS_NODEEXPORTER_PORT=9100

    # 数据库配置
    ## 是否使用外部数据库
    MS_EXTERNAL_MYSQL=false
    ## 数据库地址
    MS_MYSQL_HOST=mysql
    ## 数据库端口
    MS_MYSQL_PORT=3306
    ## 数据库库名
    MS_MYSQL_DB=metersphere
    ## 数据库用户名
    MS_MYSQL_USER=root
    ## 数据库密码
    MS_MYSQL_PASSWORD=Password123@mysql

    # Prometheus 配置
    ## 是否使用外部Prometheus
    MS_EXTERNAL_PROM=false
    MS_PROMETHEUS_PORT=9090

    # Redis 配置
    ## 是否使用外部Redis
    MS_EXTERNAL_REDIS=false
    ## Redis 端口
    MS_REDIS_PORT=6379
    ## Redis 密码
    MS_REDIS_PASSWORD=Password123@redis
    ## Redis地址
    MS_REDIS_HOST=$(hostname -I|cut -d" " -f 1)

    # Kafka 配置
    ## 是否使用外部 Kafka
    MS_EXTERNAL_KAFKA=false
    ## Kafka 地址
    MS_KAFKA_HOST=10.1.*.*
    ## Kafka 端口
    MS_KAFKA_PORT=9092
    ## 性能测试结果数据使用的 Kafka Topic
    MS_KAFKA_TOPIC=JMETER_METRICS
    ## 性能测试日志数据使用的 Kafka Topic
    MS_KAFKA_LOG_TOPIC=JMETER_LOGS
    ## 性能测试定时任务通知使用的 Kafka Topic
    MS_KAFKA_TEST_TOPIC=LOAD_TESTS
    ## 重构后性能测试结果数据使用的 Kafka Topic
    MS_KAFKA_REPORT_TOPIC=JMETER_REPORTS

    # TCP MOCK 端口范围
    MS_TCP_MOCK_PORT=10000-10010

    # Chrome 容器配置
    ## 是否启动Chrome容器
    MS_CHROME_ENABLED=false

     # 修改组件最大内存限制（v2.7以上可以在 /opt/metersphere/.env 里修改某容器服务的最大内存限制，在/opt/metersphere/ 目录下的docker-compose分别定义各自服务的最大属性值，如 api-test 的属性在 docker-compose-api-test.yml 中定义，为 MS_API_MEM_LIMIT）
    MS_API_MEM_LIMIT=1073741824（默认为 1g）
    ```

### 4.3 数据库配置文件说明

!!! info "注意"
    MeterSphere 使⽤ MySQL 5.7 对系统数据进⾏存储。同时 MeterSphere 对数据库部分配置项有要求，请参考下附的数据库配置，修改环境中的数据库配置文件。

    ```
    [mysqld]
    default-storage-engine=INNODB
    lower_case_table_names=1
    table_open_cache=128
    max_connections=2000
    max_connect_errors=6000
    innodb_file_per_table=1
    innodb_buffer_pool_size=1G
    max_allowed_packet=64M
    transaction_isolation=READ-COMMITTED
    innodb_flush_method=O_DIRECT
    innodb_lock_wait_timeout=1800
    innodb_flush_log_at_trx_commit=0
    sync_binlog=0

    server-id=1
    log-bin=mysql-bin
    expire_logs_days = 2
    binlog_format=mixed

    sql_mode=STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION
    skip-name-resolve
    ```
    
    请参考文档中的建库语句创建 MeterSphere 使用的数据库，metersphere-server 服务启动时会自动在配置的库中创建所需的表结构及初始化数据。
    ```mysql
    CREATE DATABASE `metersphere` /*!40100 DEFAULT CHARACTER SET utf8mb4 */
    ```

安装脚本默认使用 /opt/metersphere 目录作为安装目录，MeterSphere 的配置文件、数据及日志等均存放在该安装目录。

### 4.4 安装目录结构说明

!!! info "安装目录结构说明"
    ```
    /opt/metersphere/
    ├── bin                                         #-- 安装过程中需要加载到容器中的脚本
    ├── compose_files                               #-- 根据不同的安装模式，保存需要使用到的 compose 文件信息
    ├── conf                                        #-- MeterSphere 各组件及数据库等中间件的配置文件
    ├── data                                        #-- MeterSphere 各组件及数据库等中间件的数据持久化目录
    ├── docker-compose-base.yml                     #-- MeterSphere 基础 Docker Compose 文件，定义了网络等基础信息 
    ├── docker-compose-kafka.yml                    #-- MeterSphere 自带的 Kafka 所需的 Docker Compose 文件
    ├── docker-compose-mysql.yml                    #-- MeterSphere 自带的 MySQL 所需的 Docker Compose 文件
    ├── docker-compose-node-controller.yml          #-- MeterSphere Node-Controller 组件所需的 Docker Compose文件
    ├── docker-compose-server.yml                   #-- MeterSphere Server 及 Data-Streaming 所需的 Docker Compose文件
    ├── docker-compose-redis.yml                    #-- MeterSphere Redis 组件所需的 Docker Compose文件
    ├── docker-compose-prometheus.yml               #-- MeterSphere Prometheus 组件所需的Docker Compose 文件
    ├── install.conf -> /opt/metersphere/.env       #-- MeterSphere 的配置文件 /opt/metersphere/.env 的软链接
    ├── logs                                        #-- MeterSphere 各组件的日志文件持久化目录
    └── version                                     #-- 安装包对应的 MeterSphere 版本信息
    ```

## 5 执行安装脚本

```sh
# 进入安装包目录
cd metersphere-offline-installer-v1.20.15-lts
# 运行安装脚本
/bin/bash install.sh
# 等待安装脚本执行完成后，查看 MeterSphere 状态
msctl status
```

安装成功后，通过浏览器访问如下页面登录 MeterSphere。

```
地址: http://目标服务器IP地址:8081
用户名: admin
密码: metersphere
```

## 6 配置反向代理
!!! warning "注意"
    如果需要使用 Nginx、Haproxy 等反向代理，需要配置反向代理对 websocket 的支持。以 Nginx 为例，参考的配置内容如下。
    ```
    server {
        listen 80;
        server_name demo.metersphere.com;
        server_tokens off;
        return 301 https://$host$request_uri;
    }
    server {
        listen 443 ssl;
        # RSA certificate
        ssl_certificate /etc/nginx/ssl/metersphere.com/fullchain.cer; # managed by Certbot
        ssl_certificate_key /etc/nginx/ssl/metersphere.com/metersphere.com.key; # managed by Certbot
        server_name  demo.metersphere.com;
        proxy_connect_timeout       300;
        proxy_send_timeout          300;
        proxy_read_timeout          300;
        send_timeout                300;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $remote_addr;
        proxy_set_header X-Forwarded-Host $server_name;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_redirect http:// $scheme://;
        
        location / {
            proxy_pass http://ip:8081;
            client_max_body_size 1000m;
            #access_log off;
            
            # 配置 websocket 支持
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection "upgrade";
        }
    }
    ```
