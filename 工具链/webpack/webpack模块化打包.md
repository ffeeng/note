# webpack模块化打包

```

function (modules) {
		//缓存以加载的模块 {id:module}  module={export:{},id:1,loaded：false}
        var installedModules = {};
        function __webpack_require__(moduleId) {
            if (installedModules[moduleId])
                var module = installedModules[moduleId] = {
                    exports: {},
                    id: moduleId,
                    loaded: false

                };
            modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);
            module.loaded = true;
            return module.exports;
        }
        __webpack_require__.m = modules;
        __webpack_require__.c = installedModules;
        __webpack_require__.p = "";
        return __webpack_require__(0);
    })
    (
        [ 
        //将模块代码包装成函数，并在require时执行，修改mudule.export的值
            (function (module, exports) {
                module.exports = function spread(callback) {
                    return function wrap(arr) {
                        return callback.apply(null, arr);
                    };
                };
            })
        ]
    )
```











