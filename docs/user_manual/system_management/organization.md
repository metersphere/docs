##组织成员管理
>同系统下组织成员操作

##工作空间管理
>同系统下工作空间操作

##服务集成

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
    
    !!! warning "注意"
        现在不支持自定义的字段配置

- 禅道平台

!!! info "指引"
    * 账号密码为具有相应权限的禅道账号，账号需要具有超级 model 调用接口权限
    * 保存账号信息后，需要在 Metersphere 项目中手动关联，在项目列表下编辑项目，输入 Zentao ID
    
    !!! warning "注意"
            如果 禅道bug 是附属在项目上，则关联的 Zentao ID 为项目 ID
            
            如果 禅道bug 是附属在产品上，则关联的 Zentao ID 为产品 ID
    * 如果提示因为安全问题api禁用，需要修改禅道服务器配置文件，加上 $config->features->apiGetModel = true; 此配置
