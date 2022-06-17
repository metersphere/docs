如采用独立主机压测，需要部署node-controller <br>
部署过程可以参考 https://metersphere.io/docs/installation/online_installation/ <br>
install.sh中安装模式修改为node-controller（环境变量文件需要指向同一个kafka和ms-server服务），注意资源池中jmeter的内存配置，建议调整到4g以上