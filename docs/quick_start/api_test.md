---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

## 1 调试
!!! ms-abstract ""
    如下图，点击【新建请求】或者【＋】新建接口请求。
![!新建请求](../img/quick_start/api/新建请求1.png){ width="900px" }

!!! ms-abstract ""
    接下来按下图序号顺序，选择 HTTP 协议、GET 方法，输入获取文章列表接口的 URL 地址 `https://demo.halo.run/apis/api.console.halo.run/v1alpha1/posts` ，选择 Query 参数，输入 `page 等于 1，size 等于 5`。
![!新建请求](../img/quick_start/api/新建请求2.png){ width="900px" }

!!! ms-abstract "" 
    输入接口认证信息，如下图 Halo 接口采用 Basic Auth 登录认证，选择 `Basic Auth`,`用户名：demo，密码：P@ssw0rd123..`，点击【服务端执行】，执行成功后保存。
![!新建请求](../img/quick_start/api/执行.png){ width="900px" }  

!!! ms-abstract "注意" 
    本地执行需在本地安装 task_runner 和 在个人信息处配置 本地 task_runner 的地址。

## 2 创建接口
!!! ms-abstract "" 
    如下图，点击【新建请求】或者【＋】新建接口请求。
![!新建接口](../img/quick_start/api/API新建请求.png){ width="900px" }

!!! ms-abstract "" 
    在新建接口页面，选择 GET 方法，输入获取文章列表接口的 PATH 地址 `api.console.halo.run/v1alpha1/posts`，选择 Query 参数，输入 `page 等于 1，size 等于 5`，输入接口名称 `获取文章列表`，所属模块选择 `未规划接口`，状态设置为 `进行中`。
![!新建接口](../img/quick_start/api/API新建请求2.png){ width="900px" }

!!! ms-abstract "" 
    输入认证信息，选择【认证】，选择 `Basic Auth`,`用户名：demo，密码：P@ssw0rd123..`，然后点击保存。
![!新建接口](../img/quick_start/api/API新建请求3.png){ width="900px" }

## 3 创建环境
!!! ms-abstract "" 
    如下图，点击【序号1】或者直接切换到【项目管理-环境管理】页面。
![!创建环境](../img/quick_start/api/创建环境1.png){ width="900px" }

!!! ms-abstract ""
    按下图序号顺序，点击【+】后，填写环境名称 `Halo`，切换 HTTP ，点击【添加 HTTP 】，选择 https ,输入域名地址 `demo.halo.run`，点击确认。
![!创建环境](../img/quick_start/api/创建环境2.png){ width="900px" }

## 4 接口定义调试
!!! ms-abstract "" 
    重新回到接口定义页面，点击调试，然后点击【服务端执行】，执行成功后查看执行结果。
![!执行](../img/quick_start/api/调试.png){ width="900px" }	

## 5 添加后置操作
!!! ms-abstract "" 
    如下图，点击后置，点击【+ 后置条件】，选择【提取参数】。
![!执行](../img/quick_start/api/添加后置操作1.png){ width="900px" }	

!!! ms-abstract "" 
    输入参数名称 `total`，类型选择 `临时参数`，方式选择 `JSONPATH`,范围默认 `Body`，表达式选择【快捷提取】。
![!执行](../img/quick_start/api/添加后置操作2.png){ width="900px" }	

!!! ms-abstract "" 
    在【快捷提取】界面，点击 `total` 字段，然后点击确认。
![!执行](../img/quick_start/api/添加后置操作3.png){ width="900px" }	

!!! ms-abstract "" 
    点击【服务端执行】后，点击【提取】查看提取的结果。
![!保存为新用例](../img/quick_start/api/添加后置操作4.png){ width="900px" }	

## 6 添加断言
!!! ms-abstract "" 
    如下图，点击【+ 断言】，选择【状态码】，断言条件选择 `等于 200`。
![!执行](../img/quick_start/api/添加断言1.png){ width="900px" }	

!!! ms-abstract "" 
    点击【服务端执行】，执行成功后在执行结果处点击【断言】查看断言结果。
![!执行](../img/quick_start/api/添加断言2.png){ width="900px" }	

## 5 保存为用例
!!! ms-abstract "" 
    如下图，接口调试成功后，点击【保存为新用例】快速创建用例。
![!创建用例](../img/quick_start/api/创建用例1.png){ width="900px" }		

## 6 创建场景
!!! ms-abstract ""
    如下图，点击【序号1】或者【序号2】创建场景。
![!创建场景](../img/quick_start/api/创建场景1.png){ width="900px" }

!!! ms-abstract ""
    点击【添加步骤】，选择【导入系统请求】。
![!创建场景](../img/quick_start/api/创建场景2.png){ width="900px" }

!!! ms-abstract ""
    选择【接口】，选择【获取文章列表】，点击【复制】，然后点击保存。
![!创建场景](../img/quick_start/api/创建场景3.png){ width="900px" }

!!! ms-abstract ""
    点击【服务端执行】生成报告。
![!创建场景](../img/quick_start/api/创建场景4.png){ width="900px" }

## 7 查看报告
!!! ms-abstract "" 
    如下图，在【报告】页面查看场景 `文章管理流程` 的【场景报告】。
![!查看测试报告](../img/quick_start/api/查看报告1.png){ width="900px" }

!!! ms-abstract "" 
    点击 `文章管理流程` 的报告名称预览报告详情。
![!查看测试报告](../img/quick_start/api/查看报告2.png){ width="900px" }

!!! ms-abstract "" 
    如下图，点击【步骤名称】查看步骤实际请求的响应内容。
![!查看测试报告](../img/quick_start/api/查看报告3.png){ width="900px" }

