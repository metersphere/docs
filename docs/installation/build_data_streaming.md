!!! info "准备好环境变量文件、compose 文件，三台机器部署一样"

环境变量文件 .env
```
vim .env   #参考ms的.env文件进行修改

MS_KAFKA_TOPIC=JMETER_METRICS
MS_MYSQL_HOST=10.1.240.110 #修改MS的数据库
MS_KAFKA_LOG_TOPIC=JMETER_LOGS
MS_TAG=v1.9.3
MS_JMETER_DATA_PATH=metersphere/data/jmeter
MS_BASE=/opt
MS_KAFKA_TEST_TOPIC=LOAD_TESTS
MS_MYSQL_USER=root
MS_EXTERNAL_MYSQL=true
MS_PREFIX=registry.cn-qingdao.aliyuncs.com/metersphere
MS_MYSQL_DB=metersphere
MS_MYSQL_PASSWORD=Password123@mysql
MS_JMETER_TAG=5.4.1-ms3-jdk8
MS_MYSQL_PORT=3307

MS_KAFKA_BOOTSTRAP_SERVERS=10.1.240.154:9092,10.1.240.155:9092,10.1.240.156:9092  #新加
```

docker-compose-base.yml
```
vim docker-compose-base.yml #拷贝ms服务器的docker-compose-base.yml 

version: "2.1"
volumes:
ms-conf:
driver_opts:
type: none
device: ${MS_BASE}/metersphere/conf
o: bind
ms-logs:
driver_opts:
type: none
device: ${MS_BASE}/metersphere/logs
o: bind
ms-data:
driver_opts:
type: none
device: ${MS_BASE}/metersphere/data
o: bind

networks:
ms-network:
```

docker-compose-ds.yml
```
vim docker-compose-base.yml #拷贝ms服务器的docker-compose-base.yml 
vim docker-compose-ds.yml #新加ds yaml文件

version: "2.1"
services:

ms-data-streaming:
image: ${MS_PREFIX}/ms-data-streaming:${MS_TAG}
container_name: ms-data-streaming
environment:
HOST_HOSTNAME: $HOSTNAME
SPRING_DATASOURCE_URL: jdbc:mysql://${MS_MYSQL_HOST}:${MS_MYSQL_PORT}/${MS_MYSQL_DB}?autoReconnect=false&useUnicode=true&characterEncoding=UTF-8&characterSetResults=UTF-8&zeroDateTimeBehavior=convertToNull&useSSL=false
SPRING_DATASOURCE_USERNAME: ${MS_MYSQL_USER}
SPRING_DATASOURCE_PASSWORD: ${MS_MYSQL_PASSWORD}
KAFKA_PARTITIONS: 60  #此处修改kafka分区
KAFKA_REPLICAS: 1
KAFKA_TOPIC: ${MS_KAFKA_TOPIC}
KAFKA_LOG_TOPIC: ${MS_KAFKA_LOG_TOPIC}
KAFKA_TEST_TOPIC: ${MS_KAFKA_TEST_TOPIC}
KAFKA_BOOTSTRAP-SERVERS: ${MS_KAFKA_BOOTSTRAP_SERVERS} #此处修改为kafka集群
ports:
- 8084:8084
- 8085:8085
healthcheck:
test: ["CMD", "nc", "-zv", "localhost", "8084"]
interval: 6s
timeout: 10s
retries: 20
restart: on-failure
volumes:
- ./conf/metersphere.properties:/opt/metersphere/conf/metersphere.properties
- ${MS_BASE}/metersphere/logs/data-streaming:/opt/metersphere/logs/data-streaming
networks:
- ms-network
```

启动data-streaming，执行命令:
```
source .env 
docker-compose -f docker-compose-base.yml -f docker-compose-ds.yml up -d
```
