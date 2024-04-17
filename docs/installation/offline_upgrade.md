!!! ms-abstract "注意"
    升级前务必检查磁盘容量并对数据库进行备份，详细操作请参考 [MeterSphere 数据备份](./backup_data.md)。
    升级过程避免数据库执行定时任务造成数据操作损坏数据，请关闭正在运行的定时任务：
     ```
        #进入数据库
        docker exec -it mysql sh
        mysql -uroot -pPassword123@mysql
        #关闭定时任务。
        use metersphere;
        update schedule set enable=0;
        #退出
        exit;
     ```

  
## 1 执行安装命令
!!! ms-abstract ""

    ```
    #完成数据备份并停止服务
    msctl stop

    # 下载离线安装包并上传到服务器
    安装包下载链接: https://community.fit2cloud.com/#/products/metersphere/downloads
    
    # 解压安装包
    tar -zxvf metersphere-offline-installer-v3.x.y.tar.gz

    # 进入离线部署包解压缩目录
    cd metersphere-offline-installer-v3.x.y
    
    # 运行安装脚本
    /bin/bash install.sh
    
    # 查看 MeterSphere 状态，各个组件都是 healthy 状态升级完成。
     msctl status

!!! ms-abstract ""
     升级完成后，批量启用定时任务。
     ```
        #进入数据库
        docker exec -it mysql sh
        mysql -uroot -pPassword123@mysql
        #开启定时任务。
        use metersphere;
        update schedule set enable=1;
        #退出
        exit;
     ```