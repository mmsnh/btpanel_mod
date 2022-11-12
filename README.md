## 宝塔面板7.7安装脚本&优化补丁

**宝塔面板7.7优化版安装脚本**

优化：去除无用接口、减少无用代码执行、减少对于宝塔云端请求、去除面板广告等，保持面板干净清爽。

修复：兼容新版本面板运行环境、修复面板XSS高危漏洞。

* 原链接
```bash
wget -O install.sh http://f.cccyun.cc/bt/install_6.0.sh && bash install.sh
```
* 如果原链接无法访问
```bash
wget -O optimize.sh https://raw.githubusercontent.com/mmsnh/btpanel_mod/main/optimize_mod.sh && bash optimize.sh
```

**宝塔面板7.7一键优化补丁**

1.去除宝塔面板强制绑定账号

2.去除各种删除操作时的计算题与延时等待

3.去除创建网站自动创建的垃圾文件（index.html、404.html、.htaccess）

4.关闭未绑定域名提示页面，防止有人访问未绑定域名直接看出来是用的宝塔面板

5.关闭活动推荐与在线客服，去除首页企业版广告

6.去除自动校验文件与上报信息定时任务

7.去除面板日志与网站绑定域名上报

* 原链接
```bash
wget -O optimize.sh http://f.cccyun.cc/bt/optimize.sh && bash optimize.sh
```
* 如果原链接无法访问
```bash
wget -O optimize.sh https://raw.githubusercontent.com/mmsnh/btpanel_mod/main/optimize_mod.sh && bash optimize.sh
```
* 如果Ngnix创建的网站出现403 forbidden(保留网站创建的文件)
```bash
wget -O optimize.sh https://raw.githubusercontent.com/mmsnh/btpanel_mod/main/optimize_mod2.sh && bash optimize.sh
```

Credit @消失的彩虹海  
https://blog.cccyun.cn/post-433.html  
https://blog.cccyun.cn/post-431.html

**降级方法**

如果是官方版本使用脚本降级

*SSH运行命令，运行宝塔Linux工具箱
原链接
```bash
wget -O btpanel_tools.sh https://download.btpanel.cm/tools/btpanel_tools.sh && bash btpanel_tools.sh
```
如果原链接无法访问
```bash
wget -O btpanel_tools.sh https://raw.githubusercontent.com/mmsnh/btpanel_mod/main/btpanel_tools.sh && bash btpanel_tools.sh
```
输入14等待降级成功即可

*解锁专业版

进入路径www/server/panel/data，编辑plugin.json文件，点击替换按钮，搜索"endtime": -1替换为"endtime": 999999999999，搜索is_user_status，在后面一点找到 "ltd”: -1 和 "pro": -1 将这两个 -1 改为 0。保存后在面板设置中授权版本改成Pro

*ltd是企业版，pro是专业版，-1代表没授权，0代表专业版永久授权，然后点击保存按钮即可。

*防止宝塔会自动修复

打开宝塔离线模式

执行命令改变文件属性，命令如下
```bash
chattr +i /www/server/panel/data/plugin.json
```
解除命令（不想使用解锁版时操作）
```bash
chattr -i /www/server/panel/data/plugin.json
```
