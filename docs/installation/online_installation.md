## 仅需两步快速安装 MeterSphere

1. 准备一台不小于 8 G 内存且可以访问互联网的 64 位 Linux 主机；
2. 以 root 用户执行如下命令一键安装 MeterSphere。

```
curl -sSL https://github.com/metersphere/metersphere/releases/latest/download/quick_start.sh | sh
```

使用 Kubernetes 及 Helm 还可以通过 [Helm Chart](https://github.com/metersphere/helm-chart) 进行部署。

安装成功后，通过浏览器访问如下页面登录 MeterSphere

```
地址: http://目标服务器IP地址:8081
用户名: admin
密码: metersphere
```

