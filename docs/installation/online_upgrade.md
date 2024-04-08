---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
    升级前一定要进行数据库备份，请参考 [MeterSphere 数据备份](./backup_data.md)。<br>

## 1 一键升级至最新版本
!!! ms-abstract ""
    ```
    #完成数据备份后，停止服务
    msctl stop

    # 升级至最新版本
    msctl upgrade
    
    # 查看 MeterSphere 状态
    msctl status
    ```

## 2 一键升级至指定版本
!!! ms-abstract ""
    ```
    #完成数据备份后，停止服务
    msctl stop

    # 升级至指定版本
    msctl upgrade v3.x.y
    
    # 查看 MeterSphere 状态
    msctl status
    ```
