---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract "注意"
    主要是 MySQL 数据库的数据备份和 /opt/metersphere/data 路径下的目录备份。<br>
    数据库主要有 mysqldump 和 手动备份 /opt/metersphere/data/mysql 目录两种方式，可根据企业实际情况和已有备份工具制定备份策略和备份手段

## 1 数据备份
### 1.1 手动备份
!!! ms-abstract ""
    ```
    #数据库备份：
    docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere > metersphere.sql
    
    #data 目录备份
    tar -cvf data_backup.tar /opt/metersphere/data
    ```
    若备份数据库时出现`mysqldump: Error 2020: Got packet bigger than ‘max_allowed_packet’ bytes when dumping tableapi_scenario_report_detailat row: 94`，则添加max_allowed_packet参数，如下:
    ```
    docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere --max_allowed_packet=2G > metersphere.sql
    ```

### 1.2 自动备份
!!! ms-abstract ""
    ms_backup.sh
    ```
    #!/bin/bash
    
    backupDir=/opt/db_bak    
    data=/opt/metersphere/data
    currentTime=`date "+%Y-%m-%d-%H-%M-%S"`   
    backupZipFileName=ms_db_$currentTime.zip  
    dumpSqlFilePath=$backupDir/ms_db_$currentTime.sql  
    echo dumpSqlFilePath=$dumpSqlFilePath
    docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere --max_allowed_packet=2G > $dumpSqlFilePath
    cd $backupDir
    zip -r $backupZipFileName $dumpSqlFilePath $data
    echo rm -rf dumpSqlFilePath
    rm -rf $backupDir/ms_db_$currentTime.sql
    
    #remove outdated backup files
    keepBackupNum=3
    output=`ls -lt $backupDir/*.zip | awk '{print $9}'`
    step=0
    for backupFile in $output ;do
        step=$((step+1))
        echo step=$step
        echo $backupFile
        if [ $step -gt $keepBackupNum ];then
            echo Remove outdated backup $backupFile
            rm -rf  $backupFile
        fi
    done
    ```

    install_ms_backup.sh
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

    执行 crontab -l 即可查看定时任务

## 2 数据还原
!!! ms-abstract ""
    进入备份 sql 目录，将 sql 复制到 mysql 容器的挂载目录 /opt/metersphere/data/mysql 下
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