!!! warning "注意"
    升级前一定要进行数据备份，可参考 [MeterSphere 数据备份](./backup_data.md)。

如果您的服务器可以访问互联网, 可以通过以下命令直接升级 Metersphere 至最新版本。

## 1 一键升级至最新版本
```sh
# 升级至最新版本
msctl upgrade

# 查看 MeterSphere 状态
msctl status
```

## 2 一键升级至指定版本
```sh
# 升级至指定版本
msctl upgrade v1.20.x-lts

# 查看 MeterSphere 状态
msctl status
```

!!! info "注意"
    自 MeterSphere v1.3.0 起之后的版本才提供 upgrade 命令。

## 3 手动升级
GitHub release 链接: https://github.com/metersphere/metersphere/releases
```sh
# 下载在线安装包
wget https://github.com/metersphere/metersphere/releases/download/v1.x.y/metersphere-online-installer-v1.20.x-lts.tar.gz

# 解压在线安装包
tar -zxvf metersphere-online-installer-v1.20.x-lts.tar.gz

# 进入解压缩目录
cd metersphere-online-installer-v1.20.x-lts

# 执行install.sh安装脚本
/bin/bash install.sh
```
