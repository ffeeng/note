

```html
<!DOCTYPE html>
<html lang="zh-cn">
<head></head>
<body onload="console.log('body onload')" onpageshow="console.log('onpageshow')" onpagehide="console.log('onpagehide')">

<script async src="b.js">
</script>

<script async  src="c.js">
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


- 执行顺序 
加载解析 script
先执行script 
页面显示DOM->DOMContentLoaded -> Body onload -> pageShow



`async` — Execute script when available, without blocking while fetching

  `defer` — Defer script execution

  `type` — Type of script

  ![image-20201026173635889](https://tva1.sinaimg.cn/large/0081Kckwgy1gk2vebcexaj31pi0ga7ag.jpg)

### 参考
- [html5规范](https://html.spec.whatwg.org/multipage/scripting.html#the-script-element)

