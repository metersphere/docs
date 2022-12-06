
MeterSphere 作为一站式持续测试平台，其正常运行需要网络环境提供如下的网络端口配置要求，管理员可根据实际环境中 MeterSphere 组件部署的方案，在网络侧和主机侧开放相关端口。

## 网络端口要求

| 组件     | 默认端口     | 说明     |
| -------- | -------- | -------- |
| GateWay | 8081 | API 网关项目，浏览器访问端口 |
| Node Controller | 8082 | 为接口或者性能测试提供独立节点类型的测试资源池 |
| Prometheus | 9090 | 收集压力机及被测系统的监控数据 |
| Node Exporter | 9100 | 用于采集 Node 的运行指标 |
| Selenium Grid | 4444 | 为 UI自动化测试提供运行环境,支持分布式拓展 |
| TCP Mock  | 10000-10010 | TCP Mock 对外提供服务需要开放的端口范围 |
| MySQL | 3307 | MeterSphere 默认安装的数据库对外提供的端口  |
| Redis | 6379 | MeterSphere 默认安装的 Redis 对外提供的端口  |
| Minio | 9000 | MeterSphere 默认安装的分布式对象存储对外提供的端口  |
| Kafka | 9092 | MeterSphere 默认安装的消息中间件对外提供的端口  |
