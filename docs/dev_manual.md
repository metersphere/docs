## 项目结构

```
.
├── Dockerfile                                      # 构建容器镜像使用的 dockerfile
├── LICENSE
├── README.md
├── ROADMAP.md
├── backend                                         # 后端项目主目录
│   ├── backend.iml
│   ├── pom.xml                                     # 后端 maven 项目使用的 pom 文件
│   └── src                                         # 后端代码目录
├── frontend                                        # 前端项目主目录
│   ├── babel.config.js
│   ├── frontend.iml
│   ├── node
│   ├── node_modules
│   ├── package-lock.json
│   ├── package.json
│   ├── pom.xml                                     # 前端 maven 项目使用的 pom 文件
│   ├── public
│   └── src                                         # 前端代码目录
├── metersphere-server.iml
└── pom.xml                                         # 整体 maven 项目使用的 pom 文件
```

## 配置开发环境

### 后端
MeterSphere 后端使用了 Java 语言的 Spring Boot 框架，并使用 Maven 作为项目管理工具。开发者需要先在开发环境中安装 JDK 1.8 及 Maven。

后端项目中依赖了该 Github 项目 https://github.com/fit2cloud/quartz-spring-boot-starter/packages/300609 ，开发者可按照 Github Maven 仓库的[使用指导](https://help.github.com/articles/configuring-apache-maven-for-use-with-github-package-registry/)添加 Maven 仓库地址，自动下载该依赖包。

#### 初始化配置

#### 运行后端服务

mvn spring-boot:run

### 前端
MeterSphere 前端使用了 

#### 初始化配置

#### 运行前端服务
