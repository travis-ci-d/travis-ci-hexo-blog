title: crawl 爬虫
date: 2017-09-27 20:33:29
tags: [crawl, 爬虫]
categories: []
---
title: crawl 爬虫
date: 2017-09-27 20:33:29
tags: [crawl, 爬虫]
---

{% blockquote, "node 爬虫, 目标DOM元素获取", "bootstrap3" %}
# 用到了 request iconv-lite cheerio debug async express mongoose ejs cron 等js模块；
实现了目标DOM元素获取。
# node 爬虫
url: https://github.com/doc2git/201704crawl
{% endblockquote %}


强大的傻瓜式wget爬虫命令：　
* 
我用得最早，用得最多的wget爬虫命令：　wget --mirror --convert-links http://example.com
* 
http://pkuwwt.github.io/linux/2015-09-26-all-the-wget-commands-you-should-know

我2017年10月最喜欢的命令：
　
* 
爬取制定页面及应用资源：
```
wget -page-requisites --span-hosts --convert-links --adjust-extension http://example.com/dir/file
wget -p -H -k -E http://example.com/dir/file
```