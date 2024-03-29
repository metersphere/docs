---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
    测试计划属于某个项目，并可关联该项目下的测试用例。测试计划用于将测试各环节不同类型的测试任务添加到一个测试计划中，包括功能测试、接口测试和性能测试等，支持实时展示各测试环节的进度及测试情况，并实时生成测试报告。<br>
    测试计划可将测试各环节加入到一个测试计划中，包括功能测试、接口测试和性能测试等，能实时展示各测试环节的进度及测试情况，并实时生成测试报告。<br>
    点击【测试跟踪】，点击【项目】，点击测试计划，可查看当前项目中的测试计划。
![!测试计划管理](../../../img/track/测试计划管理.png){ width="900px" }

## 1 计划列表操作
!!! ms-abstract ""
    在测试计划列表信息页，鼠标点击某个计划，进入计划详情页面。
![!计划列表维护](../../../img/track/计划列表维护1.png){ width="900px" } 

!!! ms-abstract ""
    点击【执行】按钮，选择和勾选运行测试计划的相关配置后，点击【执行】即可。默认环境为用例首次关联进测试计划所选择的用例，选择新环境后可选择执行和保存，保存后新选择的环境为默认环境，点击执行不会修改默认环境，默认环境多用于定时任务、API调用及流水线触发执行。<br>
![!计划列表维护](../../../img/track/测试计划区分环境.png){ width="900px" }

!!! ms-abstract ""
    可以管理和维护本次计划测试的范围：功能测试用例、接口测试用例、场景测试用例、性能测试用例等。
![!计划列表维护](../../../img/track/计划列表维护2.png){ width="900px" } 

## 2 测试报告查看
!!! ms-abstract ""
    计划执行后，可以点击【查看测试报告】。
![!测试报告查看](../../../img/track/查看测试报告.png){ width="900px" } 

![!测试报告查看](../../../img/track/查看测试计划报告.png){ width="900px" }

!!! ms-abstract ""
    报告详细解读见 [测试跟踪->报告](../../test_report/)。