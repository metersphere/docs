---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
    升级前一定要进行数据库备份，请参考 [MeterSphere 数据备份](./backup_data.md)。<br>
    如果 MeterSphere 服务器可以访问互联网，且在线升级版本跨度不大，可通过以下方式升级到最新或指定版本。<br>
    【注意】如果升级版本跨度较大，如 V1.x 升级至 V2.x 版本，由于版本新增变更功能较多，且 v2.8.1 之后docker 使用版本升级，避免网络因素影响建议采用离线升级方式。详细步骤可参考： [MeterSphere 企业版1.20 LTS 至2.10 LTS 升级指南](https://kb.fit2cloud.com/?p=9a46f075-5cfe-46de-81f8-ab5278699697)

## 1 一键升级至最新版本
!!! ms-abstract ""
    ```
    #升级前停止服务
    msctl stop

    # 升级至最新版本
    msctl upgrade
    
    # 查看 MeterSphere 状态
    msctl status
    ```

## 2 一键升级至指定版本
!!! ms-abstract ""
    ```
    #升级前停止服务
    msctl stop
    
    # 升级至指定版本
    msctl upgrade v2.x.y
    
    # 查看 MeterSphere 状态
    msctl status
    ```
 <!-- 
## 3 离线升级
!!! ms-abstract ""
   ，如果升级版本跨度不大，则按照下面说明升级即可。
    ```
    MeterSphere 安装包下载链接: https://github.com/metersphere/metersphere/releases

    # 下载在线安装包
    wget https://github.com/metersphere/metersphere/releases/download/v2.x.y/metersphere-online-installer-v2.x.y.tar.gz
    
    # 解压在线安装包
    tar -zxvf metersphere-online-installer-v2.x.y.tar.gz
    
    # 进入解压缩目录
    cd metersphere-online-installer-v2.x.y
    
    # 执行 install.sh 安装脚本
    /bin/bash install.sh
    ```
--> 