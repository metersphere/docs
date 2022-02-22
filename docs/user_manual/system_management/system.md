系统主要针对系统级别的管理配置功能。目前，MeterSphere 内置三级租户体系并可设置只读用户。平台默认用户组及用户组角色划分为：

    系统级用户组 ：系统管理员； 
    工作空间级用户组：工作空间管理员、工作空间成员；
    项目级用户组：项目管理员、项目成员、只读用户；

平台用户组支持用户在`用户组与权限`功能页面中自定义。

##用户

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

点击`添加用户组`按钮为用户添加用户组信息。新用户至少所属一个用户组，每个用户可以所属多个用户组。
![!设置用户角色](../../img/system_management/系统下添加用户组.png)

-  查询用户

用户列表右上方，使用搜索框，根据名称查询用户。

![针对用户的其他操作](../../img/system_management/查询用户.png)

-  针对用户的其他操作

在用户列表右侧操作列，可以点击`Switch`开关切换选定用户启用状态，点击`编辑`按钮修改用户密码，点击`删除`按钮删除该用户。

![针对用户的其他操作](../../img/system_management/针对用户的其他操作.png)

##工作空间
点击左侧`系统`下拉菜单中的`工作空间`进入工作空间界面。右侧显示当前系统中的全部工作空间列表，可以对工作空间进行新增、修改、查询、删除、等操作。
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

## 用户组与权限

点击左侧`系统`下拉菜单中的`用户组与权限`进入用户组界面。用户可基于自身需求创建自定义用户组，并赋予用户组不同的权限设置。

![系统用户组首页](../../img/system_management/系统用户组首页3.png)

- 创建用户组

点击`创建用户组`按钮新建自定义用户组。在弹出的界面中编辑用户组名称及描述，选择用户组所属类型。使用`全局用户组`开关切换用户组适用状态。新建用户组类型为系统类型时自动切换为全局用户组，此开关为默认打开状态；新建用户组类型为其他类型时，全局状态可关闭，此时须为用户组选择所属工作空间。

![创建用户组](../../img/system_management/创建用户组.png)

- 为用户组配置权限

回到用户组列表中，点击`设置`按钮进入用户组权限设置页面，在该页面中基于用户组需求勾选操作权限，一个用户组即为一个权限集，点击`确认`按钮完成配置。

![为用户组配置权限](../../img/system_management/为用户组配置权限4.png)

- 编辑用户组信息

点击`编辑`按钮编辑选定用户组信息，在弹出页面中可以更改用户组名称及描述。

![编辑用户组信息](../../img/system_management/编辑用户组信息.png)

- 查询用户组

用户组列表右上方，使用搜索框，根据名称查询用户组。

- 删除用户组

用户组列表中，点击`删除`按钮删除选定用户组。

## 测试资源池管理

点击左侧`系统`下拉菜单中的`测试资源池`进入资源池界面。测试资源池主要用于接口测试及性能等测试。右侧资源池列表中，可以通过`Switch`开关切换资源池启用状态，点击`编辑`按钮更改资源池信息，点击`删除`按钮删除选定资源池。
![!测试资源池管理](../../img/system_management/系统测试资源池首页.png)

- 创建资源池

点击`创建资源池`按钮，在弹出的界面中为新建资源池编辑名称、描述等相关信息。当前系统支持用户创建 Node 或 K8s类型的资源池，并支持设定资源池最大并发数量或最大线程数量。
![!创建资源池](../../img/system_management/系统下创建资源池.png)

!!! info "说明"
     Node 类型资源池须手动安装  JMeter 工具；K8s 类型资源池系统默认自动安装  JMeter 工具。

- 查询资源池

资源池列表右上方，使用搜索框，根据名称查询资源池。

- 删除资源池

资源池列表中，点击`删除`按钮删除选定资源池。

## 系统参数设置

点击左侧`系统`下拉菜单中的`系统参数设置`进入参数设置界面，用于平台基本配置、邮箱、LDAP、显示、认证、模块管理等参数的设置。

![系统参数设置首页](../../img/system_management/系统参数设置首页.png)

### 修改当前站点 URL

性能测试执行过程中 node-controller 节点需要通过配置的 `当前站点URL` 下载 JMX 等测试资源文件。在执行性能测试前需要配置并检查测试资源池中的节点可以正常访问到该 URL，URL 值一般为通过浏览器访问 MeterSphere 的地址。
![!当前站点URL](../../img/system_management/当前站点URL.png)

!!! info "选项"

     - 当前站点URL：当前 MeterSphere 站点地址，用于性能测试 Jmeter 从 MeterSphere 站点获取压测脚本等数据；	
     - Prometheus地址：Prometheus监控服地址；	 
     - 并发数：限制场景接口自动化中场景并行执行时的并发数量。

### 邮件设置

切换至`邮件设置`标签，点击`编辑`按钮可以对 SMTP 信息进行修改、保存。

![!编辑SMTP信息](../../img/system_management/编辑smtp信息.png)

### LDAP 设置

切换至`LADP`标签，点击`编辑`按钮配置 LDAP 登录相关参数。

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


## 授权管理

点击左侧`系统`下拉菜单中的`授权管理`进入授权管理界面，点击`授权验证`导入企业版证书，开启 X-Pack 功能。

![授权管理首页](../../img/system_management/授权管理首页.png)

## 操作日志

点击左侧`系统`下拉菜单中的`操作日志`进入日志界面，显示登录用户权限范围内的全部测试资源日志信息，并支持使用高级查询来快速查找相关日志。

![操作日志首页](../../img/system_management/操作日志首页.png)

## 插件管理

### Jenkins 插件设置

- 下载地址：https://github.com/metersphere/jenkins-plugin

在构建步骤中添加MeterSphere插件。
![jenkins-plugin](../../img/system_management/jenkins-plugin.png)

配置好系统参数和待执行的用例。

![Jenkins-config](../../img/system_management/Jenkins-config.png)


