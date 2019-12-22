---
title: Vue cli3 解决跨域问题
date: 2019-12-19 23:57:56
tags:
---

## 主要内容

如果前端应用和后端 API 服务器没有运行在同一个主机上，需要在开发环境下将 API 请求代理到 API 服务器。这个问题可以通过 **vue.config.js** 中的 **devServer.proxy** 选项来配置。

**devServer.proxy** 可以是一个指向开发环境 API 服务器的字符串
 
```JavaScript
module.exports = {
  devServer: {
    proxy: 'http://192.168.6.20:4000'
  }
}
```

这会告诉开发服务器将任何未知请求 (没有匹配到静态文件的请求) 代理到 
**http://192.168.6.20:4000**。

## 应用场景

在四个爪爪工作时和后端配合开发爪爪令牌web版本，前端用的vue3.0。后端在开发服务器部署好接口，这时我在本地开发直接请求url会提醒跨域，无法正常完成请求。此时在Vue Cli3 的 配置中添加代理即可解决。

## 参考资料

Vue Cli3文档：[https://cli.vuejs.org/zh/config/#devserver-proxy](https://cli.vuejs.org/zh/config/#devserver-proxy)








