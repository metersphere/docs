!!! ms-abstract "注意"
    升级前务必检查磁盘容量并对数据库进行备份，详细操作请参考 [MeterSphere 数据备份](./backup_data.md)。

  
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