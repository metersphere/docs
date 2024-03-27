---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
    点击【项目管理】-【文件管理】，进入文件管理页面
![!文件管理](../../img/project_management/file_management/文件管理.png){ width="900px" }

## 1 模块管理
!!! ms-abstract ""
    点击【添加子模块】，添加模块节点
![!添加子节点](../../img/project_management/file_management/添加子节点.png){ width="900px" }

!!! ms-abstract ""
    左侧节点进行【新增子节点】、【展开/收缩】、【重命名】、【删除】等操作
![!左侧节点功能](../../img/project_management/file_management/左侧节点功能.png){ width="900px" }

## 2.上传文件
!!! ms-abstract ""
    点击【添加文件】，选择文件类型，将文件拖拽到指定区域即可上传。以 JAR 文件上传为例
![!文件上传功能](../../img/project_management/file_management/文件上传功能.png){ width="900px" }

!!! ms-abstract ""
    JAR 文件上传后，默认是【禁用】状态，需要点击【启用】，否则在接口前后置脚本中引用不到 JAR 包内容
![!启用jar包](../../img/project_management/file_management/启用jar包.png){ width="900px" }

!!! ms-abstract ""
    上传的文件进行【下载】、【删除】、【移动】、【切换显示】等操作，其中 JAR 包还有【开启/禁用】功能
![!上传文件功能操作](../../img/project_management/file_management/上传文件功能操作.png){ width="900px" }
![!上传文件展示形式](../../img/project_management/file_management/上传文件展示形式.png){ width="900px" }

!!! ms-abstract ""
    设置列表表头、每页显示数量
![!表头设置](../../img/project_management/file_management/表头设置.png){ width="900px" }
![!页面显示数量](../../img/project_management/file_management/页面显示数量.png){ width="900px" }

## 3 存储库
!!! ms-abstract ""
    点击【添加存储库】，对接第三方仓库，如 Gitea、GitHub、GitLab、Gitee 和其他仓库等。
![!第三方仓库](../../img/project_management/file_management/第三方仓库.png){ width="900px" }
![!第三方具体仓库](../../img/project_management/file_management/第三方具体仓库.png){ width="900px" }

!!! ms-abstract ""
    以 Gitea 仓库为例，【存储库地址】要以【.git】结尾，点击【测试连接】连接成功
![!gitea仓库为例](../../img/project_management/file_management/gitea仓库为例.png){ width="900px" }

!!! ms-abstract ""
    点击【储存库】-【添加文件】，填写分支和文件路径
![!配置存储库拉取文件](../../img/project_management/file_management/配置存储库拉取文件.png){ width="900px" }

!!! ms-abstract ""
    拉取的文件进行【下载】、【删除】操作
![!拉取文件下来的功能](../../img/project_management/file_management/拉取文件下来的功能.png){ width="900px" }