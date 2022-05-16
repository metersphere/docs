1. 修改 /opt/metersphere/.env 文件，MS_SELENIARM_ENABLED=true 修改配置后加载配置文件执行 msctl reload
2. docker ps 检查 local-selenium-grid 容器是否成功启动
3. 在 MeterSphere 系统参数设置中修改 selenium-docker 地址为http://local-selenium-grid:4444
![UI系统设置](../../img/ui_test/UI系统设置.png)
4. UI测试用例，默认 "性能模式" 没有截图展示，关掉 "性能测试" 可以查看每个步骤的截图