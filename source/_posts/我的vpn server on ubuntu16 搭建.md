title: 我的vpn server on ubuntu16 搭建
date: 2017-10-08 00:57:26
tags: []
categories: []
---
## **参考链接** 
我的主要参考uri：　*http://blog.csdn.net/hanshileiai/article/details/49205317*
我的次要参考uri：　*http://www.jianshu.com/p/a8d41e7dfbc6*
---
*网上讲这个内容的文章比较多，但我就喜欢这两篇，这样已经够了。*
*讲服务端的比较多，我就不原样搬砖了，说一下我以为需要注意的地方.*

### **服务端**

  + 关于　/etc/pptpd.conf中localip　
　  - 网上有很多教程是说指定为跟客户端统一网段，我这样配置没有成功。
    - 在我的例子中是　应该指定为服务器的外网网卡的局域网ip。
  + 关于开启1723端口
    - 以上主要参考uri链接文中没有详述
    - 其实应该是: 开启gre协议，并打开服务器47,1723号端口。使用VPN需要开启gre协议，而gre协议需要使用服务器的47和1723号端口,具体步骤如下
         ``` bash
         sudo iptables -A INPUT -p gre -j ACCEPT 
         sudo iptables -A INPUT -p tcp --dport 1723 -j ACCEPT   
         sudo iptables -A INPUT -p tcp --dport 47 -j ACCEPT
         ```
    详见我的次要参考链接　http://www.jianshu.com/p/a8d41e7dfbc6

  + 通过参考以上两个链接的参考，结合实际交互，基本能把服务端配置妥当。
  
  + 我配置服务端修改过得文件：
    - /etc/ppp/pptpd-option
    - /etc/ppp/chap-secrets
    - /etc/pptpd.conf 
    - /etc/sysctl.conf
    - /etc/ppp/chap-secrets


###### *行百里路半九十*

*在我的例子中,我的两台客户端pc都是ubuntu16.04，网络接入方式是wifi* 

### **客户端**
 
从图形界面中调出　* 网络连接 *　配置项框； 

  　+ 配置client　*vpn连接*　实例:
      - 点击右上角 '新增'
      - 选择 '以太网'
      - 选择　'点到点隧道协议（pptp）'
      - 点击 '新建'
      - 出现vpn选项表单，依次输入　'网关' ，'vpn　server'　中设置的客户 '用户名' 和 '密码' (根据情况选择密码记住或每次询问)
      - 选择 '高级按钮'
      - 勾选　'使用点到点加密'
      - 勾选　'允许有状态的加密'
      - 勾选　'发送ppp回响包'
      - 点击　'确定'
      - 点击　'保存'
    + 配置client　'WI-FI':
      - 选中自己要接入的wifi配置实例
      - 点击　'编辑' 按钮
      - 出现选项卡，当前选中的是　'WI-FI' 栏目
      - 选中常规栏目，选择　'使用此连接时自动连接vpn' 选项
      - 选择配置好的　'vpn' 项实例
      - 根据实际情况决定选择　'所有用户都可以使用这个连接'
      - 点解 '保存'　按钮
    + 收官
    　- 断开WI-FI连接
      - 重新连接该配置好的WI-FI实例
---      
**按照这么一路走来，'vpn server 应该时配置好了，如果有点啥出入，问google吧。当然也可以邮箱联系我 doc2git@yahoo.com **
      
