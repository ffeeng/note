[TOC]

## 常用文件操作
- 读路径 fs.readdirSync(currentRoot)
- 文件或文件夹是否存在 fs.existsSync(distDir)
- 删除文件夹 fs.rmdirSync(distDir, { recursive: true })
- 创建文件夹 fs.mkdirSync(distDir)
- 读文件 fs.readFileSync(path, 'utf-8');
- 写文件 fs.writeFileSync(realFileName, fileContent, 'utf-8');
- 添加内容 fs.appendFileSync('a.txt','1234\r\n');

## 综合示例
```js
let ejs = require('ejs');
let fs = require('fs');

generatorCode(`${__dirname}/template`);

// 广度优先搜索遍历文件夹 生成代码
function generatorCode(currentRoot) {
  let distDir = currentRoot.replace('template', name);
  let dir = fs.readdirSync(currentRoot);
  if (fs.existsSync(distDir)) {
    fs.rmdirSync(distDir, { recursive: true });
  }
  fs.mkdirSync(distDir);

  for (let fileName of dir) {
    let path = `${currentRoot}/${fileName}`;
    let stats = fs.lstatSync(path);
    if (stats.isFile()) {
      let str = fs.readFileSync(path, 'utf-8');
      let fileContent = ejs.render(str, { name, Name, dto, util });
      let realFileName = `${distDir}/${fileName}`.replace('template', name).replace('.ftl', '.ts');
      fs.writeFileSync(realFileName, fileContent, 'utf-8');
    } else {
      generatorCode(`${currentRoot}/${fileName}`);
    }
  }
}

```

## express返回图片
```js
let fs = require('fs');
let buff = fs.readFileSync('1.jpg');
response.send(buff);
response.end();
console.log(a); 
```

