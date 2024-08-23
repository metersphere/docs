

## 1 新建接口
!!! ms-abstract "" 
    点击【新建】或者【＋】新建接口请求。
![!新建接口](../../img/api_test/definition/新建请求1.png){ width="900px" }

!!! ms-abstract "" 
    依次输入接口请求方法类型、URL 地址，接口名称、所属模块、状态等基础信息，响应体、响应头、响应码等响应内容信息。
![!新建接口](../../img/api_test/definition/新建请求2.png){ width="900px" }

!!! ms-abstract "说明" 
    - 参数介绍：请求头、请求体、Query、REST。详情参考：[参数介绍](../api_test/request_params.md)。
	- 内置函数：请求体参数可选择内置 Mock 函数。详情参考：[内置函数](../api_test/functions.md)。

!!! ms-abstract "" 
    点击【+】新建响应内容，点击【...】复制、重命名、设为默认、删除响应信息。
![!新建接口](../../img/api_test/definition/新建请求3.png){ width="900px" }


## 2 导入接口
### 2.1 文件导入
!!! ms-abstract "" 
    按照序号顺序，点击【导入接口】，选择导入模块、导入模式、上传文件后，点击导入。
![!文件导入](../../img/api_test/definition/文件导入.png){ width="900px" }	

!!! ms-abstract "导入模式说明" 
    - **覆盖：** 
        - **系统已存在的同一接口（请求类型+路径一致）**：请求参数内容一致不做变更，请求参数内容不一致则覆盖系统原接口。
        - **系统不存在的接口**：新增。
	- **不覆盖：**
        - **系统已存在的同一接口（请求类型+路径一致）**：不做变更。
        - **系统不存在的接口**：新增。

!!! ms-abstract "更多设置" 
	- 同步更新接口所在目录：在【覆盖模式】下，可选是否更新接口所在的目录。

### 2.2 SwaggerURL 导入
!!! ms-abstract "" 
    按照序号顺序，点击【导入接口】，选择导入模块、导入模式、更多设置、Swagger 的 JSON URL 地址、Basic Auth 认证，点击导入。
![!SwaggerURL导入](../../img/api_test/definition/SwaggerURL导入.png){ width="900px" }	

!!! ms-abstract "注意" 
    支持 Swagger 3.0 版本的 json 文件，2.0 的文件建议自行在 [Swagger 官网](https://converter.swagger.io/) 转换成 3.0 再进行导入，大小不超过 50M。

### 2.3 定时导入
!!! ms-abstract "" 
    按照序号顺序，点击【定时导入】，输入任务名称、Swagger 的 JSON URL 地址、所属模块、导入模式、同步频率，点击导入。
![!定时导入](../../img/api_test/definition/定时导入.png){ width="900px" }	

!!! ms-abstract "" 
    点击上图【定时任务列表】可快速查看定时导入 API 的任务列表。
![!定时导入](../../img/api_test/definition/定时导入1.png){ width="900px" }	

!!! ms-abstract "" 
    在 [任务中心](../general.md#62) 处也可以查看定时导入 API 的任务列表。

### 2.4 IDEA 插件导入
!!! ms-abstract ""
    在 IDEA 工具安装插件，即可推送接口到平台，详细参考 [接口推送](https://kb.fit2cloud.com/?p=08e64011-725f-4546-86e0-8d1f88c72926) 。

## 3 API 预览
### 3.1 详情
!!! ms-abstract "" 
    点击【ID】查看接口详细信息，可关注、分享接口详情。
![!详情](../../img/api_test/definition/详情1.png){ width="900px" }	

![!详情](../../img/api_test/definition/详情2.png){ width="900px" }	

### 3.2 引用关系
!!! ms-abstract "" 
    查看引用该接口的场景。
![!引用关系](../../img/api_test/definition/引用关系.png){ width="900px" }

### 3.3 变更历史
![!引用关系](../../img/api_test/definition/变更历史.png){ width="900px" }	

## 4 调试
!!! ms-abstract ""
    切换到【调试】页面，输入参数信息、前后置操作、内置函数或者认证信息，选择环境，选择【服务端执行】或者【本地执行】，执行成功后在执行结果处查看响应体、响应头、实际请求、控制台、提取、断言等信息。<br>
![!执行](../../img/api_test/definition/调试.png){ width="900px" }	

!!! ms-abstract "说明" 
    - 参数介绍：请求头、请求体、Query、REST。详情参考：[参数介绍](../api_test/request_params.md)。	
    - 内置函数：请求体参数可选择内置 Mock 函数。详情参考：[内置函数](../api_test/functions.md)。

!!! ms-abstract "" 
    调试成功后，点击【保存为新用例】直接保存成用例。
![!保存为新用例](../../img/api_test/definition/保存为新用例.png){ width="900px" }	

## 5 创建用例
!!! ms-abstract "" 
    切换到【用例】页面，点击【创建用例】。
![!创建用例](../../img/api_test/definition/创建用例1.png){ width="900px" }		

!!! ms-abstract "" 
    依次输入用例名称，用例等级、状态、标签、请求参数信息，选择环境。点击执行，执行成功后，点击【创建】或【保存并继续创建】。
![!创建用例](../../img/api_test/definition/创建用例2.png){ width="900px" }	

## 6 CASE 预览
### 6.1 详情
!!! ms-abstract "" 
    点击【ID】查看用例详细信息。
![!详情](../../img/api_test/definition/用例详情1.png){ width="900px" }	

![!详情](../../img/api_test/definition/用例详情2.png){ width="900px" }

### 6.2 同步更新
!!! ms-abstract ""
    API 的请求头、请求体、Query、REST 等内容发生变更，修改后点击【保存】
![!引用关系](../../img/api_test/definition/api更新.png){ width="900px" }

!!! ms-abstract ""
    切到【用例】页面，该 case 右侧会有同步变更提示
![!引用关系](../../img/api_test/definition/case提示.png){ width="900px" }

!!! ms-abstract ""
    进入【接口与用例差异对比】页面看到具体变更内容，点击【同步】后，跳转到【用例更新】页面，点击【更新】即可同步更新成功。
![!引用关系](../../img/api_test/definition/case变更内容页面.png){ width="900px" }

![!引用关系](../../img/api_test/definition/case用例进行更新.png){ width="900px" }

![!引用关系](../../img/api_test/definition/case更新成功.png){ width="900px" }

### 6.3 引用关系
!!! ms-abstract "" 
    查看引用该用例的场景。
![!引用关系](../../img/api_test/definition/用例引用关系.png){ width="900px" }

### 6.4 执行历史
!!! ms-abstract "" 
    查看该用例的执行历史，在执行历史列表操作列点击【执行结果】查看执行结果详情。
![!执行历史](../../img/api_test/definition/用例执行历史1.png){ width="900px" }

!!! ms-abstract "" 
    点击【报告名称】查看具体响应内容。
![!执行历史](../../img/api_test/definition/用例执行历史2.png){ width="900px" }

![!执行历史](../../img/api_test/definition/用例执行历史3.png){ width="900px" }

!!! ms-abstract "" 
    选择过滤条件快捷搜索执行历史报告。
![!执行历史](../../img/api_test/definition/用例执行历史4.png){ width="900px" }

### 6.5 变更历史
!!! ms-abstract "" 
    查看该用例的变更历史。
![!变更历史](../../img/api_test/definition/用例变更历史.png){ width="900px" }

## 7 MOCK 功能
!!! ms-abstract ""
    点击【接口定义 ID】进入 API 详情页面。
![!API/CASE 列表](../../img/api_test/definition/创建mock.png){ width="900px" }

!!! ms-abstract ""
    如下图，按照序号顺序点击进入 MOCK 设置页面，按需设置请求头、QUERY、REST、请求体、以及响应体内容，并点击【创建】保存。
![!API/CASE 列表](../../img/api_test/definition/设置mock页面.png){ width="900px" }

![!API/CASE 列表](../../img/api_test/definition/mock设置页面设置.png){ width="900px" }

!!! ms-abstract "说明"
    - **格式化：** 可以格式化为对应格式展示，如 json 格式，xml 格式。
    - **跟随 API：** 开启后，返回数据默认为对应的 API 定义的响应数据。

!!! ms-abstract ""
    点击调试按钮，进入 Mock 调试页面。
![!API/CASE 列表](../../img/api_test/definition/mock调试.png){ width="900px" }

!!! ms-abstract ""
    选择 Mock 环境，点击【服务端执行】或者【本地执行】进行调试。
![!API/CASE 列表](../../img/api_test/definition/mock返回.png){ width="900px" }

!!! ms-abstract ""
    如下图对 MOCK 接口进行【编辑】、【调试】、【复制】、【复制 Mock 地址】、【删除】等操作。
![!API/CASE 列表](../../img/api_test/definition/mock功能.png){ width="900px" }

!!! ms-abstract "操作说明"
    - **编辑：** 编辑 MOCK 接口。
    - **调试：** 调试 MOCK 接口，可选择服务端调试或本地调试。
    - **复制：** 复制 MOCK 接口。
    - **复制 Mock 地址：** 将该 MOCK 地址复制下来，供外部服务调用。
    - **删除：** 删除 MOCK 接口。

## 8 API/CASE/MOCK 列表
!!! ms-abstract ""
    切换【API】或者点击【全部接口】查看 API 列表。
![!API/CASE 列表](../../img/api_test/definition/API列表.png){ width="900px" }

!!! ms-abstract ""
    切换【CASE】或者点击【全部 CASE 】查看 CASE 列表。
![!API/CASE 列表](../../img/api_test/definition/CASE列表.png){ width="900px" }

!!! ms-abstract ""
    切换【MOCK】或者点击【全部 MOCK 】查看 MOCK 列表。
![!API/CASE 列表](../../img/api_test/definition/MOCK列表.png){ width="900px" }

## 9 切换协议
!!! ms-abstract "注意"
    系统内置 HTTP 协议，其他协议需要在【系统设置-系统-插件】上传协议插件，具体参考：[接口协议插件](../../system_management/system/#72)。

!!! ms-abstract "" 
    点击具体协议名称，如 HTTP，切换到对应协议的 API/CASE 列表页面，进行相关接口定义、调试、创建用例等操作。
![!切换协议](../../img/api_test/definition/切换协议.png){ width="900px" }	

!!! ms-abstract "说明" 
	- **协议类型的插件：** 具体支持插件请查看 [插件列表](../../plugin.md)。
	- **协议类型插件开发文档：** 请查看 [接口测试插件开发文档](https://github.com/metersphere/api-test-plugins/wiki/MeterSphere-v3-%E6%8F%92%E4%BB%B6%E5%BC%80%E5%8F%91%E6%89%8B%E5%86%8C)。