---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

## 1 是否支持/如何支持分布式的性能测试？
!!! ms-abstract ""
    MeterSphere 通过在测试资源池中添加多个测试执行节点的方式来支持分布式的性能测试。在我们向一个测试资源池中添加节点时，除了节点的 IP、端口信息外，还需要根据该节点的机器规格，配置该节点可以支持的最大并发数。当我们在执行性能测试的过程中选择了某个测试资源池时，MeterSphere 会将本次性能测试定义的并发用户数，按照所选测试资源池的节点支持的最大并发数进行按比例拆分，在测试开始执行后，每个测试执行节点会将测试结果、测试日志等信息输送到执行的 Kafka 队列中，MeterSphere 中的 data-streaming 组件会从 Kafka 中收集这些信息并进行汇总处理。

    例如当我们在系统中存在一个如下配置的测试资源池，并选择该测试资源池执行一个 10000 并发用户的性能测试时，node1 及 node2 将各分配 4000 个并发用户，node3 将分配 2000 个并发用户。

![测试资源池](../img/system_management/编辑测试资源池.png){ width="900px" }

## 2 如何向测试资源池中添加节点？
!!! ms-abstract ""
    首先需要在要添加的节点上部署 MeterSphere 的 node-controller 组件，安装方式参考本文档[「在线安装」](../installation/online_installation.md)或[「离线安装」](../installation/offline_installation.md)章节内容，在执行安装脚本前，修改 install.conf 文件中的 MS_INSTALL_MODE 字段的值为 node-controller 后执行安装脚本。安装完成通过 `msctl status` 查看组件状态是否正常。<br> 
        节点添加完成点击确定后系统将对节点状态进行检查，若测试资源池为可用状态则说明该测试资源池及其中的节点可以正常使用。

## 3 采用 MeterSphere 压测和手动使用 JMeter 命令行压测得到性能测试结果差距很大该如何优化？
!!! ms-abstract ""

    - 社区版 
    社区版默认采用后置监听的方式实时处理报告，即在 JMX 脚本文件中增加 Kafka BackendListener 配置，各个 NodeController 节点在本地启动 JMeter 容器执行该 JMX 脚本，过程中通过 Kafka BackendListener 将原始的 JTL 结果数据上传到指定的 Kafka Topic 中，DataStreaming 作为该 Kafka Topic 的消费者对各个节点的数据进行汇总，并计算性能测试报告中的各项指标。<br>
    因此在高并发时 Kafka 和 DataStreaming 很容易成为瓶颈，可以部署 Kafka 和 DataStreaming 集群以及增加 Partition 的数量来增加 Kafka 的吞吐量和处理能力。优化后正常可以达到2/3左右的差距。<br>
    - 企业版
    针对社区版 Kafka BackendListener 方式，需要上传和处理原始的 JTL 结果，过程中需要处理大量的数据，企业版中做了相关优化，即在执行测试过程中不再使用 BackendListener，各个 NodeController 启动 JMeter 容器时附带启动一个 Java 程序，该 Java 程序负责实时处理本地 JMeter 产生的 JTL 结果数据，生成性能测试报告中的各项指标后上传到指定的 Kafka Topic 中，DataStreaming 作为该 Kafka Topic 的消费者对各个节点的数据进行汇总。<br>
    与优化前方案相比，Kafka 和 DataStreaming 需要处理的数据大大降低，整体上对于并发量较大情况下的结果处理能力大大提升。
    同时可以采用 部署 Kafka 和 DataStreaming 集群以及增加 Partition 数量的来增加 Kafka 的吞吐量和处理能力，可更加接近 JMeter 的真实值。

## 4 执行性能测试时提示`Kafka 不可用，请检查配置`，如何解决？
!!! ms-abstract ""
    系统在执行性能测试之前，会先检查安装系统时配置的 Kafka 地址是否可用。当提示该信息时，表明 MeterSphere 无法正常连接到 Kafka，可以按照以下排查思路进行分析和定位：

<!--![Kafka 不可用排查](../img/kafka_invalid.png){ width="900px" }-->

!!! ms-abstract ""
    （1）检查 Kafka 是否正常运行
    如果在安装时使用的外部的 Kafka，请联系相关人员进行排查，检查 Kafka 服务是否正常；如果安装时使用 MeterSphere 默认配置进行安装，使用了自带的 Kafka 服务，请通过如下命令进行排查。
    ```bash
    # 检查各组件的运行状态
    msctl status
    # 若 Kafka 容器不处于 `healthy` 状态，查看 Kafka 日志进行进一步排查
    docker logs kafka
    ```
!!! ms-abstract ""
    （2）检查 MeterSphere 到 Kafka 服务的网络连接
    如果 Kafka 服务状态正常，请通过如下命令检查 ms-node-controller 容器是否能正常连接到 Kafka 服务。
    ```bash
    # 检查 ms-node-controller 是否能正常访问 Kafka 服务
    [root@meter-prototype ~]# docker exec ms-node-controller nc -zv ${kafka 服务 IP} ${kafka 服务端口}
    kafka (172.23.0.5:19092) open
    ```
    如果 ms-node-controller 不能正常访问 Kafka 服务，提示`host is unreachable`，执行 ifconfig 将 br-XXX 和 docker-XX 的网段，加入到防火墙策略中
    ```
    firewall-cmd --zone=trusted --add-source=172.18.0.1/16 --permanent；
    firewall-cmd --zone=trusted --add-source=172.19.0.1/16 --permanent；
    firewall-cmd --reload
    ```

!!! ms-abstract ""
    (3) 如果在安装时使用的外部的 Kafka，请联系相关人员进行排查，检查 MeterSphere 部署服务器到 Kafka 服务之间的网络连接是否正常，是否有防火墙、安全组等安全策略的影响；如果安装时使用 MeterSphere 默认配置进行安装，使用了自带的 Kafka 服务，请检查 MeterSphere 部署服务器上的防火墙配置，是否放通了 Kafka 的服务端口（默认 19092），也可以选择直接禁用防火墙后，重启 docker 服务和 MeterSphere 组件进行重试。
    ```bash
    # 以 CentOS 7 操作系统为例，禁用防火墙及重启服务命令
    systemctl stop firewalld
    systemctl restart docker
    msctl start
    ```
    若检查发现网络连接状态正常，在执行性能测试时仍旧提示该错误，请联系我们的团队进行进一步定位。

## 5 执行性能测试时提示 `无法运行测试，请检查当前站点配置` 如何解决？
!!! ms-abstract ""
    执行性能测试过程中，node-controller 节点需要通过 `系统`-`系统设置`-`系统参数设置` 中配置的 `当前站点 URL` 下载相关文件。出现该问题时用户需要检查该配置参数，确保 node-controller 节点可以正常访问到该 URL。 URL 地址一般为通过浏览器访问 MeterSphere 的地址，例如 `https://demo.metersphere.com`。

## 6 站点配置的 URL 是什么？
!!! ms-abstract ""
    站点配置为部署MeterSphere Sever的地址，可以是域名或者是IP地址。

## 7 执行性能测试时 JMeter 容器内存溢出如何解决?
!!! ms-abstract ""
    修改系统设置中所使用的测试资源池配置中的 HEAP 配置来调整 JMeter 容器的内存参数。
    ```
    -Xms2g -Xmx2g -XX:MaxMetaspaceSize=256m
    ```

## 8 如果性能测试jmx有依赖的jar包，需要怎么处理？
!!! ms-abstract ""
    在创建性能测试时，可以将依赖的 jar 包与 jmx 文件一起上传。

## 9 执行性能测试时，提示`并发数超额`，该怎么解决？
!!! ms-abstract ""
    修改系统设置-测试资源池中的最大并发数后再次执行测试。

## 10 执行性能测试时，显示`image not found`如何处理？
!!! ms-abstract ""
    执行性能测试所需的 JMeter 容器需要事先存在于所选的测试资源池的节点上，请检查确保容器镜像存在后，更新测试资源池的镜像配置为正确的镜像标签。


## 11 压测执行时报错：`Error: Check node-controller /etc/hosts, `127.0.0.1 ${hostname}` must be contained. Please delete the report and rerun.`
!!! ms-abstract ""
    在部署 node-controller 的机器上，使用hostname命令获取主机名。
    ```
    [root@nginx metersphere-release-v1.8.0]# hostname
    nginx.novalocal
    ```
    将获取到的主机名 `nginx.novalocal` 配置到 /etc/hosts 文件中，配置完成效果如下。
    配置前
    ```
    127.0.0.1       localhost
    ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
    10.110.149.133 nginx111
    ```
    配置后
    ```
    127.0.0.1       localhost
    127.0.0.1       nginx.novalocal
    ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
    10.110.149.133 nginx111
    ```

## 12 同一脚本执行多次，可以将多次的报告结果进行对比吗？
!!! ms-abstract ""
    在报告列表，同个任务下，已完成状态的报告可以进行对比。

![! 报告对比](../img/faq/报告对比.png){ width="900px" }

## 13 执行压测时，多台发压机的情况下，可以设置变量不重复执行吗？
!!! ms-abstract ""
    可以在性能测试的高级配置页面，使用CSV分割功能，系统会把变量平均分配给压力机，保证数值的唯一性。

## 14 MeterSphere可以监控被测系统服务器指标吗？
!!! ms-abstract ""
    MeterSphere 使用 Prometheus 进行发压机以及被测系统服务器的监控，可以在性能测试-高级配置里面，添加被测系统服务器的 node_exporter 的地址。主服务会在安装 MeterSphere 系统时默认安装，而其他服务器，则需要单独安装 node_exporter，即可在执行性能测试的时候完成相关指标的监控。

## 15 如何安装 node_exporter 插件？
!!! ms-abstract ""

    - 方法1： docker pull prom/node-exporter 拉取 node_export 镜像，之后运行容器
    ```
    docker pull prom/node-exporter # 拉取镜像
    docker run -d -p 9100:9100 -v "/proc:/host/proc:ro" -v "/sys:/host/sys:ro" -v "/:/rootfs:ro" --net="host" prom/node-exporter # 启动容器
    
    http://服务器IP:9100/metrics # 访问查看 node_export 是否正常启动
    ```

    - 方法2：下载 node_exporter 离线包，解压之后可执行命令进行启动
    ```
    wget https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz
    tar -zxvf node_exporter-1.3.1.linux-amd64.tar.gz
    cd node_exporter-1.3.1-amd64
    ./node_exporter  # 启动 (nohup ./node_exporter & 后台启动)
    
    http://服务器IP:9100/metrics # 访问查看 node_export 是否正常启动
    ```

## 16 压力配置中，每个线程组是否能分别选择压力机？
!!! ms-abstract ""
    在压力配置里，提供了3种分配策略，分别为“自动分配、固定节点、自定义”，可以为每个线程组指定一个节点，或者按比例分配多个节点。

## 17 性能测试并发量加大的时候报错：`Non HTTP response code: java.net.SocketTimeoutException`
!!! ms-abstract ""
    在高级配置增加超时时间。

![! 性能测试-设置超时时间](../img/faq/性能测试-设置超时时间.png){ width="900px" }

## 18 进行压测时，最大用户加到 50/100 就不能继续加吗？
!!! ms-abstract ""
    可在系统设置-测试资源池-修改资源池里“最大并发数”中配置。

## 19 性能测试相关文件存储在 JMeter 容器中的哪个目录？
!!! ms-abstract ""
    在容器里的/test目录下。

## 20 性能测试状态一直是 starting 且无数据，如何排查？
!!! ms-abstract ""

    - 检查【系统设置-系统-系统参数设置】，当前站点配置是不是正确的 <br>
    - 到服务器或者压力机的查看 /opt/metersphere/logs/node-controler/ 下的 ms-jmeter-run-log.log 和 info.log，看日志中是否有报错信息。<br>

## 21 k8s资源池是否需要安装 node-controller ？
!!! ms-abstract ""

    - 执行性能测试不需要<br>
    性能测试只需要在仓库中配置好 JMeter 镜像的地址，执行性能测试的时候会自动创建 JMeter POD 进行压测，执行完之后自动销毁。<br>
    - 执行接口测试需要<br>
    执行接口测试需要部署 DaemonSet 或 Deployment，可下载示例 yaml 文件进行部署，部署好之后可以设置弹性伸缩参数，从而实现资源池的弹性伸缩。<br>
![! 接口测试-K8S配置](../img/faq/接口测试-K8S配置.png){ width="900px" }

## 22 操作时提示：`check node-controller status`
!!! ms-abstract ""
    - 检查【系统设置-系统参数设置-当前站点URL】是否正确，是不是多了"/" <br>
    - docker exec -it performance-test nc zv  ms-node-controller 8082 或者去 performance-test 容器里  curl localhost:8082/status 确保网络通畅，还可重启docker、重启服务器试试 <br>
    - 检查 JMeter 的镜像版本是不是对的，检查 JMeter 镜像有没有加载到 docker 中，执行docker load -i jmeter-master.tar，看能否加载到docker中，若不能则重新上传JMeter镜像，执行docker load -i jmeter-master.tar，修改.env环境里的JMeter镜像，重新加载项目msctl reload。<br>

## 23 操作提示：`Error:没有足够的资源启动测试`
!!! ms-abstract ""
    将【系统设置-测试资源池-JMeter HEAP】调大。

![! 接口测试-K8S配置](../img/faq/Jmeter_Heap.jpg){ width="900px" }

## 24 性能测试中怎么跨线程传递变量？
!!! ms-abstract ""
    性能测试里动态设置变量可以用属性的方式，${__setProperty(var,value,)} 设置属性，${__property(var)} 引用属性。用属性方法在性能测试中可以动态传递并且可以跨线程传递

## 25 性能测试无法正常执行，提示资源不够？
!!! ms-abstract ""
    可能的原因有: 

    - 性能测试里有添加前后置脚本，尤其是python，消耗性能比较大。
    - 测试资源池主机资源（尤其是内存）不足。

    解决方法: 

    - 尽量不要使用前后置脚本，或者换用资源消耗小的脚本，如 groovy。
    - 换用单独的测试资源池，使用 node-controller 模式安装。

## 26 性能测试报告中，并发用户数显示和设置不一致
!!! ms-abstract ""
    可能的原因有: 
    
    - 并发用户数太少，ramp-up设置的时间长，导致加压后第一个用户已经执行完测试了，第二个用户才创建出来，看起来并发用户数就一直是1。
    - 报告左上角的并发用户数在报告里显示的是平均值，不是实时变化的。

    解决方法：减少ramp-up时间，可以看到并发用户数与设置一致。

## 27 如何修改 kafka 的日志保留时间？
!!! ms-abstract ""
    修改 /opt/metersphere/docker-compose-kafka.yml 配置文档里的 KAFKA_CFG_LOG_RETENTION_HOURS 参数。

![!kafka](../img/faq/kafka_log.png){ width="900px" }

## 28 性能测试时接口读取 csv 不能按顺序读取
!!! ms-abstract ""
    所选的测试资源池有多个节点，多个节点共用一套 CSV 导致取值重复，在性能测试的高级配置里，开启 CSV 分割，多准备点测试数据。CSV 分割是: 假设有2个节点，CSV 里有100条数据，就会把 CSV 里的数据均分成2份，然后节点1 使用 1-50 条数据，节点2 使用 51-100 条数据。

## 29 性能测试配置里面上传 CSV 文件，在高级配置里面看不到
!!! ms-abstract ""
    csv 文件没有被性能 jmx 脚本引用，jmx 引用了才能看见。修改 jmx 文件，引用上传的 CSV 文件，或者在场景里添加 CSV 文件后转性能测试。

## 30 性能测试模块，自定义监控项不支持 windows 服务器
!!! ms-abstract ""
    默认提供的 promQL 是与 linux 操作系统适配，windows 操作系统的监控项需要自行编写，例如：查询 windows 的 cpu 使用率: `100 - (avg by (instance) (irate(windows_cpu_time_total{mode="idle", instance="%1$s"}[1m])) * 100) `

    其中 %1$s 是被监控节点的ip和端口，上面这条语句在执行时会变成 100 - (avg by (instance) (irate(windows_cpu_time_total{mode="idle", instance="172.16.10.54:9182"}[1m])) * 100)
    其他监控项可以自行查询来写，内存、磁盘等，还可以自行监控不同的 exporter，只要是符合 exporter规范的都可以在自定义监控中配置

## 31 部署在 K8S 下的 MS 自定义监控配置方法，默认方法无法生效，并且监控详情没有数据 
!!! ms-abstract ""
    在 prometheus.yml 中配置
    ```
    consul_sd_configs:
    - server: 'k8s中ms的ip:port'
    services: []
    ```
    自定义监控中加上需要的节点，系统参数测试中设置 prometheus 的实际地址，执行测试可以显示监控。

![!kafka](../img/faq/k8s_监控.png){ width="900px" }

## 32 接口自动化创建的性能测试，脚本及文件内容更新后，已转性能测试的用例没有同步更新 
!!! ms-abstract ""
    转性能测试的时候生成的 jmx 文件就是当前的配置，之后再修改接口对性能测试无效，点击性能测试右上角“同步场景测试最新变更”按钮手动同步即可。

## 33 运行性能测试的时候报错`Image Not Found: registry.cn-qingdao.aliyuncs.com/metersphere/jmeter-master:5.4.3-ms5-jdk11`

!!! ms-abstract ""
    服务器本地的 jmeter-master 镜像被删除了，需要手动执行命令手动拉取镜像 `docker pull registry.cn-qingdao.aliyuncs.com/metersphere/jmeter-master:5.4.3-ms5-jdk11`。

## 34 如果采用 K8S 集群压测，如何获取 SA 和 Token？
!!! ms-abstract ""
    ```
    // 创建 namespaces
    kubectl create namespace metersphere
    
    // 创建 SA
    kubectl create serviceaccount ms -n metersphere
    
    // 创建 namespace 授权 SA
    kubectl create clusterrolebinding ms --clusterrole=admin --serviceaccount=metersphere:ms -n metersphere
    
    // 查询 SA token
    kubectl describe sa/ms -n metersphere
    kubectl describe secrets -n metersphere ms-token-xxxx
    ```
