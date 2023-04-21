1. 修改 /opt/metersphere/.env 文件，MS_UI_ENABLED=true 修改配置后加载配置文件执行 msctl reload
2. msctl status 检查 selenium-hub 容器是否成功启动
3. 在 MeterSphere 系统参数设置中修改 selenium-grid 地址为 http://selenium-hub:4444
![UI系统设置](../../img/ui_test/UI系统设置.png)
4. UI测试用例，默认 "性能模式" 没有截图展示，关掉 "性能测试" 可以查看每个步骤的截图 <br>
5. 如果导入 License 成功后，依然没有 UI 测试模块，请到【用户组与权限】处配置 UI 模块权限