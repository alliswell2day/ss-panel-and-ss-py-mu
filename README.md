> 上周接触了ss-panel，发现搭建起来异常的麻烦，对新手来说，到处都是坑，因此写了本ss-panel一键安装脚本

---

# 效果
![](http://cdn.mmmxcc.cn/blog/20170509/191015542.png)
![](http://cdn.mmmxcc.cn/blog/20170509/191042466.png)
![](http://cdn.mmmxcc.cn/blog/20170509/191103228.png)

**Github：https://github.com/mmmwhy/ss-panel-and-ss-py-mu**

**示例网站：https://ss.feiyang.li/**

![](http://cdn.mmmxcc.cn/blog/20170509/215724204.png)

# 特点
- 前端使用最新[ss-panel v3](https://github.com/orvice/ss-panel)，稳定性和可管理行都有明显提高。
- 后端使用[shadowsocks-py-mu](https://github.com/fsgmhoward/shadowsocks-py-mu)，多用户版本，与前端完美对接。
- 过程全自动，所以可能碰到的坑都提前做好处理。
- 被墙掉的资源都换成了墙内资源，不会出现被卡死的情况了。

# 系统要求
建议CentOS7 X64，我用的是这个版本，目前在腾讯云，digitalocean，interserver上通过测试。
理论上：CentOS 6+ / Debian 7+ / Ubuntu 14.04 +  都可以，

![](http://cdn.mmmxcc.cn/blog/20170510/094150095.png)
# 一键安装脚本
- 登陆后运行：
```
screen -S ss
```
如果提示screen: command not found 命令不存在可以执行：`yum install screen` 或 `apt-get install screen`安装（如果网络掉线，可以重新连接，再执行 `screen -r ss` 就会看到你的ss-panel安装进程。）
- 安装脚本
```
wget -N --no-check-certificate https://raw.githubusercontent.com/mmmwhy/ss-panel-and-ss-py-mu/master/ss-panel_node.sh && chmod +x ss-panel_node.sh && bash ss-panel_node.sh
```

运行脚本后会出现脚本操作菜单，
## ss-panel和ss-node同时安装
选择并输入 1 

![](http://cdn.mmmxcc.cn/blog/20170509/214909086.png)



因为ss-panel依赖于mysql,php,nginx，使用lnmp一键安装包，点击任意键开始安装。
![](http://cdn.mmmxcc.cn/blog/20170510/102436162.png)

LNMP包编译时间较长，可以喝杯茶吃个饭。大约30分钟左右，安装结束，提示登陆IP即可查看网站

![](http://cdn.mmmxcc.cn/blog/20170510/102100972.png)

![](http://cdn.mmmxcc.cn/blog/20170510/101919599.png)

**默认账户：ss@feiyang.li**

**默认密码：feiyang**



进入ss-panel页面后，记得在**管理面板->节点管理->添加节点->输入节点信息**

![](http://cdn.mmmxcc.cn/blog/20170510/085511290.png)

之后回到用户面板，就可以使用了。

## 仅安装ss-panel
选择并输入 2 
出现的结果与1相同，只不过您vps上没有同时安装[ss-py-mu](https://github.com/fsgmhoward/shadowsocks-py-mu)
## 仅安装ss-node
选择并输入 3，用于新建节点。
先在网页增加节点信息，特别要记住这里的node_id，长这个样子的
![mark](http://cdn.mmmxcc.cn/blog/20170509/221038086.png)

输入相关信息，ip地址和域名（ss-panel的）都可以，但是需要加上**http:// 或者 https://** ，注意区分自己域名有没有ssl。否则可能出现用户使用记录无法推送的问题。

![](http://cdn.mmmxcc.cn/blog/20170509/221216262.png)

# 其他补充内容
- LNMP环境编译时间较长
- php依赖安装会花费较长时间，特别是在国内

![本页面停留时间较长](http://cdn.mmmxcc.cn/blog/20170510/101054745.png)

- mailgun账号需要自己申请，我那个只是举个例子。
- 基于[lnmp1.3稳定版](https://lnmp.org/)制作，兼容性非常好。
- [常见错误](http://feiyang.li/2017/05/03/ss-panel/index.html#常见错误)在这里查看
- 如果想设置更多的信息，请查看[安装教程全文](http://feiyang.li/2017/05/05/ss-panel-full/index.html)，本脚本和该教程内容完全一致。
- 关于[Google的bbr加速](http://feiyang.li/2017/05/05/ss-panel-full/index.html#谷歌BBR加速)，与本脚本可以通用，但是因为效果不明显(可能因为我们实验室网太烂了吧)，所以我没有加入。

---

第一次写脚本，还请多多指教~
