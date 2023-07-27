---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

系统主要针对系统级别的管理配置功能。目前，MeterSphere 内置三级租户体系并可设置只读用户。平台默认用户组及用户组角色划分为：

!!! info "说明"
    【系统级用户组】：系统管理员；<br>
    【工作空间级用户组】：工作空间管理员、工作空间成员；<br>
    【项目级用户组】：项目管理员、项目成员、只读用户。

平台用户组支持用户在`用户组与权限`功能页面中自定义。

## 1 用户
点击左侧`系统`下拉菜单中的`用户`进入用户界面。右侧显示当前系统中的全部用户列表，可以对用户进行新增、修改、查询、删除、更改状态等操作。
![!用户管理](../../img/system_management/系统用户首页.png)

!!! info "说明"
     MeterSphere 部署成功后会自动创建一个系统管理员账户，用户名为admin，默认密码为metersphere。如将平台用于生产环境，请及时更改密码。

- 创建用户

点击`创建用户`按钮创建用户，在弹出页面中编辑用户信息。
![!创建用户](../../img/system_management/系统创建用户.png)

需要创建多个用户时，可点击`导入用户`按钮，下载模版并填写用户信息，通过 Excel 文件导入用户。
![!创建用户](../../img/system_management/系统导入用户.png)

- 为用户添加用户组

点击`添加用户组`按钮为用户添加用户组信息。新用户至少所属一个用户组，每个用户可以属于多个用户组。
![!设置用户角色](../../img/system_management/系统下添加用户组.png)

-  查询用户

用户列表右上方，使用搜索框，根据名称查询用户。
![针对用户的其他操作](../../img/system_management/查询用户.png)

-  针对用户的其他操作

在用户列表右侧操作列，可以点击`Switch`开关切换选定用户启用状态，点击`编辑`按钮修改用户密码，点击`删除`按钮删除该用户。
![针对用户的其他操作](../../img/system_management/针对用户的其他操作.png)

## 2 工作空间
点击左侧`系统`下拉菜单中的`工作空间`进入工作空间界面。右侧显示当前系统中的全部工作空间列表，可以对工作空间进行新增、修改、查询、删除等操作。
![!工作空间管理](../../img/system_management/系统工作空间首页.png)

- 创建工作空间

点击`创建工作空间`按钮创建工作空间，在弹出页面中填写名称和描述。
![!创建工作空间](../../img/system_management/创建工作空间.png)

- 编辑工作空间

点击`编辑`按钮编辑工作空间，在弹出页面中修改名称和描述。
![!编辑工作空间](../../img/system_management/编辑工作空间.png)

- 删除工作空间

点击`删除`按钮删除工作空间。
![!删除工作空间](../../img/system_management/删除工作空间.png)

## 3 用户组与权限
点击左侧`系统`下拉菜单中的`用户组与权限`进入用户组界面。用户可基于自身需求创建自定义用户组，并赋予用户组不同的权限设置。
![系统用户组首页](../../img/system_management/系统用户组首页3.png)

- 创建用户组

点击`创建用户组`按钮新建自定义用户组。在弹出的界面中编辑用户组名称及描述，选择用户组所属类型。使用`全局用户组`开关切换用户组适用状态。新建用户组类型为系统类型时自动切换为全局用户组，此开关为默认打开状态；新建用户组类型为其他类型时，全局状态可关闭，此时须为用户组选择所属工作空间。
![创建用户组](../../img/system_management/创建用户组.png)

- 为用户组配置权限

回到用户组列表中，点击`设置`按钮进入用户组权限设置页面，在该页面中基于用户组需求勾选操作权限，一个用户组即为一个权限集，点击`确定`按钮完成配置。
![为用户组配置权限](../../img/system_management/为用户组配置权限4.png)

- 编辑用户组信息

点击`编辑`按钮编辑选定用户组信息，在弹出页面中可以更改用户组名称及描述。
![编辑用户组信息](../../img/system_management/编辑用户组信息.png)

- 查询用户组

用户组列表右上方，使用搜索框，根据名称查询用户组。

- 删除用户组

用户组列表中，点击`删除`按钮删除选定用户组。

## 4 测试资源池管理

点击左侧`系统`下拉菜单中的`测试资源池`进入资源池界面。测试资源池主要用于接口测试及性能等测试。右侧资源池列表中，可以通过`Switch`开关切换资源池启用状态，点击`编辑`按钮更改资源池信息，点击`删除`按钮删除选定资源池。
![!测试资源池管理](../../img/system_management/系统测试资源池首页.png)

- 创建 Node 资源池

### 4.1 创建 Node 资源池
!!! info "注意"
    在服务器上安装 node-controller 服务后，再来配置 Node 资源池。

点击【创建资源池】按钮，在弹出的界面中为新建资源池编辑名称、描述等相关信息，【类型】选择【Node】，填写相应的配置信息，并支持设定资源池最大并发数量或最大线程数量。
![!创建资源池](../../img/system_management/系统下创建资源池.png)


### 4.2 创建 Kubernetes 资源池 (X-Pack)
!!! info "注意"
    在服务器上安装 k8s 服务后，再来配置 Kubernetes 资源池。

点击【创建资源池】按钮，在弹出的界面中为新建资源池编辑名称、描述等相关信息，【类型】选择【Kubernetes】，填写相应的配置信息，并支持设定资源池最大并发数量或最大线程数量。
![!创建K8S资源池](../../img/system_management/系统下创建K8S资源池.png)

4.2.1 获取 Master URL，输入 kubectl describe svc kubernetes 可获得 Endpoints 地址

4.2.2 获取 Token，需要有 k8s 集群环境，之后创建好 SA 和 token，命令如下
```
# 1 创建 namespaces
kubectl create namespace metersphere
# 2 创建 SA
kubectl create serviceaccount ms -n metersphere
# 3 创建 namespace 授权 SA
kubectl create clusterrolebinding ms --clusterrole=admin --serviceaccount=metersphere:ms -n metersphere
# 4 查询 SA token
kubectl describe sa/ms -n metersphere
kubectl describe secrets -n metersphere ms-token-xxxx
```
4.2.3 Namespace 可以进行自定义，在 k8s 集群上创建自定义的 Namespace
```
kubectl create ns ms-pool
```
4.2.4 下载 deployment.yaml 上传到 k8s 集群服务器上，输入命令使其生效后，输入命令查询自定义 Namespace 下的 ms-node-controller 是否正常起来
```
# 使 deployment.yaml 生效
kubectl apply -f deployment.yaml -n ms-pool
# 查询 ms-node-controller 服务
kubectl get all -n ms-pool
```
![!创建K8S资源池](../../img/system_management/下载yaml文件.png)

4.2.5 Deploy Name 使用默认的 ms-node-controller 就行，不需要更改。

4.2.6 配置完成后，点击确定即可。在资源池列表中有该资源池，在性能测试页面-压力配置处也可以看到该资源池。
![!创建K8S资源池](../../img/system_management/k8s资源池配置完成.png)

![!创建K8S资源池](../../img/system_management/k8s列表显示.png)

- 查询资源池

资源池列表右上方，使用搜索框，根据名称查询资源池。

- 删除资源池

资源池列表中，点击`删除`按钮删除选定资源池。

## 5 系统参数设置
点击左侧`系统`下拉菜单中的`系统参数设置`进入参数设置界面，用于平台基本配置、邮箱、LDAP、显示、认证、模块管理等参数的设置。
![系统参数设置首页](../../img/system_management/系统参数设置首页.png)

### 5.1 修改当前站点 URL
性能测试执行过程中 node-controller 节点需要通过配置的 `当前站点URL` 下载 JMX 等测试资源文件。在执行性能测试前需要配置并检查测试资源池中的节点可以正常访问到该 URL，URL 值一般为通过浏览器访问 MeterSphere 的地址。
![!当前站点URL](../../img/system_management/当前站点URL.png)

!!! info "选项"

     - 当前站点URL：当前 MeterSphere 站点地址，用于性能测试 JMeter 从 MeterSphere 站点获取压测脚本等数据。	  - Prometheus地址：Prometheus监控服地址。
     - 并发数：限制场景接口自动化中场景并行执行时的并发数量。

### 5.2 邮件设置
切换至`邮件设置`标签，点击`编辑`按钮可以对 SMTP 信息进行修改、保存。
![!编辑SMTP信息](../../img/system_management/编辑smtp信息.png)

### 5.3 LDAP 设置
切换至`LDAP`标签，点击`编辑`按钮配置 LDAP 登录相关参数。
![配置ldap](../../img/system_management/配置ldap.png)

!!! info "选项"
    * LDAP地址 ldap://serveurl:389 或 ldaps://serveurl:636
    * 绑定DN cn=administrator,cn=Users,dc=metersphere,dc=com
    * 用户OU ou=metersphere,dc=metersphere,dc=com
    * 用户过滤器 sAMAccountName={0}
    * LDAP属性映射 {"username":"sAMAccountName","name":"cn","email":"mail"}

!!! info "选项说明"
    * OU 同级多OU用｜分割
    * 用户过滤器 根据规则到 用户OU 里面去检索用户，可能的选项为 (uid={0}) 或 (sAMAccountName={0}) 或 (cn={0}) 
    * LDAP属性映射 {"username":"sAMAccountName","name":"cn","email":"mail","phone":"phone"}，username,name,email 三项不可修改删除, phone 属性可选
    * 启用LDAP认证 启用后登录页显示 LDAP登录选项

!!! warning "注意"
    用户过滤器用什么筛选, LDAP 属性映射字段要与其一致, 过滤器用 sAMAccountName, LDAP属性映射也要用 sAMAccountName
    
启用 LDAP 认证后，登录页会新增 LDAP 登录选项。

![ldap登录](../../img/system_management/ldap登录.png)

### 5.4 显示设置 (X-Pack)
切换至`显示设置`标签，点击`编辑`按钮配置系统的logo以及显示的文字和图片，填写完成后，点击`保存`即可。
![显示设置](../../img/system_management/显示设置.png)

### 5.5 认证设置 (X-Pack)
切换至`认证设置`标签，点击`编辑`按钮，修改 CAS、OIDC 单点登录协议认证信息，也可以点击`启用/禁用`按钮或者`删除`按钮。
![认证配置](../../img/system_management/认证配置.png)

### 5.6 模块管理 (X-Pack)
切换至`模块管理`标签，点击`启用/禁用`按钮，系统只显示`启用`的模块，`禁用`的模块不会在系统中出现。
![模块管理](../../img/system_management/模块管理.png)

## 6 配额管理 (X-Pack)
进入`配额管理`页面，可`编辑`上方的工作空间默认配额，编辑完成后，在配额列表中使用默认配置的，将同步更新编辑的数据。
![配额管理](../../img/system_management/配额管理.png)

![配额管理](../../img/system_management/配额管理_1.png)

点击工作空间的`编辑`按钮，可对单个工作空间进行配额管理设置
![配额管理](../../img/system_management/配额管理_2.png)

点击`删除`按钮，即可删除已配置好的内容，恢复到最初状态，使用默认配额的状态也由`是`变成`否`
![配额管理](../../img/system_management/配额管理_3.png)

## 7 授权管理
点击左侧`系统`下拉菜单中的`授权管理`进入授权管理界面，点击`授权验证`导入企业版证书，开启 X-Pack 功能。
![授权管理首页](../../img/system_management/授权管理首页.png)

## 8 操作日志
点击左侧`系统`下拉菜单中的`操作日志`进入日志界面，显示登录用户权限范围内的全部测试资源日志信息，并支持使用高级查询来快速查找相关日志。
![操作日志首页](../../img/system_management/操作日志首页.png)

## 9 插件管理
### 9.1 MeterSphere MQTT 插件设置 (X-Pack)
在 `系统设置`-`插件管理` 界面下，上传 MQTT 插件
![jenkins-plugin](../../img/system_management/插件管理1.png)

在 `接口测试`-`接口自动化` 界面下，新建一个场景，点击场景右下角 `+` 号，添加 MQTT 相关请求。
![jenkins-plugin](../../img/system_management/插件管理2.png)

![jenkins-plugin](../../img/system_management/插件管理3.png)

