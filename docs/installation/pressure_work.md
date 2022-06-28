!!! info "基于以上环境部署成功后，进行如下压测工作"

### 1 修改MeterSphere的docker-compose-server.yaml文件

按照下图修改为连接Kafka地址

![配置修改Kafka地址](../img/installation/dis_pressure/修改kafka地址.png){:height="100%" width="70%"} <br>

### 2 如果采用k8s集群压测，需要提前准备好k8s集群，创建好SA和token，创建如下：

```
1、创建namespaces
kubectl create namespace metersphere

2、创建SA
kubectl create serviceaccount ms -n metersphere

3、创建namespace授权SA
kubectl create clusterrolebinding ms --clusterrole=admin --serviceaccount=metersphere:ms -n metersphere

4.查询SA token
kubectl describe sa/ms -n metersphere
kubectl describe secrets -n metersphere ms-token-xxxx
```

k8s对接界面配置如下，注意需要调整JMeter配置，经过测试，2500左右的VU，在无大量错误的情况下需要消耗2C4G左右资源:<br>
![配置k8s设置地址](../img/installation/dis_pressure/k8s设置.png){:height="100%" width="70%"} <br>

### 3 最终压测效果如下，打了2.5万并发VU
![配置vu值地址](../img/installation/dis_pressure/vu值.png){:height="100%" width="70%"} <br>
![配置vu1设置地址](../img/installation/dis_pressure/vu1.png){:height="100%" width="70%"} <br>

### 4 此方案已经在客户现场进行了部署测试，验证了MS在不同大规模场景下可通过水平扩展的方式，弹性支持压测池的调度。