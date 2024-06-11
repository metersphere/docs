

##  1 内置 MOCK 函数

### 1.1 基础变量
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>布尔值</td>
            <td><b>@bool</b></td>
            <td>随机生成一个布尔值</td>
        </tr>
    </tbody>
</table>

### 1.2 字符串
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>字符池</td>
            <td><b>@character(pool)</b></td>
            <td>从字符串池返回随机的字符</td>
        </tr>
        <tr>
            <td>随机小写字符</td>
            <td><b>@character(pool)</b></td>
            <td>返回一个随机的小写字符</td>
        </tr>
        <tr>
            <td>随机大写字符</td>
            <td><b>@character('upper')</b></td>
            <td>返回一个随机的大写字符</td>
        </tr>
        <tr>
            <td>特殊符号</td>
            <td><b>@character('upper')</b></td>
            <td>返回一个随机的特殊符号</td>
        </tr>
        <tr>
            <td>字符串</td>
            <td><b>@string(1,10)</b></td>
            <td>从字符串池返回一个随机字符串，字符数1-10</td>
        </tr>
    </tbody>
</table>

### 1.3 个人信息
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>身份证号</td>
            <td><b>@idCard</b></td>
            <td>随机生成一个身份证号（生成的身份证号码并不一定是真实有效）</td>
        </tr>
        <tr>
            <td>随机小写字符</td>
            <td><b>@idCard(birth)</b></td>
            <td>指定月份身份证号，例：19990907（生成的身份证号码并不一定是真实有效）</td>
        </tr>
        <tr>
            <td>手机号</td>
            <td><b>@phoneNumber</b></td>
            <td>随机生成一个手机号（生成的手机号码并不一定是真实有效）</td>
        </tr>
    </tbody>
</table>

### 1.4 日期/时间
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>日期</td>
            <td><b>@date('yyyy-MM-dd')</b></td>
            <td>返回一个随机的日期字符串。例：1983-01-29</td>
        </tr>
        <tr>
            <td>时间</td>
            <td><b>@time('HH:mm:ss')</b></td>
            <td>返回一个随机的时间字符串。 例：20:47:37</td>
        </tr>
        <tr>
            <td>日期时间</td>
            <td><b>@dateTime('yyyy-MM-dd HH:mm:ss')</b></td>
            <td>返回一个随机的日期和时间字符串。例：1977-11-17 03:50:15</td>
        </tr>
        <tr>
            <td>当前日期时间</td>
            <td><b>@now('yyyy-MM-dd HH:mm:ss')</b></td>
            <td>返回当前日期字符串。例：2014-04-29 20:08:38</td>
        </tr>
    </tbody>
</table>

### 1.5 中文姓名
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>中文名</td>
            <td><b>@cfirst</b></td>
            <td>随机生成一个常见的中文名</td>
        </tr>
        <tr>
            <td>中文姓</td>
            <td><b>@clast</b></td>
            <td>随机生成一个常见的中文姓</td>
        </tr>
        <tr>
            <td>中文姓名</td>
            <td><b>@cname</b></td>
            <td>随机生成一个常见的中文姓名</td>
        </tr>
    </tbody>
</table>

### 1.6 英文姓名
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>英文名</td>
            <td><b>@first</b></td>
            <td>随机生成一个常见的英文名</td>
        </tr>
        <tr>
            <td>英文姓</td>
            <td><b>@last</b></td>
            <td>随机生成一个常见的英文姓</td>
        </tr>
        <tr>
            <td>英文姓名</td>
            <td><b>@name</b></td>
            <td>随机生成一个常见的英文姓名</td>
        </tr>
    </tbody>
</table>

### 1.7 中文文本
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>大段文本</td>
            <td><b>@cparagraph</b></td>
            <td>随机生成一段中文文本</td>
        </tr>
        <tr>
            <td>句子</td>
            <td><b>@csentence</b></td>
            <td>随机生成一个中文句子</td>
        </tr>
        <tr>
            <td>单字</td>
            <td><b>@cword</b></td>
            <td>随机生成一个汉字</td>
        </tr>
        <tr>
            <td>标题</td>
            <td><b>@ctitle</b></td>
            <td>随机生成一个中文标题</td>
        </tr>
    </tbody>
</table>

### 1.8 英文文本
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>大段文本</td>
            <td><b>@paragraph</b></td>
            <td>随机生成一段英文文本</td>
        </tr>
        <tr>
            <td>句子</td>
            <td><b>@sentence</b></td>
            <td>随机生成一个句子，第一个单词的首字母大写</td>
        </tr>
        <tr>
            <td>单词</td>
            <td><b>@word</b></td>
            <td>随机生成一个单词</td>
        </tr>
        <tr>
            <td>标题</td>
            <td><b>@title</b></td>
            <td>随机生成一个标题</td>
        </tr>
    </tbody>
</table>

### 1.9 web 变量
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>网址</td>
            <td><b>@url('http')</b></td>
            <td>随机生成一个http URL</td>
        </tr>
        <tr>
            <td>协议</td>
            <td><b>@protocol</b></td>
            <td>随机生成一个 URL 协议。例：http ftp</td>
        </tr>
        <tr>
            <td>域名</td>
            <td><b>@domain</b></td>
            <td>随机生成一个域名</td>
        </tr>
        <tr>
            <td>顶级域名</td>
            <td><b>@tld</b></td>
            <td>随机生成一个顶级域名。例：net</td>
        </tr>
        <tr>
            <td>邮件地址</td>
            <td><b>@email</b></td>
            <td>随机生成一个邮件地址</td>
        </tr>
        <tr>
            <td>IP 地址</td>
            <td><b>@ip</b></td>
            <td>随机生成一个IP地址</td>
        </tr>
    </tbody>
</table>

### 1.10 数字
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>自然数</td>
            <td><b>@natural</b></td>
            <td>返回一个随机的自然数</td>
        </tr>
        <tr>
            <td>1-100自然数</td>
            <td><b>@natural(1,100)</b></td>
            <td>返回一个随机的1-100的自然数（大于等于 1 的整数）</td>
        </tr>
        <tr>
            <td>整数</td>
            <td><b>@integer</b></td>
            <td>返回一个随机的整数</td>
        </tr>
        <tr>
            <td>1-100整数</td>
            <td><b>@integer(1,100)</b></td>
            <td>返回随机的1-100的整数</td>
        </tr>
        <tr>
            <td>浮点数</td>
            <td><b>@floatNumber( 1, 10, 2, 5 )</b></td>
            <td>返回一个随机的浮点数，整数1-10，小数部分位数的最小值2，最大值5</td>
        </tr>
        <tr>
            <td>整型数组</td>
            <td><b>@range(1,100,1)</b></td>
            <td>返回一个整型数组，参数分别：start：起始值，stop：结束值，step：步长</td>
        </tr>
    </tbody>
</table>

### 1.11 地区
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>区域</td>
            <td><b>@region</b></td>
            <td>随机生成一个（中国）大区。例：华北</td>
        </tr>
        <tr>
            <td>省份</td>
            <td><b>@province</b></td>
            <td>随机生成一个（中国）省（或直辖市、自治区、特别行政区）</td>
        </tr>
        <tr>
            <td>城市</td>
            <td><b>@city</b></td>
            <td>随机生成一个（中国）市</td>
        </tr>
        <tr>
            <td>地区</td>
            <td><b>@county</b></td>
            <td>随机生成一个（中国）县</td>
        </tr>
        <tr>
            <td>省份/市/县</td>
            <td><b>@county(true)</b></td>
            <td>随机生成一个（中国）县（带省市）。例：甘肃省 白银市 会宁县</td>
        </tr>
        <tr>
            <td>邮编</td>
            <td><b>@zip</b></td>
            <td>随机生成一个邮政编码</td>
        </tr>
    </tbody>
</table>

### 1.12 颜色
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>颜色</td>
            <td><b>@color</b></td>
            <td>随机生成颜色，格式为 '#RRGGBB'</td>
        </tr>
        <tr>
            <td>RGB</td>
            <td><b>@rgb</b></td>
            <td>随机生成颜色，格式为 'rgb(r, g, b)'</td>
        </tr>
        <tr>
            <td>RGBA</td>
            <td><b>@rgba</b></td>
            <td>随机生成颜色，格式为 'rgba(r, g, b, a)'</td>
        </tr>
        <tr>
            <td>HSL</td>
            <td><b>@hsl</b></td>
            <td>随机生成颜色，格式为 'hsl(h, s, l)'</td>
        </tr>
    </tbody>
</table>

### 1.13 正则表达式
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td>正则表达式</td>
            <td><b>@regexp</b></td>
            <td>根据正则表达式返回结果</td>
        </tr>
    </tbody>
</table>

### 1.14 函数
!!! ms-abstract ""
    函数基于 MOCK 类型添加函数，例：@email｜md5。
<table>
    <tbody>
        <tr>
            <th width="150px">名称</th>
            <th width="150px">函数含义</th>
            <th width="600px">是否需要输入</th>
        </tr>
        <tr>
            <td><b>md5</b></td>
            <td><b>md5加密</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>base64</b></td>
            <td><b>base64加密</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>unbase64</b></td>
            <td><b>base64解密</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>substr</b></td>
            <td><b>起止</b></td>
            <td>以此开始截取一定长度的字符串</td>
        </tr>
        <tr>
            <td><b>concat</b></td>
            <td><b>结尾字符串</b></td>
            <td>以此结尾的字符串</td>
        </tr>
        <tr>
            <td><b>lconcat</b></td>
            <td><b>开头字符串</b></td>
            <td>以此开头的字符串</td>
        </tr>
        <tr>
            <td><b>sha1</b></td>
            <td><b>sha1加密</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>sha224</b></td>
            <td><b>sha224加密</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>sha256</b></td>
            <td><b>sha256加密</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>sha384</b></td>
            <td><b>sha384加密</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>sha512</b></td>
            <td><b>sha512加密</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>lower</b></td>
            <td><b>字母小写</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>upper</b></td>
            <td><b>字母大写</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>length</b></td>
            <td><b>数据长度</b></td>
            <td></td>
        </tr>
        <tr>
            <td><b>number</b></td>
            <td><b>字符串转数字</b></td>
            <td></td>
        </tr>
    </tbody>
</table>

## 2 内置 JMeter 函数
### 2.1 变量
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__RandomFromMultipleVars}</b></td>
            <td>从由|分隔的一组变量的值中提取元素</td>
        </tr>
        <tr>
            <td><b>${__split}</b></td>
            <td>将字符串拆分为变量</td>
        </tr>
        <tr>
            <td><b>${__eval}</b></td>
            <td>计算变量表达式</td>
        </tr>
        <tr>
            <td><b>${__evalVar}</b></td>
            <td>计算存储在变量中的表达式</td>
        </tr>
        <tr>
            <td><b>${__V}</b></td>
            <td>评估变量名</td>
        </tr>
    </tbody>
</table>

### 2.2 编码
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__escapeHtml}</b></td>
            <td>使用 HTML 编码对字符串进行编码</td>
        </tr>
        <tr>
            <td><b>${__escapeXml}</b></td>
            <td>使用 XML 编码对字符串进行编码</td>
        </tr>
        <tr>
            <td><b>${__unescape}</b></td>
            <td>处理包含 Java 转义符的字符串（例如 \n 和 \t）</td>
        </tr>
        <tr>
            <td><b>${__unescapeHtml}</b></td>
            <td>解码 HTML 编码的字符串</td>
        </tr>
        <tr>
            <td><b>${__urldecode}</b></td>
            <td>解码 application/x-www-form-urlencoded 字符串</td>
        </tr>
        <tr>
            <td><b>${__urlencode}</b></td>
            <td>将字符串编码为 application/x-www-form-urlencoded 字符串</td>
        </tr>
    </tbody>
</table>

### 2.3 脚本
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__groovy}</b></td>
            <td>运行 Apache Groovy 脚本</td>
        </tr>
        <tr>
            <td><b>${__BeanShell}</b></td>
            <td>运行 BeanShell 脚本</td>
        </tr>
        <tr>
            <td><b>${__unescape}</b></td>
            <td>处理包含 Java 转义符的字符串（例如 \n 和 \t）</td>
        </tr>
        <tr>
            <td><b>${__javaScript}</b></td>
            <td>处理 JavaScript (Nashorn)</td>
        </tr>
        <tr>
            <td><b>${__jexl2}</b></td>
            <td>评估 Commons Jexl2 表达式</td>
        </tr>
        <tr>
            <td><b>${__jexl3}</b></td>
            <td>评估 Commons Jexl3 表达式</td>
        </tr>
    </tbody>
</table>

### 2.4 时间
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__time}</b></td>
            <td>以各种格式返回当前时间</td>
        </tr>
        <tr>
            <td><b>${__timeShift}</b></td>
            <td>返回各种格式的日期，并添加指定的秒/分钟/小时/天</td>
        </tr>
        <tr>
            <td><b>${__dateTimeConvert}</b></td>
            <td>将日期或时间从源格式转换为目标格式</td>
        </tr>
        <tr>
            <td><b>${__RandomDate}</b></td>
            <td>生成特定日期范围内的随机日期</td>
        </tr>
    </tbody>
</table>

### 2.5 属性
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__isPropDefined}</b></td>
            <td>测试属性是否存在</td>
        </tr>
        <tr>
            <td><b>${__property}</b></td>
            <td>读取属性</td>
        </tr>
        <tr>
            <td><b>${__P}</b></td>
            <td>读取属性（简写方法）</td>
        </tr>
        <tr>
            <td><b>${__setProperty}</b></td>
            <td>设置 JMeter 属性</td>
        </tr>
        <tr>
            <td><b>${__isVarDefined}</b></td>
            <td>测试变量是否存在</td>
        </tr>
    </tbody>
</table>

### 2.6 数字
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__counter}</b></td>
            <td>生成一个递增的数字</td>
        </tr>
        <tr>
            <td><b>${__intSum}</b></td>
            <td>添加 int 数字</td>
        </tr>
        <tr>
            <td><b>${__longSum}</b></td>
            <td>添加长数字</td>
        </tr>
        <tr>
            <td><b>${__Random}</b></td>
            <td>生成一个随机数</td>
        </tr>
    </tbody>
</table>

### 2.7 文件
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__StringFromFile}</b></td>
            <td>从文件中读取一行</td>
        </tr>
        <tr>
            <td><b>${__FileToString}</b></td>
            <td>读取整个文件</td>
        </tr>
        <tr>
            <td><b>${__CSVRead}</b></td>
            <td>从 CSV 分隔文件中读取</td>
        </tr>
        <tr>
            <td><b>${__XPath}</b></td>
            <td>使用 XPath 表达式从文件中读取</td>
        </tr>
        <tr>
            <td><b>${__StringToFile}</b></td>
            <td>将字符串写入文件</td>
        </tr>
    </tbody>
</table>

### 2.8 信息
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__digest}</b></td>
            <td>生成摘要（SHA-1、SHA-256、MD5...）</td>
        </tr>
        <tr>
            <td><b>${__threadNum}</b></td>
            <td>获取线程组号</td>
        </tr>
        <tr>
            <td><b>${__threadGroupName}</b></td>
            <td>获取线程组名称</td>
        </tr>
        <tr>
            <td><b>${__samplerName}</b></td>
            <td>获取采样器名称（标签）</td>
        </tr>
        <tr>
            <td><b>${__machineIP}</b></td>
            <td>获取本机IP地址</td>
        </tr>
        <tr>
            <td><b>${__machineName}</b></td>
            <td>获取本地机器名</td>
        </tr>
        <tr>
            <td><b>${__TestPlanName}</b></td>
            <td>返回当前测试计划的名称</td>
        </tr>
    </tbody>
</table>

### 2.9 字符串
<table>
    <tbody>
        <tr>
            <th width="300px">变量</th>
            <th width="600px">说明</th>
        </tr>
        <tr>
            <td><b>${__log}</b></td>
            <td>记录（或显示）一条消息（并返回值）</td>
        </tr>
        <tr>
            <td><b>${__logn}</b></td>
            <td>记录（或显示）一条消息（空返回值）</td>
        </tr>
        <tr>
            <td><b>${__threadGroupName}</b></td>
            <td>获取线程组名称</td>
        </tr>
        <tr>
            <td><b>${__RandomString}</b></td>
            <td>生成一个随机字符串</td>
        </tr>
        <tr>
            <td><b>${__UUID}</b></td>
            <td>随机生成一个 UUID</td>
        </tr>
        <tr>
            <td><b>${__char}</b></td>
            <td>从数字列表生成 Unicode 字符值</td>
        </tr>
        <tr>
            <td><b>${__changeCase}</b></td>
            <td>根据不同模式更改大小写</td>
        </tr>
        <tr>
            <td><b>${__regexFunction}</b></td>
            <td>使用正则表达式解析先前的响应</td>
        </tr>
    </tbody>
</table>
