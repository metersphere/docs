---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
    在接口自动化中经常需要添加前后置脚本及自定义脚本，通过新增的自定义代码片段功能，用户可以将常用的脚本保存下来，在需要使用的地方直接添加即可。

## 1 自定义代码片段维护
!!! ms-abstract ""
    选择【项目设置】-【更多选项】-【自定义代码片段】。
![!项目设置](../../img/project_management/创建代码片段1.png){ width="900px" }

!!! ms-abstract ""
    点击【创建代码片段】，可以把常用的脚本代码保存在这里。
![!项目设置](../../img/project_management/创建代码片段2.png){ width="900px" }

!!! ms-abstract ""
    点击【测试】可以校验此代码执行的情况，点击【确定】创建的代码片段保存在代码列表中。
![!项目设置](../../img/project_management/创建代码片段3.png){ width="900px" }

!!! ms-abstract ""
    同时系统提供相关的管理功能：【编辑】、【复制】和【删除】等，对代码片段进行管理。
![!项目设置](../../img/project_management/代码列表操作.png){ width="900px" }

## 2 自定义代码片段使用
!!! ms-abstract ""
    代码片段维护好后，在【接口、场景测试用例】或者【环境】的【前置脚本、后置脚本】中，选择【插入自定义代码片段】可以直接引用此代码，以【接口测试用例】为例。
![!项目设置](../../img/project_management/插入自定义代码片段.png){ width="900px" }

![!项目设置](../../img/project_management/插入自定义代码片段_1.png){ width="900px" }