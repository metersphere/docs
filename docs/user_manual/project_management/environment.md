

!!! ms-abstract ""
    点击【项目管理-环境管理】进入项目环境管理页面。
![!项目环境页面](../../img/project_management/enviroment/项目环境页面.png){ width="900px" }

## 1 请求头
!!! ms-abstract ""
    配置【请求头】后，在整个项目中通用。
![!全局请求头](../../img/project_management/enviroment/全局请求头.png){ width="900px" }

!!! ms-abstract ""
    参数值使用【Mock】和【JMeter】函数，以【Mock】函数为例。
![!请求头自动生成](../../img/project_management/enviroment/请求头自动生成.png){ width="900px" }

!!! ms-abstract ""
    【批量添加】请求头。
![!批量添加请求头内容](../../img/project_management/enviroment/批量添加请求头内容.png){ width="900px" }

## 2 环境配置
!!! ms-abstract "操作说明"
    - 【复制】复制环境。
    - 【编辑】编辑环境域名、启用条件、请求头等内容。
    - 【删除】删除环境。
    - 【导入】导入环境，开启覆盖，环境名称重复则覆盖，不重复则新增；关闭覆盖，环境名称重复则不导入。
    - 【导出】导出当前选择的环境信息。

![!环境进行复制删除操作](../../img/project_management/enviroment/环境进行复制删除操作.png){ width="900px" }

![!导入导出环境](../../img/project_management/enviroment/导入导出环境.png){ width="900px" }

!!! ms-abstract "功能说明:"

    - **环境变量**：此处设置的变量是环境变量，可单个添加和批量添加。
    - **HTTP配置**：此处可配置环境地址以及启用条件，也可设置请求头。
    - **数据库**：配置数据库的数据源和连接信息。
    - **HOST**：设置 IP 和域名映射。
    - **前置**：分为【场景】和【请求】，【场景】是场景执行前执行一次，如 TOKEN 获取及场景初始化。【请求】是每一个 API 步骤执行前均执行一次，如请求内容加密。
    - **后置**：参考【前置】功能。
    - **断言**：参考接口 CASE 内的断言。
    - **显示设置**：显示环境配置内容，可进行【启用/关闭】。

### 2.1 环境变量
!!! ms-abstract ""
    【环境变量】进行单个添加和批量添加，可在请求体、前后置脚本里通过 `${变量名}` 方式进行引用。
![!环境变量](../../img/project_management/enviroment/环境变量.png){ width="900px" }

### 2.2 HTTP
!!! ms-abstract ""
    如下图，点击【+】填写环境名称，点击【添加 HTTP 】填写域名等信息后保存。
![!添加环境内容](../../img/project_management/enviroment/添加环境内容.png){ width="900px" }

!!! ms-abstract ""
    添加【HTTP】或【HTTPS】请求时，可通过不同的条件，例如模块、路径进行匹配。
![!环境变量](../../img/project_management/enviroment/http设置.png){ width="900px" }

!!! ms-abstract "环境启用条件规则:"

    - 匹配优先级按【路径】>【模块】>【无】顺序进行。
    - 当【路径】和【模块】都没有匹配上时，如配置了【无】的环境，使用【无】的环境，否则环境为空，执行失败。

!!! ms-abstract ""
    设置【连接超时】时间、【响应超时】时间，默认值为 60 秒。
![!设置超时时间](../../img/project_management/enviroment/设置超时时间.png){ width="900px" }

### 2.3 数据库
!!! ms-abstract ""
    添加【数据库】数据源操作，以 MySQL 数据库为例。
![!数据源链接成功](../../img/project_management/enviroment/数据源连接成功.png){ width="900px" }

!!! ms-abstract "数据源字段说明:"

    - **数据源名称**：自定义数据源名称。
    - **驱动**：默认内置 MySQL 驱动，其他驱动需要在【系统设置-系统-插件】上传驱动包，下拉选项中自动显示。具体参考：[插件管理](../../system_management/system/#71)。
    - **数据库连接 URL**：常用数据库连接 URL 如下<br>
        - **MySQL**：jdbc:mysql://127.0.0.1:3306/database，若需要支持执行多条 SQL 语句 ，则连接地址为 jdbc:mysql://127.0.0.1:3306/database?allowMultiQueries=true
        - **Oracle**：jdbc:oracle:thin:@192.168.2.1:1521:database，12C 版本数据库连接地址为 jdbc:oracle:thin:@192.168.2.1:1521/database
        - **SQLServer**：jdbc:sqlserver://127.0.0.1:1433;DatabaseName=database;encrypt=true;trustServerCertificate=true;
        - **PostgreSQL**：jdbc:postgresql://127.0.0.1:5432/database
    - **用户名**：数据库登录的用户名。
    - **密码**：数据库登录的密码。
    - **最大连接数**：数据库的最大连接数，默认显示 1。
    - **超时时间**：默认显示 1000。

### 2.4 HOST
!!! ms-abstract ""
    添加【HOST】，将环境中使用的域名和 IP 进行映射。
![!数据源链接成功](../../img/project_management/enviroment/host域名解析.png){ width="900px" }

### 2.5 前置/后置
!!! ms-abstract ""
    添加【场景】或【请求】的全局【前置】条件，支持【脚本操作】和【SQL操作】两种类型。以【场景-SQL操作】为例。
![!前置操作sql操作](../../img/project_management/enviroment/前置操作sql操作.png){ width="900px" }

!!! ms-abstract ""
    【后置】操作可参考【前置】操作。

### 2.6 断言
!!! ms-abstract ""
    【断言】设置有多种断言方式，详细断言可参考【接口 CASE】处的断言。以【响应体-JSONPath】为例。
![!显示设置](../../img/project_management/enviroment/断言.png){ width="900px" }

### 2.7 TCP 设置
!!! ms-abstract ""
    需要在【系统设置-系统-插件】处上传 TCP 的插件包，环境管理处才会显示【TCP配置】。
![!显示设置](../../img/project_management/enviroment/TCP配置.png){ width="900px" }

### 2.8 显示设置
!!! ms-abstract ""
    【显示设置】进行【启用/关闭】操作。
![!显示设置](../../img/project_management/enviroment/显示设置.png){ width="900px" }

[//]: # (## 2 环境组)

[//]: # (!!! ms-abstract "")

[//]: # (    场景中跨项目引用接口时，需要给每个项目的接口设置运行环境，此时可以配置环境组。<br>)

[//]: # (    点击【项目管理-环境管理-环境组】进入环境组页面，进行【新增】、【删除】操作。)

[//]: # (![!显示设置]&#40;../../img/project_management/enviroment/环境组功能.png&#41;{ width="900px" })


