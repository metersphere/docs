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

## 如何在 Kubernetes 中搭建 MeterSphere？
可以参照我们提供的 [helm chart](https://github.com/metersphere/helm-chart)

## 性能测试时并发量加大的时候报错Non HTTP response code: java.net.SocketTimeoutException

修改单个接口的连接超时时间。

## 如何在k8s搭建ms

可以参照这里的helm模板：https://github.com/metersphere/helm-chart

## 数据库如何不区分大小写

chmod 644 /opt/metersphere/conf/my.cnf 

修改完成后，重启数据库。

## docker-compose 版本与配置文件不兼容，提示请重新安装最新版本的 docker-compose

可以把安装包里的docker-compose-xx 在安装目录替换一下。

## 设置数据库忽略大小未生效，lower_case_table_names=1

chmod /opt/metersphere/conf/my.cnf 
然后重启数据库 docker restart mysql