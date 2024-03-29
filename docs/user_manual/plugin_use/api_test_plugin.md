---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
    MeterSphere 除支持通用的HTTP/HTTPS、TCP、SQL、DUBBO协议外，还可以通过插件的方式支持其它扩展协议，目前企业版本已支持的扩展协议包括：WebSocket/MQTT/AMQP。WebSocket/MQTT/AMQP 等协议插件包是企业版功能，仅向企业客户开放。<br>
    下面以 WebSocket 协议为例，介绍接口测试扩展插件的安装以及使用。

## 1 插件安装

!!! ms-abstract ""
    在【系统设置】-【系统】-【插件管理】界面下，上传 WebSocket 插件。

![jenkins-plugin](../../img/system_management/插件管理1.png){ width="900px" }

## 2 插件使用

!!! ms-abstract ""
    在【接口测试】-【接口自动化】界面下，新建场景，点击场景右下角【+】号，即可添加 WebSocket 相关请求。

![jenkins-plugin](../../img/system_management/插件管理2.png){ width="900px" }
![jenkins-plugin](../../img/system_management/插件管理3.png){ width="900px" }