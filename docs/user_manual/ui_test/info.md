

!!! ms-abstract ""

    - 修改 /opt/metersphere/.env 文件中 MS_SELENIARM_ENABLED 值，`MS_SELENIARM_ENABLED=true`， 修改配置后加载配置文件执行 `msctl reload`。
    - docker ps 检查 local-selenium-grid 容器是否成功启动。
    - 在 MeterSphere 系统参数设置中修改 selenium-docker 地址为`http://local-selenium-grid:4444`。
    - UI 测试用例，默认 "性能模式" 没有截图展示，关掉 "性能测试" 可以查看每个步骤的截图。
    - 如果导入 License 成功后，依然显示没有 UI 测试模块，请到【用户组与权限】中确认是否有 UI 模块的权限。

![UI系统设置](../../img/ui_test/UI系统设置.png){ width="900px" }
    