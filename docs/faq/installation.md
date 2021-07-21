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

## docker-compose 版本与配置文件不兼容，请重新安装最新版本的 docker-compose?

把安装包里的docker-compose-xx 在 安装目录替换下

## 升级指定版本

msctl upgrade 后边跟版本号，如 msctl upgrade v1.10.6-lts

## 卸载命令

msctl uninstall -v 

## 重新安装命令

进入到安装包，然后重新执行 ./install.sh

## 卸载会导致数据清空么

卸载不会影响数据

## 升级报 /usr/local/bin/msctl: line 115 ....

cat /usr/local/bin/msctl 查看这个文件对应行数的代码，并进行相关处理

## 升级报 Schema `metersphere` contains a faied migration to version 86 !

到github源码上 https://github.com/metersphere/metersphere/tree/master/backend/src/main/resources/db/migration
查看对应version的flyway sql记录，和当前数据库比对，看具体哪行sql执行失败了，然后 重新执行下，然后修改metersphere_version
表对应版本的的success值为1，然后 msclt reload 重启服务即可

