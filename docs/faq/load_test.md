## 是否支持/如何支持分布式的性能测试？

MeterSphere 通过在测试资源池中添加多个测试执行节点的方式来支持分布式的性能测试。在我们向一个测试资源池中添加节点时，除了节点的 IP、端口信息外，还需要根据该节点的机器规格，配置该节点可以支持的最大并发数。当我们在执行性能测试的过程中选择了某个测试资源池时，MeterSphere 会将本次性能测试定义的并发用户数，按照所选测试资源池的节点支持的最大并发数进行按比例拆分，在测试开始执行后，每个测试执行节点会将测试结果、测试日志等信息输送到执行的 Kafka 队列中，MeterSphere 中的 data-streaming 组件会从 Kafka 中收集这些信息并进行汇总处理。

例如当我们在系统中存在一个如下配置的测试资源池，并选择该测试资源池执行一个 10000 并发用户的性能测试时，node1 及 node2 将各分配 4000 个并发用户，node3 将分配 2000 个并发用户。

![测试资源池](../img/system_management/编辑测试资源池.png)

## 如何向测试资源池中添加节点？

首先需要在要添加的节点上部署 MeterSphere 的 node-controller 组件，安装方式参考本文档[「在线安装」](installation/online_installation.md)或[「离线安装」](installation/offline_installation.md)章节内容，在执行安装脚本前，修改 install.conf 文件中的 MS_MODE 字段的值为 node-controller 后执行安装脚本。

安装完成通过查看组件状态是否正常

```bash
msctl status
```

当组件状态正常后，使用管理员账号登录 MeterSphere，在「系统设置」-「系统」-「测试资源池」页面添加或编辑已有测试资源池，在弹出的页面中增加一个节点，IP 地址为要添加的测试执行节点的 IP，端口默认为 8082，最大并发数根据测试执行节点的机器规格进行配置。

节点添加完成点击确定后系统将对节点状态进行检查，若测试资源池为可用状态则说明该测试资源池及其中的节点可以正常使用。若提示校验不通过，请登录测试执行节点通过如下命令查看组件日志。

```bash
docker logs ms-node-controller
```

## 执行性能测试时提示“Kafka 不可用，请检查配置“如何解决？

系统在执行性能测试之前，会先检查安装系统时配置的 Kafka 地址是否可用。当提示该信息时，表明 MeterSphere 无法正常连接到 Kafka，可以通过以下方式进行排查定位。

### 排查思路

![Kafka 不可用排查](../img/kafka_invalid.png)

### 检查 Kafka 是否正常运行
如果在安装时使用的外部的 Kafka，请联系相关人员进行排查，检查 Kafka 服务是否正常；如果安装时使用 MeterSphere 默认配置进行安装，使用了自带的 Kafka 服务，请通过如下命令进行排查。
```bash
# 检查各组件的运行状态
msctl status
# 若 Kafka 容器不处于 `healthy` 状态，查看 Kafka 日志进行进一步排查
docker logs kafka
```
### 检查 MeterSphere 到 Kafka 服务的网络连接
若 Kafka 服务状态正常，请通过如下命令检查 ms-server 容器是否能正常连接到 Kafka 服务
```bash
# 检查 ms-server 是否能正常访问 Kafka 服务
[root@meter-prototype ~]# docker exec ms-server nc -zv ${kafka 服务 IP} ${kafka 服务端口}
kafka (172.23.0.5:19092) open
```
如果在安装时使用的外部的 Kafka，请联系相关人员进行排查，检查 MeterSphere 部署服务器到 Kafka 服务之间的网络连接是否正常，是否有防火墙、安全组等安全策略的影响；如果安装时使用 MeterSphere 默认配置进行安装，使用了自带的 Kafka 服务，请检查 MeterSphere 部署服务器上的防火墙配置，是否放通了 Kafka 的服务端口（默认 19092），也可以选择直接禁用防火墙后，重启 docker 服务和 MeterSphere 组件进行重试。
```bash
# 以 CentOS 7 操作系统为例，禁用防火墙及重启服务命令
systemctl stop firewalld
systemctl restart docker
msctl start
```
若检查发现网络连接状态正常，在执行性能测试时仍旧提示该错误，请联系我们的团队进行进一步定位。