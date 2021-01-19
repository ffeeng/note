[TOC]

## 规范
- URLSearchParams属于URL标准规范，浏览器和node都支持
```web-idl
[Exposed=(Window,Worker)]
interface URLSearchParams {
  constructor(optional (sequence<sequence<USVString>> or record<USVString, USVString> or USVString) init = "");

  undefined append(USVString name, USVString value);
  undefined delete(USVString name);
  USVString? get(USVString name);
  sequence<USVString> getAll(USVString name);
  boolean has(USVString name);
  undefined set(USVString name, USVString value);

  undefined sort();

  iterable<USVString, USVString>;
  stringifier;
};
```

## 用法
### 传字符串
```js
let url = '?name=feng&hobby=sing&hobby=read'
let params = new URLSearchParams(url);
console.log(params.get('name'))
console.log(params.get('hobby'))
console.log(params)
console.log(params.toString())
/** 输出结果
feng
sing
URLSearchParams { 'name' => 'feng', 'hobby' => 'sing', 'hobby' => 'read' }
name=feng&hobby=sing&hobby=read
**/
```

### 传对象
```js
let url = {name:'feng',hobby:['sing','read']}
let params = new URLSearchParams(url);
console.log(params.get('name'))
console.log(params.get('hobby'))
console.log(params)
console.log(params.toString())
/** 输出结果
feng
sing,read
URLSearchParams { 'name' => 'feng', 'hobby' => 'sing,read' }
name=feng&hobby=sing%2Cread   -->decodeURIComponent('%2C')===','
**/
```

### 传数组
```js
let url = [['name','feng'],['hobby',['sing','read']]]
let params = new URLSearchParams(url);
console.log(params.get('name'))
console.log(params.get('hobby'))
console.log(params)
console.log(params.toString())
/** 输出结果
feng
sing,read
URLSearchParams { 'name' => 'feng', 'hobby' => 'sing,read' }
name=feng&hobby=sing%2Cread   -->decodeURIComponent('%2C')===','
**/
```
### 注意
当使用字符串为构造函数时： 字符串必须是问号开头或者没有问号	

## 源码
[node实现](https://github.com/nodejs/node/tree/master/lib/internal)

## 参考
- [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/URLSearchParams?a=1607151405934)
- [url规范](https://url.spec.whatwg.org/#urlsearchparams)

