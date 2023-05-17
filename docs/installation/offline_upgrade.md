!!! ms-abstract "注意"
    升级前一定要进行数据备份，可参考 [MeterSphere 数据备份](./backup_data.md)。

## 1 下载并解压安装包
!!! ms-abstract ""
    按照本文档 [离线安装](./offline_installation.md) 步骤, 下载新版本安装包并上传解压后, 重新执行安装命令进行升级。

## 2 执行安装命令
!!! ms-abstract ""

    ```sh
    # 进入离线部署包解压缩目录
    cd metersphere-offline-installer-v2.x.y
    
    # 运行安装脚本
    /bin/bash install.sh
    
    # 查看 MeterSphere 状态
    msctl status
    ```
