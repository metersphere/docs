

!!! ms-abstract ""
    MeterSphere UI 测试模块围绕应用系统的 用户界面 提供以下主要功能：

    - **元素库**：平台提供元素库的功能，通过创建元素库，可以把 UI 自动化场景中的单个步骤，进行统一管理，达到页面元素在不同 UI 场景中复用的效果。
    - **UI 自动化**：支持手动创建 UI 自动化场景和导入 SeleniumIDE 工具录制好的 side 脚本文件，支持添加浏览器操作、
    弹窗操作、元素操作、鼠标操作、输入操作、流程控制等步骤，并提供查看元素库、前置操作、后置操作、错误处理高级功能。
    - **测试报告**：提供直观、美观的页面对UI测试的结果进行可视化展示，可查看场景全部步骤和失败步骤，以及控制台详情，并且支持对步骤执行时的UI截图预览。

    备注: UI 测试模块是企业版 X-Pack 功能增强包功能。如需使用企业版，请点击：[申请企业版试用](https://jinshuju.net/f/CzzAOe)。

!!! ms-abstract "注意事项"

    - 修改 /opt/metersphere/.env 文件中 MS_UI_ENABLED 值，`MS_UI_ENABLED=true`， 修改配置后加载配置文件执行 `msctl reload`。
    - docker ps 检查 selenium-hub 容器是否成功启动。
    - 在 MeterSphere 系统参数设置中修改 selenium-docker 地址为`http://selenium-hub:4444`。
    - UI 测试用例，默认 "性能模式" 没有截图展示，关掉 "性能测试" 可以查看每个步骤的截图。
    - 如果导入 License 成功后，依然显示没有 UI 测试模块，请到【用户组与权限】中确认是否有 UI 模块的权限。

![UI系统设置](../../img/ui_test/UI系统设置.png){ width="900px" }