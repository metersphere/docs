## 1 Python3 如何引用第三方依赖包？
!!! ms-abstract "注意"
    Python3 引用第三方依赖包有【挂载本地目录】 和【容器共享目录】两种方式，任选其中一种方式即可。

!!! ms-abstract "挂载本地目录"
    MeterSphere 里内嵌的 Python3 是 Python3.10，因此需要先在部署的环境里，先安装 Python3.10
    
    ```
    # 安装python3.10
    apt update && sudo apt upgrade -y
    apt install software-properties-common -y
    add-apt-repository ppa:deadsnakes/ppa
    apt install python3.10
    
    # 安装虚拟环境
    apt install -y python3.10-venv
    
    # 创建一个目录用于python虚拟环境
    mkdir /root/.venv
    cd /root/.venv
    python3 -m venv .
    source bin/activate
    
    # 安装三方包
    pip install requests
    pip install pinyin
    ```
    
    配置 task-runner 的目录挂载 /root/.venv/lib/python3.10/site-packages:/usr/local/lib/python3.10/sist-packages

    ![接口测试](../img/ask_question/api_question/task_runner_volumn.png){ width="900px" }
    
    配置完成后执行 msctl reload，服务启动后就可以在 Python3 脚本中直接使用三方包了

    ![接口测试](../img/ask_question/api_question/python3代码.png){ width="900px" }
    ```

!!! ms-abstract "容器共享目录"
    使用 Dockerfile 制作一个 python 容器

    ```
    FROM python:3.10-alpine
    
    RUN pip install requests pinyin
    
    VOLUME ["/usr/local/lib/python3.10/site-packages"]
    ```

    修改 docker-compose-task-runner.yml 文件
    ```
    version: "3"
    services:
      python:
        container_name: python
        image: python:3.10
        command: sh -c "tail -f /dev/null"  # 保持容器运行
    
      task-runner:
        image: ${MS_IMAGE_PREFIX}/metersphere-ce:${MS_IMAGE_TAG}
        container_name: task-runner
        deploy:
          resources:
            limits:
              memory: ${MS_RUNNER_MEM_LIMIT}
        entrypoint:
          - sh
          - -c
          - |
            sh /shells/task-runner.sh
        environment:
          TOTP_ENABLED: ${MS_TOTP_ENABLED}
          TOTP_SECRET: ${MS_TOTP_SECRET}
        ports:
          - ${MS_TASK_RUNNER_PORT}:8000
        healthcheck:
          test: [ "CMD", "nc", "-zv", "localhost", "8000" ]
          interval: 6s
          timeout: 5s
          retries: 50
        volumes:
          - ${MS_BASE}/metersphere/logs/task-runner:/opt/metersphere/logs/task-runner
        volumes_from:
          - python
        restart: always
        networks:
          - ms-network
    ```
