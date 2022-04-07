
如果您的服务器可以访问互联网, 可以通过以下命令直接升级 metersphere 至最新版本

## 一键升级至最新版本
```sh
# 升级至最新版本
msctl upgrade
# 查看 MeterSphere 状态
msctl status
```
!!! info "注意"
    自 MeterSphere v1.3.0 起之后的版本才提供 upgrade 命令 

## 一键升级至指定版本
```sh
# 升级至指定版本
msctl upgrade v1.x.y
# 查看 MeterSphere 状态
msctl status
```
## 手动升级
GitHub release 链接: https://github.com/metersphere/metersphere/releases
```sh
# 下载在线安装包
wget https://github.com/metersphere/metersphere/releases/download/v1.x.y/metersphere-online-installer-v1.x.y.tar.gz
# 解压在线安装包
tar -zxvf metersphere-online-installer-v1.x.y.tar.gz

cd metersphere-online-installer-v1.x.y

# 执行install.sh安装脚本
/bin/bash install.sh
```
