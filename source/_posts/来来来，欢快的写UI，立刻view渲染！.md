title: 来来来，欢快的写UI，立刻view渲染！
date: 2017-9-02 22:12:53
tags: [在线编辑UI, 即刻预览, 交互, 便捷测试,文档学习,教程学习,iframe跳转,iframe历史,工具,灵感]
categories: [工具,UI代码, 便捷测试]
---
# *在线编辑UI，即刻预览:*

## ** Version 1: ** 
  
  > link: *http://doc2git.com/edit-code-view--pad/*
  
  > state: *只是修复bug，基本上不加新功能*
  
  > inspiration: *Any html render*
  
### *特性:*
1. 
##### 文本框输入什么（html），显示框就渲染什么(html)。


---


## ** Version 2: ** 
  
  > link: *http://doc2git.com/source--hack--view/*
  
  > state: *正在利用闲余时间开发中*
  
  > view-intention: *Vue*
 
+ ### *特性:*
1. 
文本框输入什么（html），显示框就渲染什么(html)。
2. 
左侧iframe头部导航栏有键入uri, 转跳键入的ｕri, 浏览历史倒退和前进功能。
--- 
### *可能会实现:*
  + *第一屏尽可能多地用来显示干货内容*
    - navbar
    ###### 当左侧阅读源iframe的上边缘的style.top大于触碰到顶部导航条显示高度时，隐藏该顶部导航条;
    ###### 当左侧阅读源iframe的上边缘的style.top小于于触碰到顶部导航条显示高度时，现实该顶部导航条;
    - footer
    ###### 默认隐藏footer, footer将在暂时未定的某个滚动条s滚动到底部时显示；
    ###### footer将在暂时未定的某个滚动条s滚离底部高度ｙ时隐藏滚动条；
  + *考虑左边代码区域的渲染触发按钮能否优雅地放到接近或浮动与渲染输出区域的xy位置*
  + *加入可选的vim操作键功能*
---
## ** Version 3: **
  
  > link: *git@github.com:doc2git/inspiration-responsive-view.git*
  
  > state: *进入开发期*
  
  > inspiration: *boostrap*

### 构想:
1. 
上面是能让bootstrap，960等响应式设计开发独占全部屏幕的区域。
  + 考虑一个比优雅的实现方式，实现上边页面单独出现**html/css调试控制面板**
2. 
下面左边是参考源（设计图，实践较好的代码，或者ui界面）。
  + 关于尺寸的问题，用**transform:scale(arg)**或者类似的css属性来处理,使得该区域占较少的屏幕尺寸。
3. 
下面右边是实际的编码区,尝试确保阅读方便。
  + 输入便捷的问题，通过引用CodeMirror的vim模块实现。
　

  
  
