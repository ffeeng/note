[TOC]
## 基本原理
- 字符串和字符串对象通过装箱和拆箱进行转换，
- 字符串对象是类数组，
- 字符串可以for of遍历，也可以数组下标访问
![image-20210125104224901](https://tva1.sinaimg.cn/large/008eGmZEgy1gmzqtd2oblj30bm0pyn09.jpg)

## 常用示例

### 创建
```javascript
console.log('ab')
console.log(new String('ab'))
console.log(String.fromCharCode(97, 98))
console.log(String.fromCodePoint(97, 98))
console.log(String.raw({raw: ['a','b','c']}, 1, 2))
```
### 编解码
```javascript
console.log("ab".charAt(0))
console.log("ab".charCodeAt(0))
console.log("ab".codePointAt(0))
```
### 修改
#### 大小写
```javascript
console.log("Ab".toLocaleLowerCase())
console.log("Ab".toLocaleUpperCase())
console.log("Ab".toLowerCase())
console.log("Ab".toUpperCase())
```
#### 替换
```javascript
console.log("aba".replace('a', '1'))
```
#### 填充 去空格
```javascript
console.log("ab".padEnd(5, '1'))
console.log("ab".padStart(5, '1'))
console.log(" A b ".trim()) /*? $.length */
console.log(" A b ".trimEnd())
```
#### 其他
```javascript
console.log(..."ab")
console.log("ab".concat('0'))
console.log("ab" + '0')
console.log("ab".normalize("NFC"))
console.log("ab".repeat(2))
console.log("ab".split(''))
```
### 判断 比较
```javascript
console.log("ab".endsWith('b'))
console.log("ab".startsWith('a'))
console.log("ab".includes('a'))
console.log("ab".localeCompare('ba'))
```
### 截取
```javascript
console.log("ab".slice(-2))
console.log("ab".substr(0, 2))
console.log("ab".substring(0, 2))
```
### 查询
```javascript
console.log("aba".match(/a/g))
console.log([..."aba".matchAll(/a/g)])
console.log("ab".indexOf('a'))
console.log("ab".lastIndexOf('a'))
console.log("ab".length)
console.log("ab".search('a'))
console.log("ab"[1])
```
### 显示
```javascript
console.log("Ab".toString())
console.log("ab".valueOf())
console.log([..."ab"[Symbol.iterator]()])
```
### html相关
```javascript
console.log("ab".anchor('a'))
console.log("ab".big())
console.log("ab".blink())
console.log("ab".bold())
console.log("ab".strike())
console.log("ab".italics())
console.log("ab".fixed())
console.log("ab".fontcolor('red'))
console.log("ab".fontsize(20))
console.log("ab".link('http://hao123.com'))
console.log("ab".small())
console.log("ab".sub())
```
## 运行截图
![image-20210125162136670](/Users/zego/Library/Application Support/typora-user-images/image-20210125162136670.png)


## 方法详解
### String.phototype.replace
  replace接收两个参数
1. 正则模式指定要替换的部分，
2. 替换逻辑函数
                 ![image-20210125173218028](https://tva1.sinaimg.cn/large/008eGmZEgy1gn02vigdz9j30eh03lwen.jpg)

### String.phototype.match
![image-20210125173858513](https://tva1.sinaimg.cn/large/008eGmZEgy1gn02vixso0j30gl028glo.jpg)



## 参考

- [MDN String](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String)
- [ECMA String](https://262.ecma-international.org/6.0/#sec-string-objects)
