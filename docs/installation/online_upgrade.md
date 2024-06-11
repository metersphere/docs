

!!! ms-abstract ""
    升级前一定要进行数据库备份，请参考 [MeterSphere 数据备份](./backup_data.md)。<br>

## 1 一键升级至最新版本
!!! ms-abstract ""
    ```
    #完成数据备份后，停止服务
    msctl stop

    # 升级至最新版本
    msctl upgrade

    # 升级至指定版本
    msctl upgrade v3.x.y
    
    # 查看 MeterSphere 状态
    msctl status
    ```

