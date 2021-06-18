## 重启安装服务器后，如何启动 MeterSphere 相关组件？

MeterSphere 在安装过程中没有配置 docker 及其相关容器的自启动。当用户重新启动部署服务器之后，需要手动启动 docker 服务及 MeterSphere 相关容器。

```bash
service docker start
msctl start
msctl status
```

## 如何修改应用的默认端口？

修改 /opt/metersphere/.env 文件中的对应配置后，执行 `msctl reload` 命令重新加载应用。

> 配置文件说明请参考 [修改安装配置(可选)](/installation/online_installation/#_4)

## 压测执行的时候报错
Error: Check node-controller /etc/hosts, `127.0.0.1 ${hostname}` must be contained. Please delete the report and rerun.

在部署 node-controller 的机器上，使用hostname命令获取主机名
[root@nginx metersphere-release-v1.8.0]# hostname
nginx.novalocal
将获取到的主机名nginx.novalocal配置到 /etc/hosts 文件中，配置完成效果如下：
配置前
127.0.0.1       localhost
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.110.149.133 nginx111
配置后
127.0.0.1       localhost
127.0.0.1       nginx.novalocal
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.110.149.133 nginx111

## 性能测试时并发量加大的时候报错Non HTTP response code: java.net.SocketTimeoutException

修改单个接口的连接超时时间。

## 如何在k8s搭建ms

可以参照这里的helm模板：https://github.com/metersphere/helm-chart

## 数据库如何不区分大小写

chmod 644 /opt/metersphere/conf/my.cnf 

修改完成后，重启数据库。

