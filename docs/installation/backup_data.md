---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

主要是 MySQL 数据库的数据备份和 /opt/metersphere/data 路径下的目录备份。

!!! warning "注意"
    数据库主要有 mysqldump 和 手动备份 /opt/metersphere/data/mysql 目录两种方式，可根据实际情况和已有备份工具制定备份策略和备份手段

## 1 手动备份

```
#数据库备份：
docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere > metersphere.sql

#data 目录备份
zip -r XXX.zip /opt/metersphere/data
```
若备份数据库时出现mysqldump: Error 2020: Got packet bigger than ‘max_allowed_packet’ bytes when dumping tableapi_scenario_report_detailat row: 94，则添加max_allowed_packet参数，如下:
```
docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere --max_allowed_packet=2G > metersphere.sql
```

## 2 定时任务自动备份
1. 自动备份前需先生成 SSH 密钥对，并将公钥复制到备份服务器。
    ```
    ssh-keygen -t rsa
    ```
2. 将公钥复制到远程服务器。
   ```
   ssh-copy-id remote_user@remote_host
   ```
3. ms_backup.sh
```
#!/bin/bash

remote_user="username"     #备份服务器用户名
remote_host="remote_host"  #备份服务器IP地址
remote_path="remote_path"  #备份服务器目录
backupDir=/opt/db_bak    
data=/opt/metersphere/data
currentTime=`date "+%Y-%m-%d-%H-%M-%S"`   
backupZipFileName=ms_db_$currentTime.zip  
dumpSqlFilePath=$backupDir/ms_db_$currentTime.sql  
echo dumpSqlFilePath=$dumpSqlFilePath
docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere --max_allowed_packet=2G > $dumpSqlFilePath
cd $backupDir
zip -r $backupZipFileName $dumpSqlFilePath $data

#scp 将备份的数据库文件上传到备份服务器对应目录下
scp $backupZipFileName remote_user@remote_host:$remote_path
 
echo rm -rf dumpSqlFilePath
rm -rf $backupDir/ms_db_$currentTime.sql

#保留最近7天的备份，可根据实际情况调整。
keepBackupNum=7
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

执行 crontab -l 即可

## 3 数据恢复
进入备份 sql 目录，将 sql 复制到 mysql 容器的挂载目录 /opt/metersphere/data/mysql 下
```
cp metersphere.sql /opt/metersphere/data/mysql
```

进入 mysql 容器，进入数据库
```
docker exec -it mysql sh
mysql -uroot -pPassword123@mysql
```

使用 metersphere 库，并将数据导入到库里
```
use metersphere;
source /var/lib/mysql/metersphere.sql
```