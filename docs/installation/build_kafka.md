---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! info "大致流程:"
    * 先安装JDK
    * 部署Zookeeper集群
    * 部署Kafka集群
    * 部署Kafka-manager
    
## 1 部署Kafka集群

### 1.1 关闭防火墙和 selinux

关闭防火墙
```
systemctl stop firewalld.service
systemctl disable firewalld.service
```
关闭selinux
```
setenforce 0 （临时生效）
sed -i 's/^SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config（永久生效）
```

### 1.2 检查是否已经安装OpenJDK

```
rpm -qa|grep jdk  #如果安装先卸载jdk
```
下载jdk:
```
官网：https://www.oracle.com/java/technologies/javase-jdk8-downloads.html
```
选择jdk版本上传到服务器解压，这里我用的是jdk1.8.0版本
```
tar -xvf jdk-8u251-linux-x64.tar.gz
mv jdk1.8.0_251 /usr/local

vim  /etc/profile
 
export JAVA_HOME=/usr/local/jdk1.8.0_251
export CLASSPATH=$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin

source /etc/profile

java -version （检查一下jdk版本查看是否安装成功）
```

### 1.3 搭建Zookeeper集群

1.3.1 集群节点选用三台linux主机<br>

下载地址: https://archive.apache.org/dist/zookeeper/ <br>
或者: wget https://archive.apache.org/dist/zookeeper/zookeeper-3.5.5/apache-zookeeper-3.5.5-bin.tar.gz <br>

1.3.2 新建一个zookeeper-cluster目录，将安装包上传zookeeper-cluster目录下<br>
```
cd /usr/local
mkdir zookeeper-cluster
```

1.3.3 解压安装包
```
cd zookeeper-cluster
tar zxvf  apache-zookeeper-3.5.5-bin.tar.gz
```

1.3.4 配置zk1（先配一个节点，然后再复制修改相关配置）
```
1.修改解压包名称（直观区分）
mv apache-zookeeper-3.5.5-bin zk

2.新建data，logs 目录来存放数据和日志
cd zk
mkdir data logs 

3.进入conf，将zoo_sample.cfg复制重命名zoo.cfg
cd conf
cp zoo_sample.cfg zoo.cfg

4.修改conf下zoo.cfg
vi zoo.cfg
① 修改：dataDir=/usr/local/zookeeper-cluster/zk/data
② 添加：dataLogDir=/usr/local/zookeeper-cluster/zk/logs
③ clientPort=2181【clientPort是客户端的请求端口】
④ 在zoo.cfg文件末尾追加
server.1=10.1.240.150:2888:3888
server.2=10.1.240.151:2888:3888
server.3=10.1.240.152:2888:3888
5.在zk的data目录下创建一个myid文件，内容为1
cd ../data/
echo 1 > myid
```

1.3.5 其他节点配置
其他节点配置相同，除以下配置<br>
```
echo 1 >/usr/local/zookeeper-cluster/zk/data/myid # echo 中的值需要唯一，节点1，输出1，节点2，就写2.保证唯一
```

1.3.6 启动
```
cd /usr/local/zookeeper-cluster/zk/bin
./zkServer.sh start
```
![配置zk启动地址](../img/installation/dis_pressure/zk启动.png){:height="100%" width="70%"} <br>
查看集群状态
```
./zkServer.sh status
```
![配置zk状态地址](../img/installation/dis_pressure/zk状态.png){:height="100%" width="70%"} <br>
可以看到，一台作为leader，两台作为follower，zookeeper集群搭建成功。

### 1.4 Kafka集群安装

1.4.1 下载安装包 <br>

Kafka官网下载：http://kafka.apache.org/downloads <br>
或者wget，下载 https://mirrors.tuna.tsinghua.edu.cn/apache/kafka/2.6.2/kafka_2.12-2.6.2.tgz

1.4.2 新建一个Kafka-cluster目录，将安装Kafka-cluster目录下

```
cd /usr/local
mkdir kafka-cluster
```

1.4.3 解压安装包，重命名

```
tar zxvf kafka_2.12-2.6.2.tgz
mv kafka_2.12-2.6.2 kafka
```

1.4.4 修改配置文件

```
cd /usr/local/kafka-cluster/kafka/config/
vi server.properties修改
broker.id=1  #唯一
listeners=PLAINTEXT://172.16.150.154:9092  #修改为本机地址
log.dirs=/Data/kafka-logs #数据目录，kafka-logs会自动采集
zookeeper.connect=172.16.150.154:2181,172.16.150.155:2181,172.16.150.156:2181 #zokeeper集群地址，以","为分割其他的不用改
```

1.4.5 其他节点配置

其他节点配置相同，除以下内容：
```
broker.id=1  #唯一 （确定id值是唯一）
listeners=PLAINTEXT://172.16.150.154:9092  #修改为本机地址
```

1.4.6 启动

```
cd /usr/local/kafka-cluster/kafka/bin
./kafka-server-start.sh ../config/server.properties
可以发现在窗口启动之后是一个阻塞进程，会阻塞当前窗口，我们可以重新打开一个窗口进行接下来的操作，或者在启动kafka的时候使用 -daemon 参数将它声明为守护进程后台运行。
./kafka-server-start.sh  -daemon ../config/server.properties
```
到这一步kafka+zk已经是部署完成了

1.4.7 使用JMX监控Kafka

```
vim /usr/local/kafka-cluster/kafka/bin/kafka-server-start.sh
在这个字段加入export JMX_PORT="9999"
```
![配置监控kafka地址](../img/installation/dis_pressure/监控kafka.png){:height="100%" width="70%"} <br>

1.4.8 服务设置开机自启，使用systemctl工具管理（在配置时，请先把原本服务关闭）

```
先设置zookeeper开机启动
cd /lib/systemd/system/
vim zookeeper.service  在当中输入一下内容
[Unit]
Description=zookeeper
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
ExecStart=/usr/local/zookeeper-cluster/zk/bin/zkServer.sh start
ExecReload=/usr/local/zookeeper-cluster/zk/bin/zkServer.sh restart
ExecStop=/usr/local/zookeeper-cluster/zk/bin/zkServer.sh stop
[Install]
WantedBy=multi-user.target
```
然后保存退出

echo $PATH 找到我们的jdk安装路径

![配置jdk路径地址](../img/installation/dis_pressure/jdk路径.png){:height="100%" width="70%"} <br>
```
cd /usr/local/zookeeper-cluster/zk/bin
vim zkEnv.sh
```
![配置zk环境地址](../img/installation/dis_pressure/zk环境.png){:height="100%" width="70%"} <br>

找到我们第一行的变量，把我们之前部署的java环境添加刷新一下进去在后面插入<br>
export JAVA_HOME=/usr/local/jdk1.8.0_251，保存退出，然后刷新一下命令<br>
```
systemctl daemon-reload 
systemctl start zookeeper #启动服务
systemctl enable zookeeper #加入开机自启
systemctl status zookeeper #检查服务状态
```

状态如下就是正确

![配置zk状态正确地址](../img/installation/dis_pressure/zk状态正确.png){:height="100%" width="70%"} <br>

1.4.9 Kafka自启动设置

```
cd /lib/systemd/system/
vim kafka.service
添加一下内容：
[Unit]
Description=kafka
After=network.target  zookeeper.service

[Service]
Type=simple
Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/usr/local/jdk1.8.0_251/bin"
User=root
Group=root
ExecStart=/usr/local/kafka-cluster/kafka/bin/kafka-server-start.sh  /usr/local/kafka-cluster/kafka/config/server.properties
ExecStop=/usr/local/kafka-cluster/kafka/bin/kafka-server-stop.sh
PrivateTmp=on-failure
[Install]
WantedBy=multi-user.target
```
保存退出，刷新一下
```
systemctl daemon-reload
systemctl start kafka
systemctl enable kafka
systemctl status kafka
```
![配置kafka状态地址](../img/installation/dis_pressure/kafka状态.png){:height="100%" width="70%"} <br>

1.4.10 建议启动Kafka时先重新启动一下Zookeeper，有时间可能会起不来。启动Kafka前必须先要启动Zookeeper。

## 2 部署kafka-manager

可以在任意一台Kafka设备部署，Kafka可视化，yaml如下（需要提前安装好Docker环境和docker-compose环境，并下载好images）
```
version: '2'

services:

kafka-manager:
image: sheepkiller/kafka-manager:latest
restart: always
container_name: kafka-manager
hostname: kafka-manager
ports:
- 9000:9000
environment:
ZK_HOSTS: 10.1.240.154:2181,10.1.240.155:2181,10.1.240.156:2181  #修改为依据部署好的kafka集群
KM_ARGS: -Djava.net.preferIPv4Stack=true
networks:
- kafka-manager

networks:
kafka-manager:
```