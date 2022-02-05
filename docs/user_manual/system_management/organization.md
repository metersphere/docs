##组织成员管理
>同系统下组织成员操作

##工作空间管理
>同系统下工作空间操作

##服务集成

点击点击左侧`组织`下拉菜单中的`服务集成`进入服务集成界面，查看当前组织集成的缺陷第三方平台，或对需要集成的第三方平台进行配置。

![!服务集成](../../img/system_management/服务集成首页.png)

###缺陷管理平台

- TAPD 平台

!!! info "指引"
    * Tapd Basic Auth 账号信息在"公司管理-安全与集成-开放平台"中查询
    * 保存 Basic Auth 账号信息后，需要在 Metersphere 项目中手动关联，在项目列表下编辑项目，输入 TAPD 项目 ID

-  JIRA 平台

!!! info "指引"
    * JIRA software server 认证信息为 账号密码，JIRA software cloud 认证信息为 账号+令牌(账户设置-安全-创建 API 令牌)
    * 保存账号信息后，需要在 Metersphere 项目中手动关联，在项目列表下编辑项目，输入 JIRA 项目关键字
    * JIRA 地址， 例：https://xxx.atlassian.net/
    * 问题类型 和 JIRA 的事务类型保持一致，例：缺陷，Bug
    * 提交缺陷失败时可以查看 /opt/metersphere/logs/metersphere 下系统日志定位问题

!!! notice "提示"
     TAPD、Jira 现已支持自定义字段配置。配置缺陷模板时填入该字段在对应平台调用 API 创建缺陷时的 API 字段名称。配置完成后，对于使用该缺陷模板的项目，创建缺陷时填写的自定义字段值可同步至选定的缺陷管理平台中。

- 禅道平台

!!! info "指引"
    * 账号密码为具有相应权限的禅道账号，账号需要具有超级 model 调用接口权限
    * 保存账号信息后，需要在 Metersphere 项目中手动关联，在项目列表下编辑项目，输入 Zentao ID
    
    !!! warning "注意"
            如果 禅道bug 是附属在项目上，则关联的 Zentao ID 为项目 ID
            
            如果 禅道bug 是附属在产品上，则关联的 Zentao ID 为产品 ID
    * 如果提示因为安全问题api禁用，需要修改禅道服务器配置文件，加上 $config->features->apiGetModel = true; 此配置

###消息通知

点击点击左侧`组织`下拉菜单中的`消息通知`进入通知界面，支持查看和自定义当前组织中 Jenkins 接口调用任务通知、测试计划任务通知、测试评审任务通知、缺陷任务通知。

![!消息通知](../../img/system_management/消息通知首页.png)

###操作日志

> 同系统下操作日志

可查看和设置当前组织中jenkins接口调用任务通知、测试计划任务通知、测试评审任务通知、缺陷任务通知。