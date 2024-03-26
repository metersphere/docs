---
description: MeterSphere 一站式开源持续测试平台官方文档。MeterSphere 涵盖测试管理、接口测试、UI 测试和性能测试等功能，全面兼容 JMeter、Selenium 等主流开源标准，有效助力开发和测试团队充分利用云弹性进行高度可 扩展的自动化测试，加速高质量的软件交付。
---

!!! ms-abstract ""
     **组织**：组织级别的管理配置功能，开源版默认只可使用一个组织空间。组织下可以对组织成员、用户组、项目、服务集成、模板、日志、任务中心等功能做配置，用户需要在当前组织中有【组织管理员】角色才能看到该菜单。

## 1 成员
!!! ms-abstract ""
    点击左侧【系统设置-组织-成员】进入成员管理界面，查看当前组织的所有成员信息。可以对成员进行【添加成员】【查询】【修改用户组】【编辑】【移除】等操作。
![工作空间](../../img/system_management/组织成员.png){ width="900px" }


!!! ms-abstract ""
    - **添加成员**<br>
    点击【添加成员】按钮添加成员户，在弹出页面中选择要添加的用户。可根据用户 ID 和用户邮箱搜索需要添加的用户，并设置添加用户的用户组权限，系统支持可一次添加多个成员。
![!添加成员](../../img/system_management/组织添加成员.png){ width="900px" }

!!! ms-abstract ""
    -  **查询用户**<br>
    可按姓名、邮箱、手机来模糊查询成员信息，输入查询信息，点击回车即可完成查询。
![查询成员用户](../../img/system_management/组织成员.png){ width="900px" }

!!! ms-abstract ""
    - **编辑成员**<br>
    在成员列表点击【编辑】按钮，可对当前成员所属项目和用户组权限做修改。
![!编辑成员](../../img/system_management/组织更新成员.png){ width="900px" }

!!! ms-abstract ""
    - **移除成员**<br>
    在成员列表点击【移除】按钮，当前用户失去组织的访问权限
![!编辑成员](../../img/system_management/组织移出成员.png){ width="900px" }



## 2 用户组
!!! ms-abstract ""
    点击左侧【系统设置-组织-用户组】菜单进入组织用户组管理界面。用户可基于自身需求创建自定义用户组，并赋予用户组不同的权限设置。系统预置组织管理员、组织成员角色且不可删除。组织管理员权限默认不可编辑。</br>
    支持对组织用户组做【新增】【编辑权限】【添加成员】【查询】操作。
 
![系统用户组首页](../../img/system_management/组织用户组.png){ width="900px" }

!!! ms-abstract ""
    - **用户组操作**<br>
    组织管理员可点击【+】按钮添加组织用户组，可以勾选配置平台用户访问菜单权限，点击【保存】按钮保存勾选的权限配置。点击【恢复默认】按钮可恢复为上一次保存的权限。<br>
    支持对用户组做【重命名】【删除】操作。选中用户组有【+】表示当前用户组管理员可以对该用户组快捷添加成员。
![系统用户组首页](../../img/system_management/添加组织用户组.png){ width="900px" }

!!! ms-abstract ""
    - **查询用户组**<br>
    用户组列表左上方，使用搜索框，根据名称查询用户组。
![编辑用户组信息](../../img/system_management/组织用户组查询.png){ width="900px" }

!!! ms-abstract ""
    - **添加用户组成员**<br>
    选择需要添加成员的用户组切换【成员】页面，为该用户组【快速添加成员】可批量勾选成员添加，支持对当前用户组成员做【移除】操作。
![系统用户组首页](../../img/system_management/添加组织用户组成员.png){ width="900px" }

## 3 项目

!!! ms-abstract ""
    点击右侧菜单【系统设置-组织-项目】进入项目管理界面。支持对当前组织的项目【新增】【查询】【编辑】【添加成员】【结束】【删除】操作。
    
![!项目](../../img/system_management/组织的项目.png){ width="900px" }

!!! ms-abstract ""

    - **新增项目**<br>
    点击【创建项目】按钮新建项目，在弹出页面中编辑项目名称、项目管理员、开启模块、资源池、描述、启用停用状态等信息。
![!新增项目](../../img/system_management/组织项目添加.png){ width="900px" }


!!! ms-abstract ""

    - **编辑项目**<br>
    点击【编辑】按钮编辑项目，在弹出页面中修改项目名称、项目管理员、开启模块、资源池、描述、启用停用状态等信息。
![!编辑项目](../../img/system_management/更新组织项目.png){ width="900px" }


!!! ms-abstract ""

    - **添加成员**<br>
    点击【添加成员】【列表成员数组】按钮均可给当前项目添加成员用户。
![!添加成员](../../img/system_management/组织项目添加成员.png){ width="900px" }

!!! ms-abstract ""

    - **结束项目**<br>
    点击【结束】按钮，结束项目不展示在项目切换列表。
![!删除工作空间](../../img/system_management/组织项目结束.png){ width="900px" }

!!! ms-abstract ""

    - **删除项目**<br>
    点击【删除】按钮，删除项目系统会在 30天 后执行删除项目，删除后点击名称【时钟】图标可以撤销删除状态。
![!删除工作空间](../../img/system_management/组织项目删除.png){ width="900px" }

## 4 服务集成
!!! ms-abstract ""
    可查看当组织里集成的缺陷管理平台，编辑当前组织需对接的第三方的管理平台配置信息。服务集成列表会展示当前组织已集成的缺陷管理平台，点击【展开】服务集成使用指引，按指引步骤下载并配置插件。<br/>
    Metersphere 平台与管理工具集成设置可分为三步骤来完成：<br>
    (1)下载需要使用的插件，并在【系统设置-系统-插件】上传。<br>
    (2)在【服务集成】列表配置第三方平台验证相关信息。<br>
    (3)在【项目设置-应用设置-缺陷管理】配置同步缺陷项目信息及同步策略。

![!服务集成](../../img/system_management/组织服务集成.png){ width="900px" }

<!-- 
### 4.1 与 TAPD 集成
!!! ms-abstract ""
    第一步：服务集成配置。

![!TAPD-配置](../../img/system_management/jira服务集成.png){ width="900px" }

!!! ms-abstract "参数说明"
    【API 账号和口令】是 Tapd Basic Auth 账号信息在【公司管理-安全与集成-开放平台】中查询。

!!! ms-abstract ""
    第二步：关联项目配置。<br>
    配置完服务集成后，还需要配置项目中引用 TAPD 项目的设置，即关联项目。点击页面右下角的【马上关联项目】进行设置。
![!TAPD-马上关联项目](../../img/system_management/TAPD-马上关联项目.png){ width="900px" }

!!! ms-abstract ""
    跳转到项目管理页面，点击项目列表中的【编辑】按钮，编辑项目里【TAPD 项目 ID】，以及缺陷模板等相关信息。
![!TAPD-编辑信息](../../img/system_management/TAPD-编辑信息.png){ width="900px" }

!!! ms-abstract ""
    同时，还需要配置项目中的 TAPD 缺陷模板设置，【缺陷模板】需要选择【TAPD-默认模板】。
![!TAPD-默认模板](../../img/system_management/TAPD-默认模板.png){ width="900px" }

!!! ms-abstract ""
    第三步：添加个人平台账号。<br>
    点击服务集成页面右下角的【马上添加】进行设置。
![!TAPD-马上添加](../../img/system_management/TAPD-马上添加.png){ width="900px" }

!!! ms-abstract ""
    该信息为通过 TAPD 提交缺陷的用户认证信息，若未填写，则使用组织中配置的默认信息。<br>
    选择【第三方平台账号】设置【Tapd】信息，如果不设置个人平台账号，则所有使用 MeterSphere 提交缺陷的用户，此缺陷推送到配置的服务平台上账号都是服务配置中设定的账号信息。
![!TAPD-第三方平台账号](../../img/system_management/TAPD-第三方平台账号.png){ width="900px" }

!!! ms-abstract ""
    参数说明：【TAPD 昵称】是 TAPD 个人设置里查看。
![!TAPD-昵称](../../img/system_management/TAPD-昵称.png){ width="900px" }

!!! ms-abstract ""
    以上配置完成后，在 Metersphere 系统中测试用例里，就可以关联 TAPD 的相关需求。
![!TAPD-关联需求](../../img/system_management/关联需求.png){ width="900px" }

!!! ms-abstract ""
    在缺陷管理提交缺陷后，平台类型显示为 TAPD 的数据，点击【同步缺陷】按钮，会将数据同步到 TAPD 系统中。
![!TAPD-同步需求](../../img/system_management/同步缺陷_TAPD.png){ width="900px" }

!!! ms-abstract ""
    在 TAPD 缺陷中可以查询到同步过来的缺陷数据。
![!TAPD-查询需求](../../img/system_management/TAPD-查询需求.png){ width="900px" } -->

### 4.1 与 JIRA 集成 
!!! ms-abstract ""
    插件上传后，到【系统设置-系统-服务集成】可以看到 jira 集成配置项。点击【编辑】按钮配置jira集成信息。</br>
    第一步：填写对接 JIRA 的地址、认证信息、账号信息、启停用开关。 填写完成后可以校验连接是否通过。</br>
    注意：认证信息区分私有化部署选择 Basic Auth 填写账号密码, 选择 Bearer Token 填写 Token, SaaS 版本只能选择 Basic Auth, 填写(账号+令牌)(账户设置-安全-创建API令牌)</br>
![!jira集成](../../img/system_management/jira服务集成.png){ width="900px" }


!!! ms-abstract ""
    第二步： 配置关联项目<br>
    在【项目设置-应用设置-缺陷管理】页面配置同步缺陷项目，填写正确的项目及缺陷类型。<br>【JIRA 项目 Key】：项目的关键字的需要在 JIRA 平台上进行查询。
![!jira关联](../../img/system_management/jira关联项目.png){ width="900px" }
![!jira项目](../../img/system_management/jira项目.png){ width="900px" }


!!! ms-abstract ""
    切换到【项目管理-模板管理】，勾选使用jira默认模板。在缺陷创建页面即可使用到 jira 的缺陷模板。
![!jira关联项目](../../img/system_management/项目管理使用jira模板.png){ width="900px" }


!!! ms-abstract ""
    第三步：添加个人平台账号。<br>
    点击【个人信息-第三方平台账号】配置jira账号，创建缺陷同步可使用该账户信息。
![!jira关联第三方帐号](../../img/system_management/个人信息绑定.png){ width="900px" }


!!! ms-abstract ""
    以上配置完成后，在 Metersphere 【缺陷管理】模块，可以创建并同步jira 平台的缺陷。

![!同步缺陷](../../img/system_management/%E5%88%9B%E5%BB%BA%E7%BC%BA%E9%99%B7%E4%BD%BF%E7%94%A8jira%E6%A8%A1%E6%9D%BF.png){ width="900px" } 

### 4.2 与禅道集成
!!! ms-abstract ""

!!! ms-abstract ""
    插件上传后，到【系统设置-系统-服务集成】可以看到禅道集成配置项。点击【编辑】按钮配置禅道集成信息。</br>
    第一步：填写对接 禅道 的地址、账号、请用方式、启停用开关。 填写完成后可以校验连接是否通过。</br>
    注意：禅道目前存在 GET 和 PATH_INFO 两种接口调用方式（即其requestType 参数）对于禅道接口的调用使用的是 PATH_INFO 方式和 GET 请求方式的支持，用户可以根据自己使用的禅道系统的配置情况自主选择请求方式。
![!禅道集成](../../img/system_management/禅道服务集成.png){ width="900px" }


!!! ms-abstract "说明"
	1. 账号密码为具有相应权限的 Zentao 账号，账号需要具有超级 model 调用接口权限。
    2. 请求方式：在禅道里具体查看：参考禅道配置文件中$config->requestType 的值；配置文件参考路径：/opt/zbox/app/zentao/config/my.php 。
	3. 如果提示因为安全问题 api 禁用，需要修改禅道服务器配置文件/opt/zbox/app/zentao/config/my.php，加上 '$config->features->apiGetModel = true;' 这个配置。


!!! ms-abstract ""
    第二步： 关联项目配置<br>
    在【项目设置-应用设置-缺陷管理】页面配置同步缺陷项目，填写正确的禅道项目。<br>
    【Zentao（禅道）项目 ID】：如果 禅道 bug 是附属在项目上，则关联的Zentao ID 为项目 ID；如果 禅道 Bug 是附属在产品上，则关联的 ZentaoID 为产品 ID。
![!禅道-马上关联项目](../../img/system_management/配置禅道缺陷模板.png){ width="900px" }

!!! ms-abstract ""
    切换到【项目管理-模板管理】，勾选使用 禅道 默认模板。在缺陷创建页面即可使用到 禅道 的缺陷模板。
![!jira关联项目](../../img/system_management/禅道缺陷模板.png){ width="900px" }


    

!!! ms-abstract ""
    第三步：添加个人平台账号<br>
    点击【个人信息-第三方平台账号】配置 禅道 账号，创建缺陷同步可使用该账户信息。<br>
    【注意】该信息为通过禅道提交缺陷的用户名、密码，若未填写，则使用组织中配置的默认信息。<br>
  
![!jira关联第三方帐号](../../img/system_management/禅道账号绑定.png){ width="900px" }

!!! ms-abstract ""
    以上配置完成后，在 Metersphere 【缺陷管理】模块，可以创建并同步禅道平台的缺陷。
 ![!禅道-相关需求](../../img/system_management/使用禅道缺模板创建缺陷.png){ width="900px" }

<!--
### 2.4 与Azure Devops集成
!!! ms-abstract ""
    第一步：服务集成配置。<br>
    填写【Basic Auth 账号信息】后，点击【测试连接】即可 
![!禅道-马上关联项目](../../img/system_management/Azure配置项目.png){ width="900px" }

!!! ms-abstract ""
    第二步： 关联项目配置
    配置完服务集成后，还需要配置项目中引用禅道项目的设置，即关联项目。点击页面右下角的【马上关联项目】进行设置。 <br>
![!禅道-马上关联项目](../../img/system_management/Azure-马上关联项目.png){ width="900px" }

!!! ms-abstract ""
    跳转到【项目管理】，点击【编辑】，编辑项目里【集成第三方平台】、【AzureDevops项目ID】、【AzureDevops过滤ID】，以及缺陷模板等相关信息。 <br>
![!禅道-禅道项目ID](../../img/system_management/Azure-Azure项目ID.png){ width="900px" }

!!! ms-abstract ""
    第三步：添加个人平台账号<br>
    点击服务集成页面右下角的【马上添加】进行设置。
![!禅道-马上添加](../../img/system_management/Azure-马上添加.png){ width="900px" }

!!! ms-abstract ""
    选择【第三方平台账号】设置【AzureDevops 信息】，如果不设置个人平台账号，则使用 MeterSphere 提交缺陷的用户，此缺陷推送到配置的服务平台上账号都是服务配置中设定的账号信息。 <br>
![!禅道-第三方平台账号](../../img/system_management/Azure-第三方平台账号.png){ width="900px" }

!!! ms-abstract ""
    以上配置完成后，在 Metersphere 系统中测试用例里，就可以关联 AzureDevops 的相关需求。 <br>
![!禅道-相关需求](../../img/system_management/Azure-关联需求.png){ width="900px" }

!!! ms-abstract ""
    在缺陷管理提交缺陷后，点击【同步按钮】，数据会同步到 AzureDevops 系统中。 <br>
![!禅道-同步需求](../../img/system_management/同步缺陷_Azure.png){ width="900px" }  -->

## 5 模板
!!! ms-abstract ""
    【系统设置-组织-模板】管理页面，支持对当前组织下使用的模板做全局配置，目前支持配置用例模板、缺陷模板。支持对模板做编辑、启用项目模板操作。</br>
    注意：启用项目模板后，系统模板不可再编辑。
![!模板](../../img/system_management/组织模板.png){ width="900px" }

### 5.1 用例模板
!!! ms-abstract ""
    - **编辑用例模板字段**<br>
    用例模板可以添加自定义的用例字段绑定到模板中。点击【字段设置】可以新增用例模板使用的字段。支持输入框、文本、单选、多选、复选、成员等字段。字段支持编辑、删除操作</br>

![!创建项目](../../img/system_management/组织模板新增字段.png){ width="900px" }



!!! ms-abstract ""
    - **编辑用例模板**<br>
        点击【模板】，可以给用例模板帮绑定自定义字段。系统用例模板默认只有一个且不可更改。</br>支持【关联字段】【新增字段】操作。添加自定义字段后，新建用例即可使用该字段。
![!创建项目](../../img/system_management/更新用例模板.png){ width="900px" }


### 5.2 缺陷模板
!!! ms-abstract ""
    - **编辑缺陷模板字段**<br>
    缺陷模板可以添加自定义的用例字段绑定到模板中。点击【字段设置】可以新增缺陷模板使用的字段。支持输入框、文本、单选、多选、复选、成员等字段。字段支持【编辑】【删除】操作</br>
![!创建项目](../../img/system_management/组织模板新增字段.png){ width="900px" }


!!! ms-abstract ""
    - **新增缺陷模板**<br>
        点击【模板】按钮，进入缺陷管理页面，点击【创建缺陷模板】按钮可新增缺陷模板，可以给用例模板帮绑定自定义字段。缺陷模板支持【编辑】【复制】【删除】操作</br>系统预置的默认模板不可删除。
       
![!创建项目](../../img/system_management/创建缺陷模板.png){ width="900px" }

!!! ms-abstract ""
    - **编辑缺陷模板**<br>
       当系统使用了第三方缺陷平台时，需要勾选 【对接第三方平台】，并绑定对应平台的缺陷字段及 API 字段才可使用。</br>支持【关联字段】【新增字段】操作。添加自定义字段后，新建缺陷使用该模板即可使用自定义字段。
![!创建项目](../../img/system_management/缺陷模板新增字段.png){ width="900px" }

!!! ms-abstract ""
    - **缺陷工作流设置**<br>
       可以定义缺陷流转状态。系统预置了一个工作流模板。配置缺陷的开始状态和结束状态，可自定义编辑缺陷状态的流转模式。
![!创建项目](../../img/system_management/组织模板工作流状态.png){ width="900px" }



## 6  日志
!!! ms-abstract ""
   点击左侧【系统设置-组织-日志】进入日志界面，显示登录用户权限范围内的全部测试资源日志信息，并支持使用高级查询来快速查找相关日志。
![!配额管理](../../img/system_management/组织日志.png){ width="900px" }


## 7 任务中心
!!! ms-abstract ""
    点击左侧【系统设置-组织-任务中心】进入任务中心管理界面。<br>
    实时任务：支持查看当前接口用例、接口场景正在运行的任务状态。<br>
    定时任务：可创建测试定时执行任务
   ![任务中心](../../img/system_management/任务中心.png){ width="900px" }





