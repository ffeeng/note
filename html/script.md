[TOC]

## 实例代码
```javascript
//a.js
alert('a.js async');
//b.js
alert('b.js defer');
```
```html
<!DOCTYPE html>
<html lang="zh-cn">
<head></head>
<body onload="console.log('body onload')" onpageshow="console.log('onpageshow')" onpagehide="console.log('onpagehide')">

<script async src="a.js">
</script>

<script defer  src="b.js">
</script>
<script>
    console.log('script');
</script>

<div>hello</div>
<script>
    document.addEventListener('DOMContentLoaded', (e) => console.log('DOMContentLoaded' + JSON.stringify(e)))
</script>
</body>
</html>
```
## async defer原理
`async` — Execute script when available, without blocking while fetching<br/>
`defer` — Defer script execution<br/>
`type` — Type of script<br/>
![image-20201026173635889](https://tva1.sinaimg.cn/large/0081Kckwgy1gk2vebcexaj31pi0ga7ag.jpg)

## 页面显示过程 
页面显示DOM->DOMContentLoaded -> Body onload -> pageShow


## 参考
- [html5规范](https://html.spec.whatwg.org/multipage/scripting.html#the-script-element)

