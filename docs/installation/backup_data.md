---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract "概述"
    本文介绍了手动和自动两种备份方式，其中自动备份的脚本只备份数据库，备份完成后打包推送到指定服务器目录。<br>
    备份脚本中有多个变量可根据实际情况修改，用于满足不同的使用场景。

!!! ms-abstract "注意"
    1. 备份脚本中，默认保留最近的7份备份文件。（如每天备份一次，则保留最近7天的备份文件。）<br>
    2. 为加强数据的安全性，备份脚本中采取的本地加异地备份。

## 1 数据备份
### 1.1 手动备份
!!! ms-abstract ""

    ```
    # 数据库备份：
    docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere > metersphere.sql
    
    # data 目录备份 （以实际安装目录为准，默认 /opt 目录）
    tar -cvf data_backup.tar /opt/metersphere/data --exclude=/opt/metersphere/data/kafka --exclude=/opt/metersphere/data/mysql --exclude=/opt/metersphere/data/redis --exclude=/opt/metersphere/data/prometheus
    ```

### 1.2 自动备份

!!! ms-abstract ""

    1. 自动备份前需先生成 SSH 密钥对，并将公钥复制到备份服务器。
    ```
    ssh-keygen -t rsa
    ```

    2. 将公钥复制到远程服务器。
    ```
    ssh-copy-id remote_user@remote_host
    ```

    3. 创建用于数据备份的脚本文件
    ```
    vi ms_backup.sh
    ```
    
    4. 把以下内容复制到刚才创建的 ms_backup.sh 脚本中（查看脚本中的参数，与实际场景是否相符）
    ```
    #!/bin/bash

    #历史备份数据保留天数
    keepBackupNum=7
    #备份文件输出目录
    backupDir=/opt/db_bak
    #数据库用户名
    username=root
    #数据库密码
    password=Password123@mysql
    #需要备份的库名
    dbName=metersphere
    #备份文件的后缀名称
    currentTime=`date "+%Y-%m-%d-%H-%M-%S"`
    #备份文件的完整名称
    backupTarFileName=ms_db_$currentTime.tar.gz
    #导出sql文件的完整名称
    dumpSqlFile=ms_db_$currentTime.sql
    #推送远程服务器ip地址
    remoteIp=10.1.11.12
    #推送远程服务器用户名
    remoteUser=root
    #推送远程服务器目录
    remotePath=/opt
    #数据库是否内置
    isBuiltIn=true

    echo dumpSqlFilePath=$backupDir/$backupTarFileName

    #没有备份文件夹则创建
    if [  ! -d  "$backupDir" ];then
        mkdir -p "$backupDir"
    else
        echo "--------------开始进行备份-----------------"
    fi

    if [ "${isBuiltIn}" = "true" ]; then
        docker exec -i mysql mysqldump -u${username} -p${password} ${dbName} --max_allowed_packet=2G > $dumpSqlFile
    else
        mysqldump -u${username} -p${password} ${dbName} --max_allowed_packet=2G > $dumpSqlFile
    fi
    
    cd $backupDir
    tar -cvf ms_data_backup.tar /opt/metersphere/data --exclude=/opt/metersphere/data/kafka --exclude=/opt/metersphere/data/mysql --exclude=/opt/metersphere/data/redis --exclude=/opt/metersphere/data/prometheus
    tar -zcvf  $backupTarFileName $dumpSqlFile ms_data_backup.tar
    #发送备份文件到远程机器
    scp $backupTarFileName $remoteUser@$remoteIp:$remotePath  2>> "error.log"
    
    if [ $? -eq 0 ]; then
        echo "---------------远程备份完成----------------"
    else
        echo "---------------远程备份失败----------------"
    fi
    
    rm -rf $backupDir/$dumpSqlFile ms_data_backup.tar
    
    #remove outdated backup files
    
    output=`ls -lt $backupDir/*.tar.gz | awk '{print $9}'`
    step=0
    echo "---------------开始清理$keepBackupNum天前备份数据----------------"
    for backupFile in $output ;do
        step=$((step+1))
        echo step=$step
        echo $backupFile
        if [ $step -gt $keepBackupNum ];then
            echo Remove outdated backup $backupFile
            rm -rf  $backupFile
        fi
    done
    echo "---------------结束清理$keepBackupNum天前备份数据----------------"
    ```

    5. 创建用于定时任务脚本文件
    ```
    vi install_ms_backup.sh
    ```
    
    6. 把以下内容复制到刚才创建的 install_ms_backup.sh 脚本中（查看脚本中的参数，与实际场景是否相符）
    ```
    #!/bin/bash
    
    timedate_fields="0 1 * * *"  #每天凌晨1:00执行备份程序
    cmd="bash /opt/db_bak/ms_backup.sh"
    crontab -l | grep "$cmd " > /dev/null 2>&1
    if test $? -ne 0; then
        crontab -l > crontab.tmp
        echo "$timedate_fields $cmd" >> crontab.tmp
        crontab crontab.tmp
    fi
    ```

    7. 执行 install_ms_backup.sh 文件（如果遇到文件权限问题，可以使用 chmod 命令增加权限），然后使用 crontab -l 命令即可查看定时任务

## 2 数据还原
!!! ms-abstract ""
    还原 sql 数据，进入备份 sql 目录，将 sql 复制到 mysql 容器的挂载目录 /opt/metersphere/data/mysql 下
    ```
    cp metersphere.sql /opt/metersphere/data/mysql
    ```
    
    进入 mysql 容器，登录数据库
    ```
    docker exec -it mysql sh
    mysql -uroot -pPassword123@mysql
    ```
    
    使用 metersphere 库，并将数据导入到库里
    ```
    use metersphere;
    source /var/lib/mysql/metersphere.sql
    ```

!!! ms-abstract ""
    还原 data 目录数据，进入 data_backup.tar 所在目录
    ```
    tar -xvf data_backup.tar
    ```
    
