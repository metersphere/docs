如采用独立主机压测，需要部署 Node-Controller <br>
部署过程可以参考 https://metersphere.io/docs/v2.x/installation/online_installation/ <br>
在 install.conf 中修改安装模式 MS_INSTALL_MODE 的值(由原先的 allinone 改为 node-controller)，执行 install.sh 即可。
!!! info "注意："
    资源池中 JMeter 的内存配置，建议调整到 4G 以上