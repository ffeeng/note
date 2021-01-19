[TOC]
## 用法
 
```html
<meta charset="utf8">
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="ie=edge">
<meta name=generator content="Frontweaver 8.2">
<meta http-equiv="Refresh" content="20; URL=page4.html">

<!-- 根据浏览器的屏幕大小自适应的展现合适的效果 -->
<meta name="applicable-device" content="pc,mobile" />

<!-- 移动端 浏览器中页面将以原始大小显示，不允许缩放 -->
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />

<!-- 优先使用 IE 最新版本和 Chrome -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
//它必须显示在网页中除 title 元素和其他 meta 元素以外的所有其他元素之前。如果不是的话，它不起作用

<!-- iphone会把一串数字识别为电话号码，点击的时候会提示是否呼叫，屏蔽这功能则把telephone设置为no -->
<meta content="telephone=no" name="format-detection" />

<!-- iphone的私有标签，默认值为default（白色），可以定为black（黑色）和black-translucent（灰色半透明） -->
<meta content="black" name="apple-mobile-web-app-status-bar-style">

<!-- iphone设备的是有标签 允许全屏模式浏览，隐藏浏览器导航栏 -->
<meta content="yes" name="apple-mobile-web-app-capable" />

<!-- 全屏显示 -->
<meta content="yes" name="apple-touch-fullscreen" />

<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">

<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">

<!-- 屏蔽百度转码 -->
<meta http-equiv="Cache-Control" content="no-transform" />
<meta http-equiv="Cache-Control" content="no-siteapp" />

<!-- 定义网页简短描述 -->
<meta name="description" content="Cochemist">

<!-- 定义网页关键词 -->
<meta name="keywords" content="生物化学"> 

<!-- 定义网页的作者 -->
<meta name="author" content="sun_Annie">

<!-- 避免HTML页面缓存 -->
<meta http-equiv="pragma" content="no-cache" />
<meta http-equiv="cache-control" content="no-cache">
<meta http-equiv="expires" content="0">

<!-- 定义网页的缓存过期时间 -->
<meta http-equiv="expires" content="Sunday 26 October 2016 00:00 GMT">
//由于这是一个过去的日期，所以这个网页只要一打开，就会直接到网站服务器重新下载页面内容，而不是从cache调用。这是一种防止网页被cache缓存的措施。

```

## name
- 元数据名称
标准的name取值有
- application-name
- author
- description
- generator
- keywords
- referrer
- theme-color
- color-scheme


## http-equiv
-定义程序指令,控制浏览器的行为

| State                                                        | Keyword                   | Notes          |
| ------------------------------------------------------------ | ------------------------- | -------------- |
| [Content Language](https://html.spec.whatwg.org/multipage/semantics.html#attr-meta-http-equiv-content-language) | `content-language`        | Non-conforming |
| [Encoding declaration](https://html.spec.whatwg.org/multipage/semantics.html#attr-meta-http-equiv-content-type) | `content-type`            |                |
| [Default style](https://html.spec.whatwg.org/multipage/semantics.html#attr-meta-http-equiv-default-style) | `default-style`           |                |
| [Refresh](https://html.spec.whatwg.org/multipage/semantics.html#attr-meta-http-equiv-refresh) | `refresh`                 |                |
| [Set-Cookie](https://html.spec.whatwg.org/multipage/semantics.html#attr-meta-http-equiv-set-cookie) | `set-cookie`              | Non-conforming |
| [X-UA-Compatible](https://html.spec.whatwg.org/multipage/semantics.html#attr-meta-http-equiv-x-ua-compatible) | `x-ua-compatible`         |                |
| [Content security policy](https://html.spec.whatwg.org/multipage/semantics.html#attr-meta-http-equiv-content-security-policy) | `content-security-policy` |                |




## 参考文献
- [文档级元数据元素](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta)
- [meta元素规范](https://html.spec.whatwg.org/multipage/semantics.html#the-meta-element)


