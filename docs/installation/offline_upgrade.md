---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract "注意"
    升级前一定要进行数据库备份，详细操作请参考 [MeterSphere 数据备份](./backup_data.md)。

## 1 下载并解压安装包
!!! ms-abstract ""
    按照本文档 [离线安装](./offline_installation.md) 步骤， 下载新版本安装包并上传解压后, 重新执行安装命令进行升级。<br>
    【注意】如果升级版本跨度较大：如 V1.x 升级至 V2.x 最新版本，由于跨多版本新增功能较多，且 v2.8.1 之后docker 使用版本升级，请按照升级指南操作： [MeterSphere 1.20 LTS 至2.10 LTS 升级指南](https://kb.fit2cloud.com/?p=9a46f075-5cfe-46de-81f8-ab5278699697)。如果升级版本跨度不大，则按照下面说明升级即可。

## 2 执行安装命令
!!! ms-abstract ""

    ```
    #升级前停止服务
    msctl stop

    MeterSphere 安装包下载链接: https://github.com/metersphere/metersphere/releases

    # 下载在线安装包
    wget https://github.com/metersphere/metersphere/releases/download/v2.x.y/metersphere-online-installer-v2.x.y.tar.gz
    
    # 解压在线安装包
    tar -zxvf metersphere-online-installer-v2.x.y.tar.gz

    # 进入离线部署包解压缩目录
    cd metersphere-offline-installer-v2.x.y
    
    # 运行安装脚本
    /bin/bash install.sh
    
    # 查看 MeterSphere 状态
    msctl status
    ```
