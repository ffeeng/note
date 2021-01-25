[TOC]
## 基本原理
![image-20210125182101016](/Users/zego/Library/Application Support/typora-user-images/image-20210125182101016.png)

## 匹配模式
| 简写 |    全名    |
| :--: | :--------: |
|  g   |   global   |
|  I   | ignoreCase |
|  m   | multiline  |
|  u   |  unicode   |
|  y   |   sticky   |


|    字段    |              含义              |
| :--------: | :----------------------------: |
|   flags    |          匹配模式标识          |
|   Source   |        正则表达式的文本        |
|   dotAll   | `.` 是否要匹配新行（newlines） |
|   Global   |          是否全部匹配          |
| ignoreCase |         是否忽略大小写         |
| multiline  |        是否进行多行搜索        |
|  unicode   |      Unicode 功能是否开启      |
|   sticky   |       搜索是否是 sticky        |


## 方法详解
### RegExp.prototype[@@search]()
```javascript
"baba".search(/ab/)
//等同于
/ab/[Symbol.search]('baba')
```

### RegExp.prototype[@@split]()
```javascript
/b/[Symbol.split]('aba')
//等同于
"aba".split(/b/)
```

### RegExp.prototype[@@replace]()
```javascript
/b/[Symbol.replace]('aba',1)
//等同于
"aba".replace(/b/,1)
```

### RegExp.prototype[@@match]()
```javascript
/b/[Symbol.match]('aba')
//等同于
"aba".match(/b/)
```

### String.phototype.match
![image-20210125173858513](https://tva1.sinaimg.cn/large/008eGmZEgy1gn02vixso0j30gl028glo.jpg)

## 参考
- [MDN 正则入门](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)
- [MDN RegExp](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
- [ECMA RegExp](https://262.ecma-international.org/6.0/#sec-regexp-regular-expression-objects)
