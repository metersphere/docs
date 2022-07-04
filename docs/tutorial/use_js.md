■ 注意: js 代码都是在前置或者后置脚本中，脚本类型选择 javascript

## 使用本地 js
!!! info "引用本地 js 流程："
    1.将js文件上传到服务器 /opt/metersphere/data/xx.js <br>
    2.在前置或者后置脚本中写入 load(“/opt/metersphere/data/xx.js”)，即可使用js文件中的方法

## 使用网上 js
js 代码(以加密为例)
```
g = new Packages.org.mozilla.javascript.tools.shell.Global(Packages.org.mozilla.javascript.Context.getCurrentContext());
this.load = g.load;
load("https://cdn.bootcdn.net/ajax/libs/crypto-js/4.0.0/crypto-js.min.js");
var var1=CryptoJS.MD5("metersphere");
log.info("===111=== "+var1);
```

![](../img/tutorial/use_js/use_js_1.png)
![](../img/tutorial/use_js/use_js_2.png)

