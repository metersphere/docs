!!! ms-abstract ""
     该插件帮助开发人员在IntelliJ IDEA IDE 中，将编写的 HTTP 接口文档信息快捷推送到 MeterSphere 系统中。

!!! info "安装注意"
     * 不低于 2018.3 的 IDEA Ultimate，Community 版本（2019,2020版本支持 ???）
   
## 1 插件安装
### 1.1 在线安装
!!! ms-abstract ""
     在 IDEA -> Settings -> plugins -> Marketplace 搜索并选择【MeterSphere】，点击 install 即可进行在线安装。

![ideal_plugin](../../img/user_manual/plugin_use/idea_plugin/idea_plugin_4.png)

### 1.2 离线安装
!!! ms-abstract ""
     先在 [jetbrains plugin marketplace](https://plugins.jetbrains.com/plugin/18097-metersphere/versions) 中下载与 IDEA版本匹配的版本,
     然后在 IDEA -> Settings -> plugins，点击【Install Plugin from Disk】并选择已下载的离线包进行安装。

![ideal_plugin](../../img/user_manual/plugin_use/idea_plugin/idea_plugin_1.png)

## 2 插件使用
!!! ms-abstract ""
     IDEA -> Settings -> MeterSphere 中配置好访问地址以及 AK/SK 等详细信息，点击【test】按钮即确认连接成功。

![ideal_plugin](../../img/user_manual/plugin_use/idea_plugin/idea_plugin_2.png)

!!! ms-abstract ""
     配置导出是否覆盖、目录层级等信息后，点击【Apply】按钮。

![ideal_plugin](../../img/user_manual/plugin_use/idea_plugin/idea_plugin_3.png)

!!! ms-abstract ""
     在要同步接口的 Controller 页面中右键选择【Export MeterSphere】即可将代码中的 HTTP 接口推送到 MeterSphere 系统中。