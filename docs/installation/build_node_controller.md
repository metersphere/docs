如采用独立主机压测，需要部署 node-controller <br>
部署过程可以参考 https://metersphere.io/docs/installation/online_installation/ <br>
install.conf 中安装模式修改为 node-controller（环境变量文件需要指向同一个 kafka 和 ms-server 服务），注意资源池中 JMeter 的内存配置，建议调整到 4G 以上