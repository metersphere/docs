本仓库保存了 [MeterSphere 项目]() 的 [官方文档](https://metersphere.io/docs/)，该文档使用 [MkDocs]() 文档框架下的 [Material for MkDocs]() 主题进行构建。

## 本地开发

### 克隆本仓库
```bash
git clone https://github.com/metersphere/docs.git
```

### 安装依赖
```bash
cd docs
pip install -r requirements/requirements.txt
```

### 修改文档内容
本文档的文档结构定义在 `mkdocs.yml` 文件中，文档的具体内容均在 `docs` 目录中。
```yaml
..........
nav:
    - 项目介绍: index.md
    - 快速开始:
          - 一键部署: quick_start/quick_start.md
          - 创建项目: quick_start/create_project.md
          - 使用测试跟踪: quick_start/test_track.md
          - 使用接口测试: quick_start/api_test.md
          - 使用UI 测试: quick_start/ui_test.md
          - 使用性能测试: quick_start/load_test.md
    - 系统架构: system_arch.md
    - 安装部署:
          - Linux单机部署:
                - 在线安装: installation/online_installation.md
                - 离线安装: installation/offline_installation.md
                - 在线升级: installation/online_upgrade.md
                - 离线升级: installation/offline_upgrade.md
          - Kubernetes中部署: installation/kubernetes_installation.md
          - 命令行工具: installation/cli.md
    - 用户手册:
          - 通用功能: user_manual/general.md
          - 测试跟踪:
                - 模块说明: user_manual/test_track/intro.md
                - 首页: user_manual/test_track/home.md
                - 功能用例: user_manual/test_track/test_case.md
                - 用例评审: user_manual/test_track/test_case_review.md
                - 测试计划: user_manual/test_track/test_plan.md
                - 缺陷管理: user_manual/test_track/test_defect.md
                - 报告: user_manual/test_track/test_report.md
          - 接口测试:
                - 模块说明: user_manual/api_test/intro.md
                - 首页: user_manual/api_test/home.md
                - 接口定义: user_manual/api_test/api_definition.md
                - 接口自动化: user_manual/api_test/api_automation.md
                - 接口测试报告中心: user_manual/api_test/test_report.md
                - 用例步骤说明: user_manual/api_test/api_step.md
                - 内置函数: user_manual/api_test/functions.md
          - UI 测试:
                - 模块说明: user_manual/ui_test/intro.md
                - 注意事项: user_manual/ui_test/info.md
                - 元素库: user_manual/ui_test/ui_element_store.md
                - UI 自动化: user_manual/ui_test/ui_automation.md
                - 测试报告: user_manual/ui_test/ui_test_report.md  
          - 性能测试:
                - 模块说明: user_manual/load_test/intro.md
                - 首页: user_manual/load_test/home.md
                - 性能测试: user_manual/load_test/load_test.md
                - 性能测试报告: user_manual/load_test/test_report.md
          - 报表统计:
                - 项目报表: user_manual/report_statistics/project_statistics.md
          - 项目设置:
                - 项目信息: user_manual/project_management/project_info.md
                - 项目成员: user_manual/project_management/project_user.md
                - 用户组与权限: user_manual/project_management/usergroup_permission.md
                - 项目环境: user_manual/project_management/project_environment.md
                - 文件管理: user_manual/project_management/file_management.md
                - 自定义代码片段: user_manual/project_management/customcode_snippets.md
                - 模版管理: user_manual/project_management/template_management.md
                - 消息设置: user_manual/project_management/notice_management.md
                - 操作日志: user_manual/project_management/operation_log.md
                - 应用管理: user_manual/project_management/application_management.md
          - 系统设置:
              - 模块说明: user_manual/system_management/intro.md
              - 系统: user_manual/system_management/system.md
              - 工作空间: user_manual/system_management/workspace.md
    - 使用教程:
          - MeterSphere的UI测试模块如何远程调用浏览器: tutorial/ui_testing.md
          - 使用 MeterSphere 进行 Dubbo 接口测试: tutorial/dubbo.md
          - 使用 MeterSphere 进行场景化接口测试: tutorial/api_testing.md
          - 使用预执行脚本功能生成接口认证签名: tutorial/pre_processor.md
    - 教学视频: teach_video/video_index.md
    - 常见问题:
          - 安装部署相关: faq/installation.md
          - 测试跟踪相关: faq/test_track.md
          - 接口测试相关: faq/api_test.md
          - 性能测试相关: faq/load_test.md
          - 报表统计相关: faq/report_statistics.md
          - 系统设置相关: faq/system_management.md
          - 企业版相关: faq/enterprise.md
    - 开发文档: dev_manual.md
    - 用户案例:
          - 中国移动上研院基于MeterSphere构建规范化测试体系: case_studies/china_mobile_research_institute_shanghai.md
          - 88完美邮箱全面提升产品质量的落地指南: case_studies/88com.md
          - 蔚澜环保基于MeterSphere的自动化测试实践: case_studies/weilanep.md
          - 易盛信息MeterSphere接口测试使用经验: case_studies/esunny.md
          - 永福信息基于MeterSphere从项目维度持续推进测试任务: case_studies/yongfu.md
          - 九里云基于MeterSphere落地一站式自动化测试平台: case_studies/jiuliyun.md
          - 民生科技基于MeterSphere平台实现测试用例复用: case_studies/mskj.md
          - 360借助MeterSphere提升自动化测试水平: case_studies/360b.md
    - 更新日志: about/changelog.md
    - 联系我们: about/contact.md
..........
```

文档内容使用 markdown 语法编写，若要添加新的文档，需要先在 `mkdocs.yml` 文件中的 `nav` 部分增加对应章节导航。

### 本地调试文档
```bash
mkdocs serve
```
执行上述命令后，可通过 `http://127.0.0.1:8000` 地址查看生成的文档内容，当修改文档后，页面内容会自动更新。

### 构建文档
```bash
mkdocs build
```

执行上述命令后，会在 `site` 目录下生成文档站点的静态文件，将目录中的内容复制到任意 HTTP 服务器上即可完成文档的部署。

## 帮助完善文档

### Fork 文档仓库
点击仓库右上角的 `fork` 按钮，复制本仓库到自己的 github 账号。

### 克隆 fork 后的仓库
```bash
git clone https://github.com/your-github-account/docs.git
```

### 本地修改并调试

### Push 修改内容到 GitHub 仓库

### 提交 Pull Request 到本仓库


## 问题反馈

如果您发现文档中存在错误，或对文档内容存在疑问，请提交 GitHub Issue 到 [MeterSphere 项目的主仓库](https://github.com/metersphere/metersphere/issues)

