---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! warning "注意"
    升级前一定要进行数据备份，可参考 [MeterSphere 数据备份](./backup_data.md)。

## 1 下载并解压安装包
按照本文档 [离线安装](./offline_installation.md) 步骤, 下载新版本安装包并上传解压后, 重新执行安装命令进行升级。

## 2 执行安装命令

```sh
# 进入离线部署包解压缩目录
cd metersphere-offline-installer-v1.20.x-lts

# 运行安装脚本
/bin/bash install.sh

# 查看 MeterSphere 状态
msctl status
```