title: Todo-2017.10-week2
date: 2017-10-02 00:00:00
tags: [plan, todo, 2017, week2]
categories: [plan, todo, 2017]
---
+ **DONE** 跟进doc2git.com的审核，并完成其代替换　doc2git.github.io的操作。
　　
+ **DONE** 对doc2git.wang进行备案，并设置将其到我的 码市。

+ **DONE** 打电话问码云客服，为啥我现在不能push代码更新到码云repo.**

+ 恒创vps

``` 
**DONE** *doc2git.wang*　解析到　恒创上部署的 *doc2git.wang* 虚拟主机，
在其主页中用js重定向到 *gitee.com/doc2git* 。

**DONE**　实现定时更新 恒创上部署的 *doc2git.wang* 虚拟主机中的 主页, 
让其与　*gitee.com/doc2git*　大致同步，比如一天同步一次, 
因为会在window.onload 绑定的函数中重定向到　*gitee.com/doc2git*,
所以对同步的要求不高，适当同步即可，这对seo是有相当大影响的。

**DONE** 将 *get-bootstrap* 静态项目部署到恒创vps上，使用nginx代理。
规划在恒创vps上建立js,css,images静态资源站，
以供doc2git.github.io, gitee.com/doc2git/，
bootzee.com/mytemplates 由三方提供的由我开发并维护的页面等使用。
```


+ html-uri--relative2protocal
```
  - 实现　uriReplaceSrcList.js 中数组的一键　生成, 或者自动生成。
  - 完成　纯粹nodejs代码和命令行使用方式，以及"uriReplaceSrcList.js 中导入数组的一键　生成, 或者自动生成"的文档撰写。
```

+ **DONE** 脚本化实现快速同步github,码云,本地版本同步.
```
  **DONE** 本地git--bare库的创建;
  **DONE** github,码云,本地版本　三个uri添加到　git remote all 命令队列中;
```

+ repo中的双镜像处理
```
**DONE** 在我的hexo博客中将所有doc2git.com字符串改为doc2git.com；
在我在线及离线项目中添加doc2git.com，以及对应项目的码云镜像;
```

+ **DONE** 让　[git@github.com:doc2git/git-deployer](https://doc2git.com/doc2git/deployer.git) 更便于使用.

```
+   为以上项目简单写写README.md;
+   向宿主目录（git-deployer的上一级目录）中的 .gitignore文件中加入该项目文件名；
+   Bug:
    -   当本地分支不存在，但是remote映射all存在时,会报错：fatal: 远程 all 已经存在；
    -   需要尝试（尝试用git rebase）删除本地和远程repo中，
            带有myreponsitory（应为myrepository）字样的版本，
            这会导致前版本升级到新版本时，运行中出现报错：
            'mkdir: 无法创建目录"/home/myrepository/doc2git-bashrc.git": 没有那个文件或目录';
```

+ **DONE** 参照　[firefox插件开发](http://doc2git.com/2017/10/17/firefox%E6%8F%92%E4%BB%B6%E5%BC%80%E5%8F%91/)　写个最简单的firefox插件　*hello, world.*