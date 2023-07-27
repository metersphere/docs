---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! info "注意"
    * WebSocket/MQTT/AMQP 等协议插件包是企业版功能，暂不开源

MeterSphere 支持常用协议外，还支持其他扩展协议，如 WebSocket/MQTT/AMQP 等协议，但是需要在【系统设置-插件管理】界面，上传扩展协议的插件包。

以 MQTT 协议为例，在【系统设置-插件管理】界面下，上传 MQTT 插件
![jenkins-plugin](../../img/system_management/插件管理1.png)

在【接口测试-接口自动化】界面下，新建一个场景，点击场景右下角【+】号，添加 MQTT 相关请求。
![jenkins-plugin](../../img/system_management/插件管理2.png)

![jenkins-plugin](../../img/system_management/插件管理3.png)


