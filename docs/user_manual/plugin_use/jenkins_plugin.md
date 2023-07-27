---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

## 1 插件下载
要想实现在 Jenkins 中完成 MeterSphere 自动化接口测试，需要在 Jenkins 上安装 MeterSphere 提供的 Jenkins 插件。
```
插件下载地址: https://github.com/metersphere/jenkins-plugin/releases
下载 MeterSphere 对应版本的 hpi 包,在 Jenkins 的插件管理页面，上传并安装下载好的 hpi 插件包
```

## 2 插件使用
插件安装后，在指定的 Jenkins 构建任务中，添加【MeterSphere】类型的构建步骤
![录制](../../img/user_manual/plugin_use/jenkins_plugin/add_jenkins_1.png)

通过配置 MeterSphere 认证信息，并指定需要触发执行的接口测试、性能测试或测试计划。
![](../../img/user_manual/plugin_use/jenkins_plugin/add_jenkins_2.png)
