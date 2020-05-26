## 环境要求

!!! info "部署服务器要求"
    * 操作系统: 任何支持 Docker 的 Linux x64
    * CPU/内存: 4核8G
    * 磁盘空间: 50G

## 下载离线包

请自行下载 MeterSphere 完整离线包，并复制到目标机器的 /tmp 目录下

!!! tip "下载链接"
    https://github.com/KubeOperator/KubeOperator/releases

## 解压离线包

以 root 用户 ssh 登录到目标机器, 并执行如下命令

```sh
cd /tmp
# 解压离线包
tar zxvf metersphere-v1.0.0-release.tar.gz
```

## 修改安装配置(可选)

进入安装包解压后的目录，编辑修改安装参数

```sh
cd metersphere-v1.0.0-release
vim install.conf
```

??? info "安装配置文件说明, 如果无特殊需求可以不进行修改采用默认参数安装"
    ```vim
    # MeterSphere 安装目录的上级目录, MeterSphere 将安装在 ${base_dir}/metersphere 目录中
    #base_dir=/opt
    # MeterSphere 相关组件所使用 Docker 镜像的镜像标签
    #metersphere_image_tag
    # 安装模式, 支持的安装模式有 allinone | server | node_controller 三种
    #install_mode=allinone
    # MeterSphere Server 组件的服务端口
    #metersphere_server_port=8081
    # 是否使用外部 MySQL 数据库
    #external_mysql=false
    # MySQL 数据库地址, 仅在 external_mysql=true 时有效
    #mysql_host=mysql
    # MySQL 数据库端口, 仅在 external_mysql=true 时有效
    #mysql_port=3306
    # MySQL 数据库名称, 仅在 external_mysql=true 时有效
    #mysql_dbname=metersphere
    # MySQL 数据库用户名, 仅在 external_mysql=true 时有效
    #mysql_username=root
    # MySQL 数据库密码, 仅在 external_mysql=true 时有效
    #mysql_password=Password123@mysql
    # 是否使用外部 Kafka
    #external_kafka=false
    # 用于接收性能测试结果数据的 Kafka Topic 名称, 仅在 external_kafka=true 时有效
    #kafka_topic=JMETER_METRICS
    # Kafka 连接地址, 仅在 external_kafka=true 时有效
    #kafka_host=本机IP地址
    # Kafka 连接端口, 仅在 external_kafka=true 时有效
    #kafka_port=19092
    # 用于接收性能测试日志数据的 Kafka Topic 名称, 仅在 external_kafka=true 时有效
    #kafka_log_topic=JMETER_LOGS
    ```

在安装包解压后所在目录，执行如下命令

```sh
./msctl.sh install
```

安装脚本默认使用 /opt/metersphere 目录作为安装目录，MeterSphere 的配置文件、数据及日志等均存放在该安装目录

## 执行安装脚本

```sh
# 进入项目目录
cd metersphere-v1.0.0-release
# 运行安装脚本
./install.sh
# 查看 MeterSphere 状态
msctl status
```