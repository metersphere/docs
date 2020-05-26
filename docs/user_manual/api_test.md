# 接口测试

​       传统的接口自动化测试大多借助第三方测试框架，以代码工程项目的形式实现，不利于管理和维护； MeterSphere 为了解决这个问题，开发了可视化接口自动化测试功能，只需要配置每个接口的入参和 断言，即可实现对接口的自动化测试，同时还开发了基于chrome浏览器的MeterSphere Recorder插件，方便录制场景以及快速导入场景，大大提升了接口测试的效率。

#### 首页

​        由测试、报告、测试日历三个部分组成，可快速了解到最近执行的测试内容以及整体的接口测试频次。

- ##### 测试：展示最近 5 次执行的接口测试

- ##### 报告：展示最近 5 次执行的接口测试所生成的报告

- ##### 测试日历：按时间维度展示接口测试执行的频次，颜色越深，代表使用频次越高

![image-20200526151627711](/Users/luoting/Library/Application Support/typora-user-images/image-20200526151627711.png)

#### 项目

​       对项目进行新增、修改、删除、查询操作

![image-20200526160337680](/Users/luoting/Library/Application Support/typora-user-images/image-20200526160337680.png)

- ##### 新增项目：点击“创建项目”，录入项目名称和描述

  ![image-20200526161235890](/Users/luoting/Library/Application Support/typora-user-images/image-20200526161235890.png)

- ##### 修改项目：选择要修改的项目，点击编辑按钮

  ![image-20200526161657718](/Users/luoting/Library/Application Support/typora-user-images/image-20200526161657718.png)

- ##### 删除项目：选择要删除的项目，点击删除按钮

  ![image-20200526161844214](/Users/luoting/Library/Application Support/typora-user-images/image-20200526161844214.png)

- ##### 查询项目： 查询全部项目选择“显示全部”，查询单个项目可以根据名称搜索

  ![image-20200526162045573](/Users/luoting/Library/Application Support/typora-user-images/image-20200526162045573.png)

#### 测试

​       对测试接口或接口集合进行新增、修改、删除、查询操作

- ##### 创建测试 ：点击创建测试，如图 5 步即可成功创建接口测试

  ![image-20200526164346609](/Users/luoting/Library/Application Support/typora-user-images/image-20200526164346609.png)

  - 场景配置：场景内的全局变量和请求头配置，作用域为场景内

    自定义变量：在场景配置中自定义变量的名称和值, 接口运行或者测试集合里面可以通过 ${BASE} 来访问当前场景下定义的全局变量

    ![image-20200526182004257](/Users/luoting/Library/Application Support/typora-user-images/image-20200526182004257.png)

    请求头：这里增加全局 header，可以在项目中设置全局 header 值

    ![image-20200526182452449](/Users/luoting/Library/Application Support/typora-user-images/image-20200526182452449.png)

  - 请求配置

    请求参数：接口 url 的查询字符串

    ![image-20200526183529482](/Users/luoting/Library/Application Support/typora-user-images/image-20200526183529482.png)

    请求头：http请求的header，作用域为请求内

    ![image-20200526184041858](/Users/luoting/Library/Application Support/typora-user-images/image-20200526184041858.png)

    请求内容：http 请求的 body 部分，如果http请求方式是 post, put 等请求方式时会有 请求内容 部分，形式有2种，分别是 键值对（form）、文本（json）

    ![image-20200526184241522](/Users/luoting/Library/Application Support/typora-user-images/image-20200526184241522.png)

    

    断言：断言支持文本、正则和响应时间三种方式

    ![image-20200526184822836](/Users/luoting/Library/Application Support/typora-user-images/image-20200526184822836.png)

    提取：支持从响应中提取返回值作为变量存储，作用域为场景内，提取方式为正则、JSONPath、XPath三种

    ![image-20200526190002190](/Users/luoting/Library/Application Support/typora-user-images/image-20200526190002190.png)

  

- ##### 修改测试：请求执行顺序和场景执行顺序支持拖拽调整

  ![拖拽效果](/Users/luoting/Documents/拖拽效果.gif)

- ##### 删除测试：点击测试-显示全部，选择要删除的测试，点击删除按钮

  ![image-20200526190751152](/Users/luoting/Library/Application Support/typora-user-images/image-20200526190751152.png)

- ##### 查询测试：查询全部测试，点击显示全部，查询单个测试可以根据名称搜索

  ![image-20200526191200568](/Users/luoting/Library/Application Support/typora-user-images/image-20200526191200568.png)

- ##### 执行测试：保存成功的测试点击“执行”按钮，编辑完成的测试也可以点击“保存并执行”按钮，页面将会跳转到当前测试的测试报告中。

  ![image-20200526191445792](/Users/luoting/Library/Application Support/typora-user-images/image-20200526191445792.png)

  ![image-20200526191647234](/Users/luoting/Library/Application Support/typora-user-images/image-20200526191647234.png)

- ##### 更多操作：

  暂未实现

  





#### 报告

