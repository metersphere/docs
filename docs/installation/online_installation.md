---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---



## 1 环境要求
!!! ms-abstract "部署服务器要求"
    * 操作系统: Ubuntu 22 / CentOS 7 64 位系统
    * CPU/内存: 2C4G
    * 磁盘空间: 200 G
    * 网络要求：可稳定访问互联网
    * Docker：一键安装基于 Docker 环境，安装 Docker 可参考官方的 [安装文档](https://docs.docker.com/engine/install/) 进行操作。

## 2 一键安装
!!! ms-abstract ""

    ```
    docker run -d -p 8081:8081 --name=metersphere -v ~/.metersphere/data:/opt/metersphere/data metersphere/metersphere-ce-allinone
    ```

    安装成功后，通过浏览器访问如下页面登录 MeterSphere。<br>
    ```
    地址: http://目标服务器IP地址:8081
    用户名: admin
    密码: metersphere
    ```

    安装脚本默认将主机的 ~/.metersphere/data 目录作为挂载目录，MeterSphere 的配置文件、数据及日志等均存放在该安装目录。

## 3 配置反向代理

!!! ms-abstract ""
    如果使用了 Nginx、HAProxy 进行反向代理配置，需要增加对 websocket 的支持。以 Nginx 为例，参考配置如下:
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

            #配置 websocket 支持
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection "upgrade";
        }
    }
    ```