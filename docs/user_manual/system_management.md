## 首页
>系统设置主要是针对租户和测试资源的管理和配置，目前对于租户的角色设置有系统级角色 ：admin； 组织级角色 ：admin；工作空间级角色：测试经理，测试人员，只读用户
## 个人信息
>用户可以修改自己的用户名、邮箱、电话、密码等信息

![image-20200526151627711](../img/system_management/个人信息.png)

![image-20200526151627711](../img/system_management/修改个人信息.png)

> 用户在点击确定之后会去匹配旧密码正确与否

![image-20200526151627711](../img/system_management/修改个人密码.png)

### API Keys

![APIkey](../img/system_management/APIkey.png)

## 系统

### 用户

>当前系统中所有的用户，可以对用户进行新增，修改，查询，删除，状态更改操作

![image-20200526151627711](../img/system_management/系统用户首页.png)

-  删除用户，更改用户状态

>对用户进行状态和删除操作，可以点击Switch开关和删除按钮

- 查询用户

>可以根据名称单独查询用户

- 创建用户（最多可以给用户匹配5个角色）

![image-20200526151627711](../img/system_management/系统创建用户.png)


![image-20200526151627711](../img/system_management/系统下添加用户.png)

- 编辑用户信息

![image-20200526151627711](../img/system_management/系统修改用户.png)


- 修改用户密码

![image-20200526151627711](../img/system_management/系统修改用户密码.png)

### 组织

>当前系统中所有的组织，可以对组织以及组织下成员进行创建，编辑，查询，删除，更改操作

![image-20200526151627711](../img/system_management/系统组织首页.png)

- 删除组织

>选择要删除的组织，点击删除按钮

- 查询组织

>查询单个组织可以通过名称查询

- 创建组织

> 点击“创建组织”，录入组织名称和描述

![image-20200526151627711](../img/system_management/系统创建组织.png)

- 修改组织

> 点击修改按钮，修改对应组织

![image-20200526151627711](../img/system_management/系统修改组织.png)

- 组织下成员列表

![image-20200526151627711](../img/system_management/系统组织成员弹框.png)

>点击成员数量可以跳转到成员列表弹框，该页面可以实现对用户创建，移除，修改操作

- 删除成员

>选择要删除的成员，点击删除按钮

- 查询成员

>查询单个成员可以通过名称查询

- 添加成员

![image-20200526151627711](../img/system_management/系统组织添加成员.png)

- 修改成员

![image-20200526151627711](../img/system_management/系统组织修改成员.png)

### 工作空间

>当前系统中所有的工作空间，可以对工作空间以及工作空间下成员进行创建，编辑，删除，查询操作

![image-20200526151627711](../img/system_management/系统工作空间首页.png)

- 创建工作空间
>点击“创建工作空间”，录入工作空间名称，描述和所属组织
![image-20200526151627711](../img/system_management/系统创建工作空间.png)

- 修改工作空间

>点击编辑按钮，修改工作空间

![image-20200526151627711](../img/system_management/系统修改工作空间.png)


- 工作空间下成员列表

>点击成员数量可以跳转到成员列表弹框，该页面可以实现对成员创建，移除，修改操作【同组织下成员操作一致】

### 测试资源池

>当前系统下所有创建的资源池，可以对资源池进行新增，修改，删除，查询，启用禁用操作

![image-20200526151627711](../img/system_management/系统测试资源池首页.png)

- 删除资源池
>选择要删除的资源池，点击删除按钮

- 查询资源池
>查询单个资源池，可以通过名称查询

- 创建资源池
>点击"创建资源池"，录入资源池名称，描述，类型，根据类型不同录入相应所填项

![image-20200526151627711](../img/system_management/系统下创建资源池.png)

- 修改资源池
>选择要修改的资源池，点击修改按钮

![image-20200526151627711](../img/system_management/系统下修改资源池.png)



###  系统参数设置

#### 邮件设置

>可以对SMTP信息进行重新配置

![image-20200526151627711](../img/system_management/系统下邮件服务设置首页.png)

- 编辑SMTP信息

> 点击编辑按钮可以对SMTP信息进行修改，保存SMTP信息

![image-20200526151627711](../img/system_management/编辑smtp信息.png)

#### LDAP 设置

> 配置LDAP登录

![配置ldap](../img/system_management/配置ldap.png)

> 启用LDAP认证后，登录页会新增LDAP登录选项

![ldap登录](../img/system_management/ldap登录.png)

### 插件

#### Jenkins插件

> 下载地址：https://github.com/metersphere/jenkins-plugin
>
> 在构建步骤中添加MeterSphere插件

![jenkins-plugin](../img/system_management/jenkins-plugin.png)

> 配置好系统参数和待执行的用例

![Jenkins-config](../img/system_management/Jenkins-config.png)

## 组织

### 成员

>同系统下组织成员操作

### 工作空间

>同系统下工作空间操作

## 工作空间
### 成员

>同系统工作空间下成员操作

### 测试报告模版

>该页面可以对测试模版进行创建，修改，删除，查询操作

![image-20200526151627711](../img/system_management/测试报告模版首页.png)


- 查询测试报告模版

>查询单个测试报告模版，可以通过名称查询

![image-20200526151627711](../img/system_management/查询测试模版.png)


- 创建测试报告模版

> 点击"创建模版"进入模版编辑页面，左边是组件库，右边是测试报告内容，测试报告的模版可以通过拖拽左边的组件进行编辑

![image-20200526151627711](../img/system_management/工作空间下测试模版组件.png)

>拖拽左边自定义模块，可以自定义组件内容

![image-20200526151627711](../img/system_management/自定义组件.png)

- 保存测试模版

>输入测试模版名称-保存

- 编辑测试报告模版

>点击模版可以对现有模版进行编辑

![image-20200526151627711](../img/system_management/编辑测试模版.png)












































