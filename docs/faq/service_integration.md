## 1 在禅道上已创建的缺陷，MS 上点击“同步缺陷”，未成功同步
禅道缺陷同步到 MS 是企业版功能，开源版只支持单向同步，只能 MS 缺陷同步到禅道上

## 2 禅道在 PATH_INFO 下，项目集成失败
禅道配置文件的请求方式与 MS 平台选择的请求方式不一致，修改禅道配置或 MS 平台设置，使禅道请求方式与 MS 平台保持一致
```
1.【修改禅道配置】配置文件路径：/opt/zbox/app/zentao/config/my.php，修改 $config->requestType = 'PATH_INFO' 或 'GET'，重启禅道/opt/zbox/zbox restart
2.【修改MS配置】在“系统设置-工作空间-服务集成-禅道”配置页面，选择请求方式为'PATH_INFO' 或 'GET'
```

## 3 MS 集成 TAPD，在 MS 平台上提交缺陷（上传图片），在 TAPD 中无法正确显示图片
TAPD 没有替 MS 平台当前站点配置问题，修改 MS 平台【系统设置-系统-系统参数设置-基本配置-当前站点URL】，需要配置成 https 的地址

## 4 MS 集成禅道，在 MS 平台上项目 ID 填写正确，检查时提示 “ID不存在或者其他错误”
造成原因:
```
1.没有对应产品或者项目的权限，或者有权限但是需要填产品 ID，结果填了项目 ID;
2.缺少配置 $config->features->apiGetModel
3.襌道里 api 超级调用模式有没有授权
```
解决方法:
```
1.在项目编辑弹框-项目ID 后有提示说明
2.在禅道安装路径中：${安装路径}/zentao/config/ 目录下创建一个 my.php 文件，然后在里面添加如下内容：$config->features->apiGetModel = true;
  注意：如果有 my.php，则直接在最下方添加 "$config->features->apiGetModel = true;"即可；添加完需要重启禅道服务器，/opt/zbox/zbox restart
3.禅道 web 端，【组织-权限-权限维护-API 接口】，勾选“超级model调用接口”即可
```
## 5 MS 集成 JIRA 平台，填写【JIRA项目key】后进行保存时，页面提示 "ID不存在或其他错误"
用户没有权限访问此项目，查看该项目的用户是否存在 MS 系统【系统设置-服务集成-JIRA】处配置的账号
![! JIRA](../img/faq/服务集成JIRA.png)