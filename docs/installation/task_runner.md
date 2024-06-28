
## 1 服务端部署 Task Runner

!!! ms-abstract "部署服务器要求"

    * 操作系统：Ubuntu 22 / CentOS 7
    * CPU/内存：2C4G
    * 磁盘空间：50 G

!!! ms-abstract ""
    ```
    # 下载在线安装包并上传到服务器
    找到和 MeterSphere 主服务相同版本下载安装包，链接:  https://github.com/metersphere/metersphere/releases/
    
    # 解压安装包
    tar -zxvf metersphere-ce-online-installer-v3.x.y.tar.gz

    # 进入离线部署包解压缩目录
    cd metersphere-ce-online-installer-v3.x.y

    # 修改部署模式为 task-runner
    vi install.conf
    
    # 运行安装脚本
    /bin/bash install.sh
    
    # 查看 MeterSphere 状态，task-runner 状态为 healthy 即安装完成。
    msctl status
    ```
![配置主机3](../img/installation/dis_pressure/修改模式.png){ width="900px" }

![配置主机3](../img/installation/dis_pressure/status.png){ width="900px" }

!!! ms-abstract ""
     - **编辑资源池** <br>
     【系统设置-系统-资源池】点击编辑资源池，填写相应的 IP、Port 、最大并发数信息。
![配置主机3](../img/installation/dis_pressure/资源池添加.png){ width="900px" }

!!! ms-abstract "操作说明"
    - 内网URL：资源池部署在内网时，可走内网地址，如 http://MS服务器的内网IP:8081 。</br>
    - IP、Port：资源池部署服务器的 IP ，默认端口 8000 。
    - 最大并发数：社区版单个节点最大并发数为 10，如需更大并发数，可申请 [企业版试用](https://jinshuju.net/f/CzzAOe)
  
## 2 本地部署 Task Runner

!!! ms-abstract "说明"
    Task Runner 在其 Docker Hub 组织内提供自动更新的 Docker 镜像。可以始终使用最新的稳定标签来更新 Docker 镜像。</br>
    Docker 安装可参考 [官方文档](https://docs.docker.com/desktop/install/windows-install/)

### 2.1 Windows 环境

!!! ms-abstract "安装 WSL"
    参考 [在 Windows 10 上安装 WSL | Microsoft Docs](https://docs.microsoft.com/zh-cn/windows/wsl/install) 进行 Windows 宿主机 WSL 的安装和配置。  
    
    使用管理员身份运行以下命令，然后重启操作系统。
    ```
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    ```

    下载并安装 [适用于 x64 计算机的 WSL2 Linux 内核更新包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)

    以管理员身份执行以下命令，设置 WSL 默认版本：<br>
    ```
    wsl --set-default-version 2
    ```

!!! ms-abstract "安装 Ubuntu"
    在 Microsoft Store 里搜索 Ubuntu 进行安装。
 ![安装Ubuntu](../img/installation/dis_pressure/windows-install-ubuntu.png){ width="900px" }

!!! ms-abstract "检测 Ubuntu WSL 版本"
    以管理员身份执行 PowerShell
    ```
    wsl.exe -l -v
    ```
 ![WSL版本1](../img/installation/dis_pressure/check-version-1.png){ width="900px" }

!!! ms-abstract "检查 Ubuntu 是否安装完成"
    示例中安装的 Ubuntu Name 为 "Ubuntu"， 如像上图出现 Ubuntu 版本为 1， 则继续执行命令：
    ```
    wsl.exe --set-version Ubuntu 2
    ```

    出现以下内容即为成功。
    ```
    正在进行转换，这可能需要几分钟时间...
    有关与 WSL 2 的主要区别的信息，请访问 https://aka.ms.wsl2
    转换完成。
    ```

!!! ms-abstract "Docker 安装与配置"
    下载 [Docker Desktop for Windows](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe)，双击 Docker Desktop Installer.exe 完成docker 的安装。

    Docker Desktop 安装完成后，进入 Settings 界面，选择 Resources 菜单下的 WSL INTEGRATION，按下图设置后，点击右下角的 `Apply & Restart`。
![docker设置](../img/installation/dis_pressure/docker-settings.png){ width="900px" }

!!! ms-abstract "启动 Ubuntu"
    在应用商店里，选择 Ubuntu，点击"启动"按钮启动 Ubuntu，并执行 `sudo su` 命令切换到 root 用户。</br>
    
    在 Ubuntu 命令行中执行命令`docker version`，如能像下图一样正常显示 docker 版本信息，则能正常执行 MeterSphere 后续的安装操作，如出现异常，则需要根据提示信息解决。
![docker检测](../img/installation/dis_pressure/check-docker.png){ width="900px" }

!!! ms-abstract ""
  
    虚拟机安装完成后，执行以下步骤安装：

    ```
    # 下载在线安装包到 Windows 电脑 D 盘
     找到和 MeterSphere 主服务相同版本下载安装包，链接:  https://github.com/metersphere/metersphere/releases/
    
    # 解压安装包并进入目录修改安装模式为 task-runner
    MS_INSTALL_MODE=task-runner

    
    # 切换到 Ubuntu 终端运行安装脚本
    cd /mnt/d/metersphere-ce-online-installer-v3.X.y/metersphere-ce-online-installer-v3.x.y
    
    ./install.sh
    
    # 查看 MeterSphere 状态，task-runner 状态为 healthy 安装完成。
    msctl status
    ```
![配置主机3](../img/installation/dis_pressure/修改模式w.png){ width="900px" }

![配置主机3](../img/installation/dis_pressure/部署w.png){ width="900px" }

![配置主机3](../img/installation/dis_pressure/ww.png){ width="900px" }

!!! ms-abstract ""
    安装完成后，在【个人中心-本地执行】填写完整的访问 url：`http://localhost:8000` 。
![配置主机3](../img/installation/dis_pressure/本地.png){ width="900px" }

### 2.2 Mac 环境

!!! ms-abstract ""
    Mac 推荐使用 OrbStack 作为 Docker 的客户端，OrbStack 更加轻量化、快捷。</br>
    安装 OrbStack ，下载地址：https://orbstack.dev/download ,选择对应芯片架构的安装包下载、安装。

!!! ms-abstract "说明"
    安装成功并启动 OrbStack 后，在 Mac 终端中用 Docker 方式启动 Task Runner，命令如下：
    ```
    docker run -d -p 8000:8000 --name=task-runner registry.fit2cloud.com/metersphere/task-runner:v3.x.y
    ```

![配置主机3](../img/installation/dis_pressure/mac_install_1.png){ width="900px" }
    

!!! ms-abstract ""
    安装完成后，在【个人中心-本地执行】填写完整的访问 url：`http://localhost:8000` 。
![配置主机3](../img/installation/dis_pressure/本地.png){ width="900px" }