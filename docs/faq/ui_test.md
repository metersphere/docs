---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

## 1.本地调试时，启动日志中出现两个 ChromeDriver 版本号，原因是？
![! UI测试-版本](../img/faq/UI测试本地调试版本不对.png){ width="900px" }

!!! ms-abstract ""
    本地浏览器的版本号与下载的驱动版本不匹配，可查看浏览器版本后，重新下载对应版本的驱动。

## 2.本地调试，启动日志中报错：`cannot find Chrome binary`，如何解决？
![! UI测试-版本](../img/faq/UI测试本地调试找不到浏览器.jpg){ width="900px" }

!!! ms-abstract ""
    将 chrome.exe 的路径配置到环境变量 PATH 里。

## 3.本地调试，日志没有任何报错情况，但是页面浏览器没有被调用起来，如何处理？
![! UI测试-版本](../img/faq/UI测试不勾选性能测试.png){ width="900px" }

!!! ms-abstract ""
    在UI场景中，不勾选【性能模式】，即可看到浏览器被调用的过程。