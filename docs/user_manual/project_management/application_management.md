## 应用管理权限
![!项目设置](../../img/project_management/应用管理权限1.png)

如果 `项目设置` 里看不到 `应用管理` 菜单，表示此用户没有此权限，需要到 `用户组与权限` 修改 `项目管理员` 的权限。
![!项目设置](../../img/project_management/应用管理权限2.png)

选中‘应用管理’权限即可
![!项目设置](../../img/project_management/应用管理权限3.png)

## 应用管理设置
点击 `项目设置->应用管理` 可以对MeterSphere的测试跟踪、接口测试、性能测试等应用进行高级设置。
![!项目设置](../../img/project_management/应用管理1.png)

对部分参数说明如下：

### 测试跟踪设置
维护 `测试跟踪` 下的一些高级应用配置管理。包含 `启用设置` 。包含 `测试用例自定义ID` 和 `定时清理测试计划报告` 配置。
![!项目设置](../../img/project_management/测试跟踪设置1.png)

#### <font size=4> 测试用例自定义ID </font>
开启后，在创建 `测试用例` 页面，可以自定义设置用例ID
![!项目设置](../../img/project_management/测试跟踪设置2.png)

#### <font size=4> 定时清理测试计划报告 </font>
![!项目设置](../../img/project_management/测试跟踪设置3.png)

### 接口测试设置
维护`接口测试` 下的一些高级应用配置管理。包含 `启用设置` 。包含 `接口定义URL可重复` ，`场景自定义ID` ，`TCP Mock Port` 以及 `定时清理接口测试报告` 等配置。
![!项目设置](../../img/project_management/接口测试设置1.png)

####  <font size=4> 接口定义URL可重复 </font>
启用后接口定义重复性校验将不校验URL，同一个项目下允许接口路径想相同的 `接口定义` 
![!项目设置](../../img/project_management/接口测试设置2.png)

#### <font size=4> 场景自定义ID </font>
启用后创建场景支持自定义设置场景ID
![!项目设置](../../img/project_management/接口测试设置3.png)

#### <font size=4> TCP Mock Port </font>
设置接口协议为TCP的接口，Mock服务的可用性。
![!项目设置](../../img/project_management/接口测试设置4.png)

如果TCP协议的接口需要使用Mock服务，则需要开启此服务，开启后在接口测试中，Mock服务才可用。
![!项目设置](../../img/project_management/接口测试设置5.png)

#### <font size=4> 定时清理接口测试报告 </font>
![!项目设置](../../img/project_management/接口测试设置6.png)

### 性能测试设置
维护`接口测试` 下的一些高级应用配置管理。包含 `启用设置` 。包含 `定时清理接口测试报告` 配置。
![!项目设置](../../img/project_management/性能测试设置.png)
