---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

如采用独立主机压测，需要部署 node-controller <br>
部署过程可以参考 https://metersphere.io/docs/v1.20.x-lts/installation/online_installation/ <br>
在 install.conf 中修改安装模式 MS_INSTALL_MODE 的值(由原先的 allinone 改为 node-controller)，执行 install.sh 即可。
!!! info "注意："
    资源池中 JMeter 的内存配置，建议调整到 4G 以上