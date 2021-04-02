

## 正确处理异常方式

```javascript
<script>
  window.addEventListener('error', e => {
    var stack = e.error.stack;
    var message = e.error.toString();

    if (stack) {
      message += "\n" + stack;
    }

    var xhr = new XMLHttpRequest();
    xhr.open("POST", "/log", true);
    // Fire an Ajax request with error details
    xhr.send(message);
  });
  
</script>
```

## vue中异常处理

```javascript
Vue.config.errorHandler = function (err, vm, info) {
  // handle error
  //`err`是js错误栈信息，可以获取到具体的js报错位置。
  //`vm` vue实例
  //`info` 是 Vue 特定的错误信息，比如错误所在的生命周期钩子
  // 只在 2.2.0+ 可用
   if (vm) {
        var componentName = formatComponentName(vm);
        //调用错误日志收集接口
    } else {
        //调用错误日志收集接口
    }
}

function formatComponentName(vm) {
    if (vm.$root === vm) return 'root';
    var name = vm._isVue
        ? (vm.$options && vm.$options.name) ||
        (vm.$options && vm.$options._componentTag)
        : vm.name;
    return (
        (name ? 'component <' + name + '>' : 'anonymous component') +
        (vm._isVue && vm.$options && vm.$options.__file
            ? ' at ' + (vm.$options && vm.$options.__file)
            : '')
    );
}
```



## 参考

- [浏览器工作原理](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/)

new Array(100)