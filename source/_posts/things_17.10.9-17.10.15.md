title: Todo-2017.10-week3
date: 2017-10-09 00:00:00
tags: [plan, todo, 2017, 2017.10 week3]
categories: [plan, todo, 2017, 2017.10]
---
+ a-tag-collection
    +   编写一个简单的firefox demo,实现一下功能：
        -   当在任意a标签上右击鼠标时，弹出菜单中有一个我加入的"添加链接信息到数据库"；
        -   为该a标签绑定一个click事件
        -   弹出一个表单，有如下元件：
    
            >　text-input: innerText, href, hostPageUri(宿主页面);
        
            >　button-like: drop, reset, submit;
    +   将该多个a标签的以上text-input中的value存入数据库。
    +   将上一条中存入数据库的a标签信息，简洁的渲染到页面上，简单的样式还是要有的。

+   为我的blog以优雅的形式添加一个 "Getting Things Done" 单页;
+   **DONE** 部署在github,码云，码市的我的博客镜像;
　　    +   **DONE** 部署本地的三镜像同步;
　　    +   用nginx反向代理，原因:
　　        -   不用git仓库提供的CNAME　api是因为gitee没有提供该api接口；
　　        -   CNAME会被更新时会被覆盖，不便于同时使用同一版本master一键同步。
　　        到这三个镜像,配置好的可访问域名为:
　　        -   http://doc2git.com,     http://icccc.cc,        http://doc2git.com.cn,  http://doc2git.club;
　　        -   http://te.doc2git.com,  http://te.icccc.cc,     http://te.doc2git.com.cn;
　　        -   http://co.doc2git.com,  http://co.icccc.cc，    http://co.doc2git.com.cn
　　        -   http://hu.doc2git.com， http://hu.icccc.cc;     http://hu.doc2git.com.cn;
+   **　用vue开发firefox插件，这是一种尝试.**
        +   jquery操作dom那么方便，为什么还用vue?
            +   jquery作为操作dom的最佳实践，我并不排斥;
            +   我同时兼有:
                -   自己开发插件的诉求;
                -   加强vue工程能力的诉求;
        +   尝试最简单demo预计流程：
            -   尝试用vue按类名或者标签名获取dom元素
            -   如果上一步在实践中不好用,就用原生js获取dom元素,并为该元素添加唯一的不容易重名的id;
            -   编写vue实例，将vue实例挂载到上述有id的元素上;
        +   尝试让这种依赖搭配的开发更加优雅，更具通用性；
+   **  完成我的blog中　/todo-match-indigo 页面的适配开发。**    
+   **DONE**    把讲vuex简单demo的　[vuex2.0 基本使用(2) --- mutation 和 action](http://www.cnblogs.com/SamWeb/p/6543931.html) 读完，并且透彻理解。
+   **DONE**    在gitee.com注册vue2git账号，并兼容本地设置,开启　http:/vue2git.gitee.io pages 服务,放一组vuex　demos上去测试流程跑通.
    +   在vps上部署nginx上部署nginx重定向到vue2git.gitee.io;
    +   意义:
        -   实现vue静态资源的扩展性部署,可自定义url,
            而只让vps只在客户端没有缓存重定向的情况下转发;
        -   经我测试所知，${user}.gitee.io 与我的vps有　差不多的ping 值, 比${user}.coding.me, 
            ${user}.github.io都要快;
        -   充分利用公益资源；        