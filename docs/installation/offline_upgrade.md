---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract "注意"
    升级前务必检查磁盘容量并对数据库进行备份，详细操作请参考 [MeterSphere 数据备份](./backup_data.md)。

## 1 下载并解压安装包
!!! ms-abstract ""
    按照本文档 [离线安装](./offline_installation.md) 步骤， 下载新版本安装包解压，执行安装命令进行升级。<br>
  
## 2 执行安装命令
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
    ```
