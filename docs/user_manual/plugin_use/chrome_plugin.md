---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

该插件为 MeterSphere 配套的浏览器插件，该插件可将用户在浏览器操作时的 HTTP 请求记录下来并 生成 JMX 文件（JMeter 脚本文件），用于在 MeterSphere 中进行接口测试或性能测试。

## 1 开发者模式安装

!!! info "开发者模式安装"
     * 谷歌浏览器输入 chrome://extensions/ 进入扩展程序安装界面，打开开发者模式
     * https://github.com/metersphere/chrome-extensions/releases/tag/v1.2.4 下载 metersphere-chrome-plugin-v1.2.4.zip 后进行解压
     * 选择【加载已解压的扩展程序】选择解压后的目录进行安装  

## 2 使用指导 
插件安装后，点击浏览器插件列表中该插件图标，在弹出页面中可以修改录制脚本的名称，点击开始录制按钮
![录制](../../img/user_manual/plugin_use/chrome_plugin/chrome_plugin_1.png)

访问需要进行录制的站点，进行正常使用操作，浏览器中的所有网络请求均会被记录下来。当操作完成后，点击插件界面的停止按钮停止录制<br>
![录制](../../img/user_manual/plugin_use/chrome_plugin/chrome_plugin_2.png)

录制停止后，点击插件界面的保存按钮进行保存 <br>
![录制](../../img/user_manual/plugin_use/chrome_plugin/chrome_plugin_3.png)

插件弹出所有记录到请求的站点列表，勾选需要保留的站点请求点击下载按钮，下载 JMX 脚本至本地
![录制](../../img/user_manual/plugin_use/chrome_plugin/chrome_plugin_4.png)

在 MeterSphere 中创建性能测试任务， 上传刚刚录制的 JMX 脚本，然后设置并发参数，进行性能测试。
![录制](../../img/user_manual/plugin_use/chrome_plugin/chrome_plugin_5.png)