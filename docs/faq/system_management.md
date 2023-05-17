## 1 忘记了登录密码如何处理？
!!! ms-abstract ""
    当普通用户忘记密码，admin 管理员可在【系统设置-用户】为其重置密码。
    ![! JIRA自定义字段01](../img/faq/修改普通用户密码.png){ width="900px" }
    
    当系统管理员忘记密码且没有其他系统管理员账号时，需要通过数据库操作重置密码。

    * MeterSphere 的用户信息存放在数据库中的 `user` 表中，其中 password 字段为用户密码的 `md5` 值。

    ```sql
    update user set password='3259a9d7f208ef9690025d1432558c5b' where id='admin';
    ```
## 2 测试资源池的概念是什么？
!!! ms-abstract ""
    测试资源池相当于 MeterSphere 中的执行机集合，可以用于执行指定的接口或性能测试。目前支持添加 Node 资源池和 K8S 资源池，参考[资源池配置](../installation/build_node_controller.md)。

## 3 LDAP测试连接，提示 “用户不存在或者不唯一”
!!! ms-abstract ""
    可在【系统设置-系统参数设置-LDAP 设置】更改用户过滤器为 (cn={0})；LDAP属性映射为｛"username": "cn"｝

## 4 项目可以配置通用的域名吗?
!!! ms-abstract ""
    在【系统设置-工作空间-环境配置】页面，【通用设置】启用 Hosts，可以为项目配置通用的域名。

## 5 系统设置里面的“组织”为什么找不到了？
!!! ms-abstract ""
    为了给用户带来更好的使用体验，和更清晰的租户层级关系，在 1.14 版本中，“组织”模块以及相关菜单已被移除。

## 6 邮件服务器连接不成功
!!! ms-abstract ""
     导致邮箱链接不成功的原因可能是 465 端口未开放, 可在【系统设置-系统参数设置-邮件设置设置】将邮件设置中的 465 端口改成 25端 口并去掉 ssl 选项.

## 7 环境配置数据库连接不通， 提示WARN: Establishing SSL connection without server's identity verification is not recommended. 
!!! ms-abstract ""
    数据库默认开启了 SSL 验证相应的配置导致，可在【系统设置-环境管理】数据库的URL增加？useSSL=false 来解决。
    ![! 数据库配置](../img/faq/数据库配置1.png){ width="900px" }

## 8 在一个SQL请求下如何执行多条SQL
!!! ms-abstract ""
    在【系统设置-环境管理】编辑环境数据源配置的 url 后面加上 allowMultiQueries=true。


## 9 环境配置数据库配置提示：no database selected
!!! ms-abstract ""
    在【系统设置-环境管理】编辑环境数据源连接 url 没有拼接库名。需添加如：jdbc:mysql://127.0.0.1:3306/database

## 10 admin的系统管理员角色默认被误删怎么办？
!!! ms-abstract ""
    可使用 navicat 连接 metersphere 数据库执行插入管理员账号sql。<br >
    数据库连接默认账号:root/Password123@mysql
    ```
    INSERT INTO user_group (id, user_id, group_id, source_id, create_time, update_time)
    VALUES (UUID(), 'admin', 'admin', 'system', 1622183788364, 1622183788364);
    ```



