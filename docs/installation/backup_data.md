主要是 mysql 数据库数据备份以及 /opt/metersphere/data 路径下的 body 和 jar 目录备份
## 1 手动备份

```
#数据库备份：
docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere > metersphere.sql

#body/jar 目录备份
zip -r XXX.zip /opt/metersphere/data/body /opt/metersphere/data/jar
```
若备份数据库时出现mysqldump: Error 2020: Got packet bigger than ‘max_allowed_packet’ bytes when dumping tableapi_scenario_report_detailat row: 94，则添加max_allowed_packet参数，如下:
```
docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere --max_allowed_packet=2G > metersphere.sql
```

## 2 定时任务自动备份

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
zip -r $backupZipFileName $dumpSqlFilePath $data/body $data/jar
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

timedate_fields="0 1 * * *"
cmd="bash /opt/db_bak/ms_db_back.sh"
crontab -l | grep "$cmd " > /dev/null 2>&1
if test $? -ne 0; then
    crontab -l > crontab.tmp
    echo "$timedate_fields $cmd" >> crontab.tmp
    crontab crontab.tmp
fi
```