## 重启安装服务器后，如何启动 MeterSphere 相关组件？

MeterSphere 在安装过程中没有配置 docker 及其相关容器的自启动。当用户重新启动部署服务器之后，需要手动启动 docker 服务及 MeterSphere 相关容器。

```bash
service docker start
msctl start
msctl status
```

## 如何修改应用的默认端口？

修改 /opt/metersphere/.env 文件中的对应配置后，执行 `msctl reload` 命令重新加载应用。

> 配置文件说明请参考 [修改安装配置(可选)](/installation/offline_installation/#_4)。

## 如何在 Kubernetes 中搭建 MeterSphere？

可以参照我们提供的 [helm chart](https://github.com/metersphere/helm-chart)。
详见在线文档/安装部署/Kubernetes中部署：https://metersphere.io/docs/installation/kubernetes_installation/

## docker-compose 版本与配置文件不兼容，请重新安装最新版本的 docker-compose?

把安装包里的docker-compose-xx 在 安装目录替换下。

## 升级指定版本

msctl upgrade 后边跟版本号，如 msctl upgrade v1.10.6-lts 。

## 卸载命令

msctl uninstall -v 

## 重新安装命令

进入到安装包，然后重新执行 ./install.sh 。

## 卸载会导致数据清空么？

卸载不会影响数据

## 升级报 `/usr/local/bin/msctl: line 115 ....`

cat /usr/local/bin/msctl 查看这个文件对应行数的代码，并进行相关处理。

## 升级报 `Schema ` metersphere `contains a faied migration to version 86 !`

到github源码上 https://github.com/metersphere/metersphere/tree/master/backend/src/main/resources/db/migration
查看对应version的flyway sql记录，和当前数据库比对，看具体哪行sql执行失败了，然后重新执行下，然后修改metersphere_version
表对应版本的的success值为1，然后 msclt reload 重启服务即可。

## 如何备份数据库?

```
docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere > metersphere.sql
```

## mysqldump: `Error 2020: Got packet bigger than 'max_allowed_packet' bytes when dumping table `api_scenario_report_detail` at row: 94`

```
添加max_allowed_packet参数，如下。
docker exec -i mysql mysqldump -uroot -pPassword123@mysql metersphere --max_allowed_packet=2G > metersphere.sql
```

## 关于"Log4j2远程代码执行漏洞"的修复

由于 MeterSphere 使用到的 Kafka 及依赖的 JMeter 会受此漏洞的影响，在 Kafka 及 JMeter 发布解决该漏洞的版本前，用户可以手动在 docker compose 文件 (docker-compose-kafka.yml，docker-compose-node-controller.yml 及 docker-compose-server.yml) 里添加 `FORMAT_MESSAGES_PATTERN_DISABLE_LOOKUPS: 'true'` 环境变量规避此问题。

具体修改方式请参考该 [GitHub Commit](https://github.com/metersphere/installer/commit/36a60b09117d17735eeadc36af2dc9b5e67a54f7?diff=unified)，修改完成后执行 `msctl reload` 命令重建容器使环境变量生效。

## 性能测试时并发量加大的时候报错Non HTTP response code: java.net.SocketTimeoutException

修改单个接口的连接超时时间。

## 数据库如何不区分大小写

chmod 655 /opt/metersphere/conf/my.cnf 

修改完成后，重启数据库。

## docker-compose 版本与配置文件不兼容，提示请重新安装最新版本的 docker-compose。

可以把安装包里的docker-compose-xx 在安装目录替换一下。

## 设置数据库忽略大小未生效，lower_case_table_names=1

```
chmod /opt/metersphere/conf/my.cnf 
然后重启数据库 docker restart mysql
```