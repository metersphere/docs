## 1 一键部署
!!! ms-abstract ""
    按部署服务器要求准备好部署环境后，可通过 MeterSphere 快速安装脚本一键快速部署。<br>
    一键安装采用默认安装参数，更多有关离线部署、容器部署等方式可查看【**安装部署**】章节内容。<br>

    **部署服务器要求**：<br>

     - 操作系统要求：任何支持 Docker 的 Linux x64
     - CPU内存要求：最低要求 4C8G，推荐 8C16G
     - 部署目录空间（默认/opt目录）要求： 50G
     - 网络要求：可访问互联网


    以 root 用户 ssh 登录部署目标服务器, 执行以下脚本进行一键安装:<br>
    ```sh
    curl -sSL https://resource.fit2cloud.com/metersphere/metersphere/releases/latest/download/quick_start.sh | bash
    ```

    安装成功后，客户端通过浏览器访问以下地址，输入用户名和密码，即可开始使用 MeterSphere。
    ```
    地址: http://目标服务器IP地址:8081
    默认用户名: admin
    默认密码: metersphere
    ```

## 2 界面说明
!!! ms-abstract ""
    进入 MeterSphere 主界面后可以看到界面左边是导航栏，包括【工作台】【测试跟踪】【接口测试】【UI 测试】【性能测试】【报表统计】【项目设置】【系统设置】八个模块，其中 UI 测试是企业版本 X-Pack的功能，界面上方以 Tab 页方式展示当前模块的具体功能。

![界面说明](../img/界面说明.png)
