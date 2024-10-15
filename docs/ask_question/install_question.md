## 1 kafka 服务无法启动
!!! ms-abstract "问题现象"
    kafka 服务起不来，docker logs kafka 看到日志里出现 "/opt/kafka/config/file not writable"
![接口测试](../img/ask_question/api_question/kafka起不来日志.png){ width="900px" }

!!! ms-abstract "解决方法1"
    升级 docker 版本即可。若服务器有网环境，执行

    ```
    yum update
    yum install docker-ce docker-ce-cli containerd.io
    ``` 
    
    若服务器没网，MeterSpher 离线安装包里有离线 docker，执行
    ```
    chmod +x docker/bin/*
    cp docker/bin/* /usr/bin/
    cp docker/service/docker.service /etc/systemd/system/
    chmod 754 /etc/systemd/system/docker.service
    service docker start
    ```

!!! ms-abstract "解决方法2"
    若使用的是离线包自带的 docker 也出现该错误，可以在 `/opt/metersphere/docker-compose-kafka.yml` 里添加 privileged: true 参数后，执行 msctl reload 即可。
![接口测试](../img/ask_question/api_question/kafka的yml添加特权.png){ width="900px" }

## 2 mysql 服务无法启动
!!! ms-abstract "问题现象"
    mysql 服务起不来，docker logs mysql 日志里出现 "Fatal glibc error: CPU does not support x86-64-v2"

!!! ms-abstract "解决方法"
    降低 mysql 的镜像版本。修改安装目录 `/opt/metersphere/docker-compose-mysql.yml` 里 mysql 的镜像版本号后，执行 msctl reload 即可。
![接口测试](../img/ask_question/api_question/降低mysql版本.png){ width="900px" }

## 3 MeterSphere 服务日志出现 Schema `metersphere` contains a failed migration to version 3.2.0.2 !
!!! ms-abstract "问题现象"
    metersphere 容器状态 Restarting ，执行 docker logs metersphere 查看日志
![接口测试](../img/ask_question/install_question/ms服务没启动.png){ width="900px" }

!!! ms-abstract ""
    错误为：Schema `metersphere` contains a failed migration to version 3.2.0.2 !
![接口测试](../img/ask_question/install_question/ms日志.png){ width="900px" }

!!! ms-abstract "解决方法"
    到 github 源码上 https://github.com/metersphere/metersphere/tree/v3.3.0/backend/framework/domain/src/main/resources/migration/3.2.0/ddl 下载文件名为 V3.2.0_2__ga_ddl.sql 的 flyway sql。此处链接 v3.3.0 为安装的版本号，如果不是该版本，可切换到目标版本再下载 sql 文件。
![接口测试](../img/ask_question/install_question/下载sql.png){ width="900px" }

!!! ms-abstract ""
    连接 mysql 切到 metersphere 库，将 sql 文件手动执行一下。执行成功后，修改 metersphere_version 表对应版本 3.2.0.2 的 success 值为 1 后，msctl reload 重启服务即可。
    ```
    update metersphere_version set success=1 where version="3.2.0.2";
    ```
