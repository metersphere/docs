---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

## 1 一键部署
!!! ms-abstract ""
    准备好部署服务器后，可通过 MeterSphere 快速安装脚本一键快速部署。一键安装采用默认安装参数，更多有关离线部署、容器部署、分布式部署等方式可查看【**安装部署**】章节内容。<br>

    **部署服务器要求**：<br>

     - 操作系统要求：CentOS 7.x
     - CPU内存要求：最低要求 4C8G，推荐 8C16G
     - 部署目录空间（默认/opt目录）要求：50G
     - 网络要求：可访问互联网
     - 如用于生产环境，推荐使用 [离线安装包](https://community.fit2cloud.com/#/products/metersphere/downloads) 进行部署


    以 root 用户 ssh 登录部署目标服务器，执行以下脚本进行一键安装:<br>
    ```sh
    curl -sSL https://resource.fit2cloud.com/metersphere/metersphere/releases/latest/download/quick_start.sh | bash
    ```

    安装成功后，客户端通过浏览器访问以下地址，输入用户名和密码，即可开始使用 MeterSphere。
    ```
    地址: http://目标服务器IP地址:8081
    默认用户名: admin
    默认密码: metersphere
    ```

## 2 界面说明
!!! ms-abstract ""
    进入 MeterSphere 主界面后可以看到界面左边是导航栏，包括【工作台】【测试跟踪】【接口测试】【UI 测试】【性能测试】【报表统计】【项目设置】【系统设置】八个模块，其中 UI 测试是企业版本 X-Pack的功能，界面上方以 Tab 页方式展示当前模块的具体功能。

![界面说明](../img/界面说明.png){ width="900px" }
