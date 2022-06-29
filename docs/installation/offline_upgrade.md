
## 1 下载并解压安装包
按照本文档 [离线安装](./offline_installation.md) 步骤, 下载新版本安装包并上传解压后, 重新执行安装命令进行升级。

## 2 执行安装命令

```sh
# 进入离线部署包解压缩目录
cd metersphere-release-v1.x.y-offline

# 运行安装脚本
/bin/bash install.sh

# 查看 MeterSphere 状态
msctl status
```

!!! warning "注意"
    如果在旧版本安装过程中修改了安装目录(默认为 /opt 目录), 在执行升级脚本前需要修改 install.conf 文件中的安装目录为旧版本的安装目录。