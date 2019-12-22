---
title: Vue项目优化技巧
date: 2019-12-17 22:19:04
tags: vue
---

#### 1. 按需加载组件库

在项目开发过程中，不可避免都会使用一些开源的组件库，如UI组件库：ant-design-vue/element-UI，工具库：moment.js等等。但项目使用某个库所有组件的概率也很低，如果把组件库全部引入势必会造成代码体积较大，用户加载时间较长的缺点。此时可以通过按需引入，避免引入很多未用到的资源，很多库的官方文档都会有按需引入的说明，例如 [ant-design-vue](https://www.antdv.com/docs/vue/introduce-cn/) 推荐使用 **babel-plugin-import** 进行按需引入。 