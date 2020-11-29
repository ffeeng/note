### webpack调试

- 在配置文件webpack.config.js中插入断点

```
let path = require('path');
debugger;
module.exports = {
    mode: 'development',
    entry: './src/index.js',
    output: {
        filename: "bundle.js",
        path: path.resolve(__dirname, 'build'),  //绝对路径
    }
}
```

- 执行如下命令

```
node --inspect-brk ./node_modules/webpack/bin/webpack.js --inline --progress
```

- 打开Chrome浏览器，地址栏里输入chrome://inspect/#devices：

![webpack调试](C:\Users\94963\Desktop\note\img\webpack调试.jpg)