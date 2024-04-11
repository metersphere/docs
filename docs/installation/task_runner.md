---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
    部署 Task-Runner，需要采用服务器独立部署。 部署服务器要求：

    * 操作系统: Ubuntu 22.04 / CentOS 7 64 位系统
    * CPU/内存: 4C8G 
    * 磁盘空间: 50 G

    

## 1 安装 Task_Runner
!!! ms-abstract ""

    ```
    # 下载在线安装包并上传到服务器
    找到和 MeterSphere 主服务相同版本下载安装包，链接:  https://github.com/metersphere/metersphere/releases/
    
    # 解压安装包
    tar -zxvf metersphere-ce-online-installer-v3.0.0-rc12.tar.gz

    # 进入离线部署包解压缩目录
    cd metersphere-ce-online-installer-v3.0.0-rc12

    # 修改部署模式为 ，改为 task-runner
    vi install.conf

    MS_INSTALL_MODE=task-runner

    
    # 运行安装脚本
    /bin/bash install.sh
    
    # 查看 MeterSphere 状态，task-runner 状态为healthy 安装完成。
    msctl status
    ```
![配置主机3](../img/installation/dis_pressure/修改模式.png){ width="900px" }


## 2 配置资源池

!!! ms-abstract ""
    社区版限制添加资源池节点，下列为企业版添加方式：

     - **编辑资源池**<br>

    【系统设置-系统-资源池】点击新建资源池，在弹出的界面中为资源池名称、描述、站点URL、应用组织、用途、类型、添加资源池方式等信息。
![配置主机3](../img/installation/dis_pressure/资源池添加.png){ width="900px" }


!!! ms-abstract "操作说明"
 
     - 【站点URL】: MeterSphere 服务真实 ip 地址。 如：http：//ip：8081 ，站点 URL 地址和 Node 资源池服务器要求网络互通。</br>
    - 【最大并发数】：单机部署 JMeter 最大支持 2000 并发 。</br>
    - 【IP、端口】Node 资源池部署服务器的真实 ip ，默认 8000 端口， Monitor 为监控 node_exporter 端口 9100。
  
## 3 配置本地执行

!!! ms-abstract ""
    本地执行具有多个优势：</br>

    - 实时反馈：在本地调试时，你可以立即看到代码的执行结果，这让你能够快速发现和解决问题。</br>
    - 快速迭代：本地调试允许你快速进行代码修改和测试，从而加快开发迭代的速度。</br>
    - 隔离环境：本地调试让你在一个受控的环境中进行开发和测试，不受外部环境的影响，有助于排除外部因素导致的问题。</br>
    </br>

    配置本地执行的 task-runner 参考步骤1，优先在安装本地执行的 task-runner。</br>
    windows 可以采用虚拟机部署 task-runner，mac 在终端安装 task-runner 。本地电脑安装的 task_runner 需要和 MeterSphere 主服务网络互通。</br>

    安装完成后，在 MeterSphere 【个人中心-本地执行】填写完整的访问url：http://部署 task-runner 服务器 ip:8000 。即可在接口测试开始使用本地调试 。点击跳转：[接口本地调试 ](../user_manual/api_test/debug.md)。
![配置主机3](../img/installation/dis_pressure/task.png){ width="900px" }

   