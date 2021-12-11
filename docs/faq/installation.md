## 重启安装服务器后，如何启动 MeterSphere 相关组件？

MeterSphere 在安装过程中没有配置 docker 及其相关容器的自启动。当用户重新启动部署服务器之后，需要手动启动 docker 服务及 MeterSphere 相关容器。

```bash
service docker start
msctl start
msctl status
```

## 如何修改应用的默认端口？

修改 /opt/metersphere/.env 文件中的对应配置后，执行 `msctl reload` 命令重新加载应用。

> 配置文件说明请参考 [修改安装配置(可选)](/installation/offline_installation/#_4)

## 如何在 Kubernetes 中搭建 MeterSphere？

可以参照我们提供的 [helm chart](https://github.com/metersphere/helm-chart)

## 关于"Log4j2远程代码执行漏洞"的修复

由于 MeterSphere 使用到的 Kafka 及依赖的 JMeter 会受此漏洞的影响，在 Kafka 及 JMeter 发布解决该漏洞的版本前，用户可以手动在 docker compose 文件 (docker-compose-kafka.yml，docker-compose-node-controller.yml 及 docker-compose-server.yml) 里添加 `FORMAT_MASSAGES_PATTERN_DISABLE_LOOKUPS: 'true'` 环境变量规避此问题。

具体修改方式请参考该 [GitHub Commit](https://github.com/metersphere/installer/commit/36a60b09117d17735eeadc36af2dc9b5e67a54f7?diff=unified)，修改完成后执行 `msctl reload` 命令重建容器使环境变量生效。