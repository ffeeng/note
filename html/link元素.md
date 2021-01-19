[TOC]
## 用法
```html
<link rel=preload as=style href=css/chunk-vendors.793ef94c.css >
<link rel=prefetch href=css/LiveRoom.b34e7a1d.css >
<link rel="dns-prefetch" href="https://cdn.bootcss.com">
<link rel="preconnect" href="https://cdn.domain.com" crossorigin>
```

## preload 
它专注于当前的页面，并以高优先级加载资源

## prefetch
专注于下一个页面将要加载的资源并以低优先级加载，空闲时下载

## dns-prefetch
DNS prefetching 允许浏览器在用户浏览页面时在后台运行 DNS 的解析。

## preconnect
preconnect 允许浏览器在一个 HTTP 请求正式发给服务器前预先执行一些操作，
这包括 DNS 解析，TLS 协商，TCP 握手，这消除了往返延迟并为用户节省了时间。

## prerendering
Prerendering 和 prefetching 非常相似，它们都优化了可能导航到的下一页上的资源的加载，区别是 prerendering 在后台渲染了整个页面，整个页面所有的资源。


## 注意
- vue-cli默认开启prefetch preload
![image-20210119110920435](/Users/zego/Library/Application Support/typora-user-images/image-20210119110920435.png)


js和css会阻塞dom
## 参考文献
- [资源提示 —— 什么是 Preload，Prefetch 和 Preconnect](https://juejin.cn/post/6844903646996480007)
- [whatwg link元素](https://html.spec.whatwg.org/multipage/links.html#linkTypes)
- [更快地构建 DOM: 使用预解析, async, defer 以及 preload](https://juejin.cn/post/6844903497033318414)
- [页面资源优化之preload、prefetch](https://juejin.cn/post/6908344595998998542)


