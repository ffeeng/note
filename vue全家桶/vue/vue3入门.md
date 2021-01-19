# vue3入门

[TOC]

## 创建项目

###  通过vite创建项目

```bash
npm i -g create-vite-app
create-vite-app vue3-vite-demo
```

### 通过webpack创建项目

```bash
npm i -g @vue/cli
# 对于 Vue 3.x 的项目，需要使用 Vue CLI v4.5 以上的版本
# 查看vue-cli版本
vue -V 
vue create vue3-demo
```
- 用webpack创建的vue3项目，点击这里定位源文件

![image-20201121152730314](https://tva1.sinaimg.cn/large/0081Kckwgy1gkwtrxwt2zj32eq0gowjv.jpg)

## 插件机制

![image-20210115115236897](https://tva1.sinaimg.cn/large/008eGmZEgy1gmo8ndjal7j30jf0ifjur.jpg)

## vuex

- _context.config.globalProperties.$store = $store
- _context.provides.$store = $store

## vue-router

- _context.config.globalProperties.$router = $router
- _context.provides.Symbol([vue-router]: router) = $router  
- _context.provides.SymbolSymbol([vue-router]: route location) = routeLocation
- _context.components.RouterLink = RouterLink  
- _context.components.RouterView = RouterView

