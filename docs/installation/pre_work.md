---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
    MeterSphere 大规模的性能压测主要取决于三个组件

    ■ Node Controller: 为性能测试提供独立节点类型的测试资源池， 接收来自系统的性能测试任务， 动态的启动 JMeter 容器完成性能测试<br>
    ■ Data Streaming: 从 Kafka 中获取性能测试结果数据进行处理后存入 MySQL 数据库<br>
    ■ Kafka: 接收 JMeter 产生的性能测试结果数据
    
    所以如果需要进行大规模（5000 VU以上）的性能测试，需要对上述三个组件进行水平扩容。具体架构如下：<br>
![配置架构图地址](../img/installation/dis_pressure/架构图.png){:height="100%" width="70%"} <br>

!!! ms-abstract ""
    依据架构所示，需要独立部署 Kafka 集群和 Data-Streaming 集群（Kafka和Data-Streaming可以部署在一起），如果采用独立主机压测，还需要部署 Node-Controller 集群。部署步骤:<br>
    
    ■ 部署 Kafka 集群 <br>
    ■ 部署 Data-Streaming 集群 <br>
    ■ 部署 Node-Controller 集群

