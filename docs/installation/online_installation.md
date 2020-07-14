## 环境要求

!!! info "部署服务器要求"
    * 操作系统: CentOS 7.x
    * CPU/内存: 4核8G
    * 磁盘空间: 50G
    * 可访问互联网

## 下载安装包

请自行下载 MeterSphere 最新版本的在线安装包，并复制到目标机器的 /tmp 目录下

!!! tip ""
    安装包下载链接: https://github.com/metersphere/metersphere/releases

## 解压安装包

以 root 用户 ssh 登录到目标机器, 并执行如下命令

```sh
cd /tmp
# 解压安装包
tar zxvf metersphere-release-v1.0.3.tar.gz
```

## 修改安装配置(可选)

在安装包解压后的目录，编辑修改安装参数

```sh
cd metersphere-release-v1.0.3
vim install.conf
```

??? info "安装配置文件说明, 如果无特殊需求可以不进行修改采用默认参数安装"
    ```vim
    # 基础配置
    ## MeterSphere 安装目录的上级目录, MeterSphere 将安装在 ${base_dir}/metersphere 目录中
    MS_BASE=/opt
    ## MeterSphere 相关组件所使用 Docker 镜像的镜像地址前缀
    MS_PREFIX=''
    ## MeterSphere 相关组件所使用 Docker 镜像的镜像标签
    MS_TAG=dev
    ## 安装模式, 支持的安装模式有 allinone | server | node-controller 三种
    MS_MODE=allinone
    ## MeterSphere Web 服务的监听端口
    MS_PORT=8081
    ## Node controller Web 服务的监听端口
    MS_NODE_CONTROLLER_PORT=8082

    # 数据库配置
    ## 是否使用外部 MySQL 数据库
    MS_EXTERNAL_MYSQL=false
    ## MySQL 数据库地址，仅在使用外部数据库时修改
    MS_MYSQL_HOST=mysql
    ## MySQL 数据库端口，仅在使用外部数据库时修改
    MS_MYSQL_PORT=3306
    ## MySQL 数据库库名, 仅在使用外部数据库时修改
    MS_MYSQL_DB=metersphere
    ## MySQL 数据库用户名
    MS_MYSQL_USER=root
    ## MySQL 数据库密码
    MS_MYSQL_PASSWORD=Password123@mysql

    # Kafka 配置
    ## 是否使用外部 kafka
    MS_EXTERNAL_KAFKA=false
    ## Kafka 地址, 仅在使用外部 Kafka 时修改
    MS_KAFKA_HOST=$(hostname -I|cut -d" " -f 1)
    ## Kafka 端口, 仅在使用外部 Kafka 时修改
    MS_KAFKA_PORT=19092
    ## Kafka Topic
    MS_KAFKA_TOPIC=JMETER_METRICS
    ## Kafka Log Topic
    MS_KAFKA_LOG_TOPIC=JMETER_LOGS

    ```

安装脚本默认使用 /opt/metersphere 目录作为安装目录，MeterSphere 的配置文件、数据及日志等均存放在该安装目录

## 执行安装脚本

```sh
# 进入安装包目录
cd metersphere-release-v1.0.3
# 运行安装脚本
/bin/bash install.sh
# 等待安装脚本执行完成后，查看 MeterSphere 状态
msctl status
```

安装成功后，通过浏览器访问如下页面登录 MeterSphere

```
地址: http://目标服务器IP地址:8081
用户名: admin
密码: metersphere
```

## 升级

按照本文档前述步骤, 下载新版本安装包并上传解压后, 重新执行安装命令进行升级

```sh
# 进入项目目录
cd metersphere-v1.x.y-release
# 运行安装脚本
/bin/bash install.sh
# 查看 MeterSphere 状态
msctl status
```

!!! warning "注意"
    如果在旧版本安装过程中有修改安装目录(默认为 /opt 目录), 在执行升级脚本前需要修改 install.conf 文件并配置安装目录为旧版本的安装目录 

