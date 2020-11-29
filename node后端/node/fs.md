## node文件操作

```javascript
let fs = require('node后端/node/fs')

//没有就创建 写文件
// let res = fs.writeFileSync('a.txt','1234');
//没有就创建  追加文件内容
let res = fs.appendFileSync('a.txt','1234\r\n');
console.log(res);
```

