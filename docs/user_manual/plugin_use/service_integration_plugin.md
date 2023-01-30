!!! info "注意"
    自v2.4 版本缺陷对接实现了服务集成插件化，可根据自身需求开发对应插件。目前已实现 禅道、Jira 平台的插件化，原先使用 禅道、Jira 的用户，需要下载下插件，并在系统设置-插件管理上传插件 使用方式跟原来一致，具体参考插件项目 https://github.com/metersphere/metersphere-platform-plugin

以 Jira 平台为例，在【系统设置】-【系统】-【插件管理】界面下，上传 Jira 插件包
![录制](../../img/user_manual/plugin_use/service_integration_plugin/service_integration_plugin_1.png)

【系统设置】-【系统】-【服务集成】处可看到 Jira 平台，选中 Jira 平台可出现相关账号信息
![录制](../../img/user_manual/plugin_use/service_integration_plugin/service_integration_plugin_2.png)

点击【编辑】填写Jira 平台相关账号信息后进行保存，点击【测试连接】可看到验证通过的提示
![录制](../../img/user_manual/plugin_use/service_integration_plugin/service_integration_plugin_3.png)

【系统设置】-【系统】-【项目管理】处，进行项目编辑时，可看到【集成第三方平台】的下拉框有 Jira 平台选项以及 Jira 平台的相关信息
![录制](../../img/user_manual/plugin_use/service_integration_plugin/service_integration_plugin_4.png)