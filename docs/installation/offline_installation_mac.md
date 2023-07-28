---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

## 1 环境要求
!!! ms-abstract "部署服务器要求"
    * 操作系统: 可运行 Docker 的 Mac 操作系统
    * CPU/内存: 最低要求 4C8G，推荐 8C16G (2.3.0版本及其之后的版本，最低配置 8C16G)
    * 磁盘空间: 50G

## 2 安装部署
### 2.1 安装 Docker
!!! ms-abstract ""
    在应用商店下载 Docker 进行安装，安装后并启动 Docker

### 2.2 Docker 设置
!!! ms-abstract ""
    进行 Docker 设置，需要添加 /opt/metersphere 路径 <br>
![安装docker](../img/installation/mac-install-docker.png){ width="900px" }

### 2.3 安装 MeterSphere
!!! ms-abstract ""
    下载安装包，安装包下载链接: https://community.fit2cloud.com/#/products/metersphere/downloads <br>
![安装MeterSphere](../img/installation/mac-install-metersphere.png){ width="900px" }

!!! ms-abstract ""
    解压安装包 <br>
![安装MeterSphere](../img/installation/mac-install-tar.png){ width="900px" }

!!! ms-abstract ""
    进入解压好的安装包目录 <br>
![安装MeterSphere](../img/installation/cd-mac-install.png){ width="900px" }

!!! ms-abstract ""
    执行安装命令 sh install.sh，安装过程中的提示，输入 y  <br>
![安装MeterSphere](../img/installation/mac-install-sh.png){ width="900px" }

!!! ms-abstract ""
    安装完成，使用 docker ps 查看后台服务都为 healthy 状态，则通过浏览器访问如下地址访问 MeterSphere <br>
    ```
    地址: http://目标服务器IP地址:服务运行端口
    用户名: admin
    密码: metersphere
    ```
![安装MeterSphere](../img/installation/mac-install-server.png){ width="900px" }

![安装MeterSphere](../img/installation/mac-install-localhost.png){ width="900px" }