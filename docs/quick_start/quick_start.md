按部署服务器要求准备好部署环境后，可通过 MeterSphere 快速安装脚本一键快速部署。

!!! warning "注意"
    快速安装脚本所部署的环境仅适用于测试体验目的, 生产环境请参考本文档[「在线安装」](../installation/online_installation.md)章节内容进行部署。

## 1 部署服务器要求

!!! info "部署服务器要求"
     * 操作系统要求：任何支持 Docker 的 Linux x64
     * CPU内存要求：最低要求 4C8G，推荐 8C16G
     * 部署目录空间（默认/opt目录）要求： 50G
     * 网络要求：可访问互联网

## 2 网络端口要求

MeterSphere 作为一站式持续测试平台，其正常运行需要网络环境提供如下的网络端口配置要求，管理员可根据实际环境中 MeterSphere 组件部署的方案，在网络侧和主机侧开放相关端口：

| 组件     | 默认端口     | 说明     |
| -------- | -------- | -------- |
| GateWay | 8081 | API 网关项目，浏览器访问端口 |
| Node Controller | 8082 | 为接口或者性能测试提供独立节点类型的测试资源池 |
| Prometheus | 9090 | 收集压力机及被测系统的监控数据 |
| Node Exporter | 9100 | 用于采集 Node 的运行指标 |
| Selenium Grid | 4444 | 为 UI自动化测试提供运行环境,支持分布式拓展 |
| TCP Mock  | 10000-10010 | TCP Mock 对外提供服务需要开放的端口范围 |
| MySQL | 3307 | MeterSphere 默认安装的数据库对外提供的端口  |
| Redis | 6379 | MeterSphere 默认安装的 Redis 对外提供的端口  |
| Minio | 9000 | MeterSphere 默认安装的分布式对象存储对外提供的端口  |
| Kafka | 9092 | MeterSphere 默认安装的消息中间件对外提供的端口  |

## 3 安装步骤
以 root 用户 ssh 登录部署目标服务器, 执行以下命令。
```sh
curl -sSL https://github.com/metersphere/metersphere/releases/latest/download/quick_start.sh | sh
```
安装脚本默认使用 /opt/metersphere 目录作为安装目录，MeterSphere 的配置文件、数据及日志等均存放在该安装目录。

!!! warning "注意"
    如果需要使用 Nginx、Haproxy 等反向代理，需要配置反向代理对 websocket 的支持。以 Nginx 为例，参考的配置内容如下。
    ```
    server {
        listen 80;
        server_name demo.metersphere.com;
        server_tokens off;
        return 301 https://$host$request_uri;
    }
    server {
        listen 443 ssl;
        # RSA certificate
        ssl_certificate /etc/nginx/ssl/metersphere.com/fullchain.cer; # managed by Certbot
        ssl_certificate_key /etc/nginx/ssl/metersphere.com/metersphere.com.key; # managed by Certbot
        server_name  demo.metersphere.com;
        proxy_connect_timeout       300;
        proxy_send_timeout          300;
        proxy_read_timeout          300;
        send_timeout                300;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $remote_addr;
        proxy_set_header X-Forwarded-Host $server_name;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_redirect http:// $scheme://;
        
        location / {
            proxy_pass http://ip:8081;
            client_max_body_size 1000m;
            #access_log off;
            
            # 配置 websocket 支持
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection "upgrade";
        }
    }
    ```

## 4 登录并使用
### 4.1 登录
安装成功后，在浏览器打开以下地址页面，输入用户名和密码，登录 MeterSphere。
```
地址: http://目标服务器IP地址:8081
用户名: admin
密码: metersphere
```

### 4.2 界面说明
![界面说明](../img/界面说明.png)
