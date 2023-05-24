!!! ms-abstract ""
    升级前一定要进行数据库备份，请参考 [MeterSphere 数据备份](./backup_data.md)。<br>
    如果 MeterSphere 服务器可以访问互联网，可通过以下方式升级到最新或指定版本。

## 1 一键升级至最新版本
!!! ms-abstract ""
    ```
    # 升级至最新版本
    msctl upgrade
    
    # 查看 MeterSphere 状态
    msctl status
    ```

## 2 一键升级至指定版本
!!! ms-abstract ""
    ```
    # 升级至指定版本
    msctl upgrade v2.x.y
    
    # 查看 MeterSphere 状态
    msctl status
    ```

## 3 手动升级
!!! ms-abstract ""
    MeterSphere 安装包下载链接: https://github.com/metersphere/metersphere/releases
    ```
    # 下载在线安装包
    wget https://github.com/metersphere/metersphere/releases/download/v2.x.y/metersphere-online-installer-v2.x.y.tar.gz
    
    # 解压在线安装包
    tar -zxvf metersphere-online-installer-v2.x.y.tar.gz
    
    # 进入解压缩目录
    cd metersphere-online-installer-v2.x.y
    
    # 执行 install.sh 安装脚本
    /bin/bash install.sh
    ```
