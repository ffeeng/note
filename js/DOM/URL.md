[TOC]


## URL
### 规范
- URL属于标准规范，node和浏览器都支持

| 规范                                | 状态            | 描述        |
| :---------------------------------- | :-------------- | :---------- |
| [URL](https://url.spec.whatwg.org/) | Living Standard | WHATWG 规范 |


```IDL
[Exposed=(Window,Worker),
 LegacyWindowAlias=webkitURL]
interface URL {
  constructor(USVString url, optional USVString base);

  stringifier attribute USVString href;
  readonly attribute USVString origin;
           attribute USVString protocol;
           attribute USVString username;
           attribute USVString password;
           attribute USVString host;
           attribute USVString hostname;
           attribute USVString port;
           attribute USVString pathname;
           attribute USVString search;
  [SameObject] readonly attribute URLSearchParams searchParams;
           attribute USVString hash;

  USVString toJSON();
};
```
### 用法
- 常见用法
```javascript
let addr = new URL("https://developer.mozilla.org/en-US/docs/Web/API/URL_API?a=1&b=2&b=3");
console.log(addr);
console.log(addr.toJSON());
console.log(addr.toString());
console.log(addr.searchParams);
```
- 运行截图
![image-20210119162100426](https://tva1.sinaimg.cn/large/008eGmZEgy1gmt2w0m8w5j30i00ekjsv.jpg)

  

## URLSearchParams

### 规范
- URLSearchParams属于标准规范，浏览器和node都支持

| Specification                                                | Status          | Comment  |
| :----------------------------------------------------------- | :-------------- | :------- |
| [URLSearchParams](https://url.spec.whatwg.org/#urlsearchparams) | Living Standard | 初次定义 |
```IDL
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

### 用法
#### 传字符串
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

#### 传对象
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

#### 传数组
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

### 源码
[node实现](https://github.com/nodejs/node/tree/master/lib/internal)

## 参考
- [URL](https://developer.mozilla.org/zh-CN/docs/Web/API/URL/URL)
- [URL Living Standard](https://url.spec.whatwg.org/#constructors)
- [URLSearchParams](https://developer.mozilla.org/zh-CN/docs/Web/API/URLSearchParams?a=1607151405934)
- [URLSearchParams规范](https://url.spec.whatwg.org/#urlsearchparams)

