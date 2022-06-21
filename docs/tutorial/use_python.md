## 方案

Virtualenv是一个创建隔绝的Python环境的工具。Virtualenv创建一个包含所有必要的可执行文件的文件夹，用来使用Python工程所需的包。通过在MeterSphere持续测试平台所在宿主机上创建Virtualenv环境，安装第三方库，挂载进JMeter容器中，就可以实现在MeterSphere平台执行Python脚本时引入第三方库的操作。

## 实现步骤

### 1. 前提

MeterSphere所在宿主机已安装Python和Virtualenv工具。

安装virtualenv
```
pip install virtualenv
```

### 2. 具体步骤

① 进入MeterSphere所在节点，安装所需第三方包。

■ 注意：在同时安装了python2和python3的环境下，使用 virtualenv --copies . 创建的虚拟环境会是python3的，目前MS只支持python2，所以这里尽量使用python2 -m virtualenv 环境名来创建

安装第三方包
```
#创建virtualenv
#data目录为docker默认挂载路径，可将第三方包安装该目录下，若Metersphere实际安装路径为其他路径，则下面操作放在MS实际安装路径下
cd /opt/metersphere/data/
mkdir python
cd python/
virtualenv --copies .
source bin/activate

#安装第三方包，比如xpinyin
pip install requests -i https://pypi.tuna.tsinghua.edu.cn/simple
#查看是否安装成功，是否有生成相应目录
ll lib/python2.7/site-packages/
```

② 前台编写Python前后置脚本，并进行验证。

脚本示例
```
import sys
#注意：此路径容器内部的映射路径，为固定值
sys.path.append("/opt/metersphere/data/python/lib/python2.7/site-packages")

import requests

res = requests.get("https://www.baidu.com")
log.info("==========debug==========")
log.info(res.text)
```
![](../img/tutorial/use_python/use_python_1.png)
![](../img/tutorial/use_python/use_python_2.png)