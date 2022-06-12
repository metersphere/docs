## 1 目的
MeterSphere的接口测试、性能测试均基于JMeter实现，且兼容JMeter中的函数。在使用MeterSphere做接口测试、准备测试数据时，经常需要使用JMeter函数构造生成接口测试的测试数据。数据准备过程中经常需要查看摸索JMeter函数的使用范围方法，为了备忘、便于查看，也为了让大家减少一些探究试验的时间，本文将对这部分内容做出总结和演示，希望对大家有所帮助。

## 2 JMeter函数的设置使用
在MeterSphere平台，JMeter函数可在接口、接口用例的请求参数的QUERY参数、REST参数、请求体、前置操作脚本、后置操作脚本中设置使用。

### 2.1 常用的JMeter函数及示例
对于常用的JMeter函数可以百度查看JMeter官方文档，或搜索相关文章。<br>
函数调用的格式为：${__functionName(var1,var2,var3)} <br>
其中，_functionName 为函数名，括号内是函数的参数，无参数时可以不用括号，如 ${_UUID}。<br>
以下是常用的一些函数及使用示例。<br>
<table>
  <td bgcolor="#783887" align="middle" style="font-weight:bold;color: white">
   函数
  </td>
  <td bgcolor="#783887" align="middle" style="font-weight:bold;color: white">
   示例
  </td>
  <tbody>
    <tr>
        <td >__time 以多种格式返回当前时间</td>
        <td >${__time} //13位的毫秒级时间戳</td>
    </tr>
    <tr>
        <td >__counter 计数器函数</td>
        <td >${__counter(True,)} //每个线程分开计数</td>
    </tr>
    <tr>
        <td >__Random 返回指定最大值和最小值之间的随机整数</td>
        <td >${__Random(1,99, num)} //生成1到99之间的随机数</td>
    </tr>
    <tr>
        <td >__UUID 通用唯一标识符函数</td>
        <td >${__UUID} //生成uuid</td>
    </tr>
  </tbody>
</table>  

### 2.2 在请求参数中使用JMeter函数
在MeterSphere中，可以在请求参数的QUERY参数、REST参数、请求体、前后置脚本中引用使用JMeter函数，引用使用方法如下表以生成UUID函数为例所示。
<table>
  <td bgcolor="#783887" align="middle" style="font-weight:bold;color: white">
   引用使用
  </td>
  <td bgcolor="#783887" align="middle" style="font-weight:bold;color: white">
   使用方法及示例(假设函数为__UUID)
  </td>
  <tbody>
    <tr>
        <td >在请求参数之QUERY参数中引用</td>
        <td >${__UUID}</td>
    </tr>
    <tr>
        <td >在请求参数之REST参数中引用</td>
        <td >${__UUID}</td>
    </tr>
    <tr>
        <td >在请求参数之请求体中引用</td>
        <td >${__UUID}</td>
    </tr>
    <tr>
        <td >在请求参数之前后置BeanShell脚本中引用</td>
        <td >BeanShell注意事项 <br>
             1.每行须以分号结尾 <br>
             2.注释是// <br>
             uuid="${__UUID}"; <br>
             打印到控制台输出查看变量值，调试时用 <br>
             log.info("uuid="+uuid);
        </td>
    </tr>
    <tr>
       <td >在请求参数之前后置Python脚本中引用</td>
       <td >获取变量值<br>
            uuid="${__UUID}";<br>
            打印到控制台输出查看变量值，调试时用<br>
            log.info("uuid="+uuid);
       </td>
    </tr>
  </tbody>
</table>  

需要特别说明的是，在前置/后置脚本中也是可以引用使用JMeter函数的。

具体的使用方法：<br>
（1）在双引号内输入函数的调用方法，如图2-1所示； <br>
（2）以Python脚本中的引用为例，在“查询database列表接口用例”页面中，将以下脚本内容设置为前置脚本内容，如图2-1所示；<br>
（3）然后执行用例，在“控制台”的输出内容中能够看到打印出的uuid和time函数生成的时间戳，如图2-2所示。<br>
```
uuid="${__UUID()}";
strTime="${__time()}";
log.info("--------pre script begin-------------");
log.info("uuid="+uuid);
log.info("strTime="+strTime);
log.info("--------pre script end-------------");
```
![配置在前置脚本中使用JMeter函数地址](../img/tutorial/use_function/在前置脚本中使用JMeter函数.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-1 在前置脚本中使用JMeter函数</font><br>
![配置控制台输出JMeter函数地址](../img/tutorial/use_function/控制台输出JMeter函数.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-2 控制台输出JMeter函数</font><br>

### 2.3 在QUERY参数、REST参数中使用JMeter函数
在QUERY参数、REST参数中设置使用JMeter函数，具体操作方法为：<br>
1、在“接口用例”页面，在“请求参数”面板的“QUERY参数”选项卡中，选择如图2-3所示的铅笔图标“编辑”按钮，打开“参数设置”对话框，在对话框中选择设置并保存，如图2-4所示；也可以直接在在参数值的输入框输入“$”，之后从下拉JMeter函数列表中选择要使用的JMeter函数，如图2-5所示。<br>
2、设置之后，执行用例时，平台会通过JMeter函数生成的参数值发出请求。<br>
![配置选择打开【参数设置】对话框地址](../img/tutorial/use_function/选择打开【参数设置】对话框.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-3 选择打开【参数设置】对话框</font><br>
![配置参数设置-设置JMeter函数地址](../img/tutorial/use_function/参数设置-设置JMeter函数.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-4 参数设置-设置JMeter函数</font><br>
![配置参数设置-输入$在下拉列表中选择JMeter函数](../img/tutorial/use_function/参数设置-在下拉列表中选择JMeter函数.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-5 参数设置-输入$在下拉列表中选择JMeter函数</font><br>


### 2.4 具体场景演示示例
下面用InfluxDB写入接口测试场景演示变量和JMeter函数的使用。
```
#写入接口API curl调用
curl -i -XPOST 'http://10.1.13.12:8086/write?db=monitoringdb' --data-binary 'cpu_usage,host=10.1.10.131,app=dataease value=0.10 1632761023000000000'
#cpu_usage为measurement，类似关系数据库里的表, host为主机ID，app为dataease
```

操作步骤如下。之前的示例步骤比较详细，这里就只列出关键的步骤截图了。

（1）在【接口列表】页面，创建【InfluxDB写入接口】，请求协议为POST，路径为/write，如图2-6所示。

（2）在【CASE】页面，如图2-7所示，选择【+添加】打开【创建接口用例】页面，创建写入接口用例，如图4-5所示。

（3）根据curl命令我们可以看到需要设置QUERY参数db，以及请求体raw内容。

如图2-8所示，设置QUERY参数db，设置值使用环境变量${dbname}，dbname变量已在环境中设置，并设置值为monitoringdb。

如图2-9所示，设置请求体，格式选择raw，内容设置为 cpu_usage,host=${_UUID},app=dataease value=${usage} ${_time()}000000 

使用JMeter函数_UUID做为host ID，使用_time函数生成13位的时间戳，使用usage变量，usage变量在前置脚本中使用python random函数计算，保存在usage变量中。

![配置创建写入接口地址](../img/tutorial/use_function/创建写入接口.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-6 创建写入接口</font><br>
![配置选择创建写入接口用例地址](../img/tutorial/use_function/选择创建写入接口用例.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-7 选择创建写入接口用例</font><br>
![配置设置QUERY参数db地址](../img/tutorial/use_function/设置QUERY参数db.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-8 设置QUERY参数db</font><br>
![配置设置请求体-监控数据地址](../img/tutorial/use_function/设置请求体-监控数据.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-9 设置请求体-监控数据</font><br>
![配置设置前置python脚本-生成usage并保存到变量地址](../img/tutorial/use_function/设置前置python脚本-生成usage并保存到变量.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-10 设置前置python脚本-生成usage并保存到变量</font><br>

（4）保存并执行用例，在【响应内容】下【请求内容】中查看请求内容POST data，如图2-11所示，可以看到使用JMeter函数生成的数值以及python random函数生成的值。

cpu_usage,host=e48222aa-e98e-4974-8dfb-df9a1aecc4cc,app=dataease value=0.00309123923176 1652670605313000000 <br>
![配置查看请求内容地址](../img/tutorial/use_function/查看请求内容.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图2-11 查看请求内容</font><br>

### 3 MockJS函数的设置使用
对于MockJS函数，在MeterSphere中，在请求参数的QUERY参数、REST参数值设置时使用。MockJS函数，请加参数设置页面中列表，如图2-13所示。可将MockJS设置到参数值中，在请求时，随机生成布尔值、自然数、整数、浮点数、字符、字符串、日期、时间、日期时间、当前时间等参数值，使用生成的参数值发出请求。<br>
需要注意的是，在请求体和前后置脚本中，不能使用MockJS函数，可以使用JMeter函数。
![配置选择打开【参数设置】对话框地址](../img/tutorial/use_function/选择打开【参数设置】对话框.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图3-1 选择打开【参数设置】对话框</font><br>
![配置参数设置-选择MockJS函数地址](../img/tutorial/use_function/参数设置-选择MockJS函数.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图3-2 参数设置-选择MockJS函数</font><br>

也可以直接在在参数值的输入框输入“@”，之后从下拉MockJS函数列表中选择要使用的MockJS函数，如图3-3所示。
![配置参数设置-输入@列出MockJS并选择](../img/tutorial/use_function/参数设置-列出MockJS并选择.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图3-3 参数设置-列出MockJS并选择</font><br>

以下通过一个创建接口用例设置参数值的场景演示一下具体的使用：<br>

如图3-4，在“接口用例”页面中，添加两个QUERY参数：一个键为“pretty”， 值为“@boolean”；一个键为“serverName”，值为“@date@time”。执行用例后，可在响应体的“请求内容”选项卡中查看这些函数生成的随机值，如图3-5的“请求内容”所示。

  * pretty的@boolean函数生成的是false。
  * serverName的@date@time函数生成的是gl8Im02011-12-2116:10:31

![配置MockJS函数(以@开头)地址](../img/tutorial/use_function/MockJS函数(以@开头).png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图3-4 MockJS函数(以@开头)</font><br>
![配置请求内容中查看函数输出地址](../img/tutorial/use_function/请求内容中查看函数输出.png){:height="100%" width="70%"} <br>
<font size=2 class="png-lable-span">图3-5 请求内容中查看函数输出</font><br>

## 4 总结
本文总结了MeterSphere中使用JMeter函数、MockJS函数的方法和注意事项，并通过具体的接口测试场景演示了JMeter函数和MockJS的使用，希望对大家有帮助。