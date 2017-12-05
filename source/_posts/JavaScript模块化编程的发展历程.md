title: webpack1指南
date: 2017-10-02T08:18:29.349Z
tags: [JS模块化编程的发展历程,webpack1， 入门, 进阶, loader, 集成gulp--missed, jquery引入--missed, ts, vue   ]
categories: [gitbook释出]
---
# webpack1指南： https://www.gitbook.com/book/toobug/webpack-guide
#### 虽然webpack1渐渐远去，但有些精巧的小项目是基于webpack1构建的，个人觉得还是有必要熟悉一下。一是为了避免重复早车轮，二是为了深入了解一些经典实现思想（比如《非模块化文件打包》<gh-pages on github支持一个index.html文件,不提供同repo下的资源请求，我目前在摸索快速美观单页repo的高效部署； 又比如《UMD模块打包》，这里面有判断当前宿主js环境规范的经典实现， 编写跨规范js包可以直接拿来用；etc.）。
## 模块化： https://webpack.toobug.net/zh-cn/chapter1/
#### 原始时代： https://webpack.toobug.net/zh-cn/chapter1/ancient-times.html
#### 命名空间时代： https://webpack.toobug.net/zh-cn/chapter1/name-spacing-age.html
#### 模块化时代： https://webpack.toobug.net/zh-cn/chapter1/modular-age.html
## wepack入门： https://webpack.toobug.net/zh-cn/chapter2/
#### 入口文件： https://webpack.toobug.net/zh-cn/chapter2/entry-point.html
#### 非模块化文件打包：https://webpack.toobug.net/zh-cn/chapter2/non-moduler.html
#### AMD模块打包： https://webpack.toobug.net/zh-cn/chapter2/amd.html
#### Node模块和NPM： https://webpack.toobug.net/zh-cn/chapter2/node-modules-and-npm.html
#### UMD模块打包： https://webpack.toobug.net/zh-cn/chapter2/umd.html
## webpack进阶： https://webpack.toobug.net/zh-cn/chapter3/
#### CLI与API使用模式： https://webpack.toobug.net/zh-cn/chapter3/cli-api.html
#### 基本配置项： https://webpack.toobug.net/zh-cn/chapter3/config.html
#### 分片： https://webpack.toobug.net/zh-cn/chapter3/chunks.html
#### CommonChuncks插件： https://webpack.toobug.net/zh-cn/chapter3/common-chunks-plugin.html
#### 高级配置项： https://webpack.toobug.net/zh-cn/chapter3/advanced-config.html
## Loader
#### 使用Loader: https://webpack.toobug.net/zh-cn/chapter4/using-loaders.html
#### 常用Loader:
##### bundle-loader: https://webpack.toobug.net/zh-cn/chapter4/bundle-loader.html
##### exports-loader: https://webpack.toobug.net/zh-cn/chapter4/exports-loader.html
##### imports-loader: https://webpack.toobug.net/zh-cn/chapter4/imports-loader.html
##### expose-loader: https://webpack.toobug.net/zh-cn/chapter4/expose-loader.html
## 杂谈
#### TypeScript和Vue: https://webpack.toobug.net/zh-cn/chapter6/ts-and-vue.html
##### 信息提供： https://www.gitbook.com/book/toobug/webpack-guide