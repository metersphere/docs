---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---


MeterSphere 默认内置了命令行运维工具 - msctl，通过执行 msctl help 命令，可以查看相关的帮助文档。

## msctl

!!! Abstract "" 
    MeterSphere 默认内置了命令行运维工具 - msctl，通过执行 msctl help 命令，可以查看相关的帮助文档。

```
MeterSphere 控制脚本

Usage: 
  ./msctl.sh [COMMAND] [ARGS...]
  ./msctl.sh --help

Commands: 
  status    查看 MeterSphere 服务运行状态
  start     启动 MeterSphere 服务
  stop      停止 MeterSphere 服务
  restart   重启 MeterSphere 服务
  reload    重新加载 MeterSphere 服务（修改配置文件 /opt/metersphere/.env 时，运行此命令使配置生效）
  upgrade   升级 MeterSphere 至最新版本
  upgrade [RELEASE]  根据版本号搜索离线包，升级 MeterSphere 至对应版本
  uninstall 卸载 MeterSphere 服务
  version   查看 MeterSphere 版本信息
```
