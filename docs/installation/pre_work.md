MeterSphere大规模的性能压测主要取决于三个组件：

■ Node Controller: 为性能测试提供独立节点类型的测试资源池, 接收来自系统的性能测试任务, 动态的启动 JMeter容器完成性能测试<br>
■ Data Streaming: 从 Kafka 中获取性能测试结果数据进行处理后存入 MySQL 数据库<br>
■ Kafka: 接收 JMeter 产生的性能测试结果数据<br>

所以如果需要进行大规模（5000 VU以上）的性能测试，需要对上述三个组件进行水平扩容。具体架构如下：<br>
![配置架构图地址](../img/installation/dis_pressure/架构图.png){:height="100%" width="70%"} <br>

依据架构所示，需要独立部署Kafka集群和Data-Streaming集群（Kafka和Data-Streaming可以部署在一起），如果采用独立主机压测，还需要部署Node-Controller集群。部署步骤:<br>
■ 部署Kafka集群 <br>
■ 部署Data-Streaming集群 <br>
■ 部署Node-Controller集群 <br>

