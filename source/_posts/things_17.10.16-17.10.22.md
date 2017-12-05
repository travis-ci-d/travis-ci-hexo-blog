title: Todo-2017.10-week4
date: 2017-10-23 11:11:20
tags: [plan, todo, 2017 ]
categories: [plan, todo, 2017]
---
* 
完善我的博客中vue便签模块;
    
    **DONE**    让新的便签条目默认显示在最前面；
    
    **DONE**    添加功能:    
            **DONE**   加热(冷文本变热);
            **DONE**   降温(热文本变冷);
            **DONE**   移除(移除文本)； 
            
    **DONE**    最后一个操作的简要提示功能:
                
            **DONE**    监听 *加热*　并显示提示信息；
            **DONE**    监听 *降温*　并显示提示信息；
            **DONE**    监听 *移除*　并显示提示信息；
    **本地搜索**
        **DONE**   添加本地字符串搜索功能；
        **DONE**   添加本地正则搜索功能；
    
    **开发字典功能**
    
        +   开发本地词典UI；
        +   获取并探索api
            -   衔接yahoo翻译api;
            -   衔接金山翻译api;
            -   衔接百度翻译api;
            -   打通api和ui交互;
        +   优化
    +   回滚
        -   添加正反序热切换功能；
        -   添加历史命令回滚功能；
    -   对以上功能进行排版；
    -   让尽可能多的使用该便签，以发并修复现存在的其他问题和需要优化的地方；
    -   理顺该便签页优雅生成静态页面的自动化部署流程，以便部署到 *git　pages* 站点中去；
    -   合并我的博客的　*note-dev* 分支到　master分支;
    -   尝试将该便签项目移植为 *Firefox 插件*;
* 
尝试实现：　
    +    在产品原型搭建的初期，
    
        使用web组件,如:
```
            <head>
                <link rel="import" href="src/new.html">
            </head>
            <body>
                  ...           
            </body>
            <script>
                var lnk = document.querySelector('link[rel="import"]');
                var content = link.import;
                var aDomVariable = content.querySelector('aSelector');
            </script>
```
        的方式提取我要的部分，
        进行ui原型预览；
    +   尝试解决的问题：
            -   避免复制粘贴过程的琐碎；
            -   避免复制和粘贴后的修改及扩展问题；
            -   避免样式和css的跨域问题；
