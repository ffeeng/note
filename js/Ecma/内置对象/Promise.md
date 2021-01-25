[TOC]
## 基本原理

<img src="/Users/zego/Library/Application Support/typora-user-images/image-20210124163439314.png" alt="image-20210124163439314" style="zoom:67%;" />

![img](https://mdn.mozillademos.org/files/8633/promises.png)

## 常用示例

```javascript
let a = [1, new Promise(resolve => resolve(2))];
console.log(await Promise.all(a));
console.log(await Promise.allSettled(a));
console.log(await Promise.resolve(1));
Promise.reject('reject').catch(console.error);
Promise.resolve('resolve').then(console.log);
Promise.resolve('resolve').finally(() => console.log('finally'));
console.log(await Promise.reject(1));
```
## 运行截图
![image-20210122115402356](/Users/zego/Library/Application Support/typora-user-images/image-20210122115402356.png)

## 方法特性
- Promise.all
有rejected就返回最先执行的rejected，否则按顺序登录所有fulfilled.
```javascript
let a = [
  new Promise(resolve => {
    setTimeout(() => {
      resolve(1);
    })
  }),
  Promise.resolve(2),
  4,
];
console.log(await Promise.all(a)); 
// 输出1 2 4

let a = [
  new Promise(resolve => {
    setTimeout(() => {
      resolve(1);
    })
  }),
  Promise.resolve(2),
  Promise.reject(3),
  4,
];
console.log(await Promise.all(a)); 
// 报错 3
```

- Promise.race
  返回最先执行的fulfilled或rejected的值
```javascript
let a = [
  new Promise(resolve => {
    setTimeout(() => {
      resolve(1);
    })
  }),
  Promise.resolve(2),
  Promise.reject(3),
  4,
];
console.log(await Promise.race(a));
// 输出 2
```
- Promise.allSettle
  返回按顺序返回所有promise的执行结果<br/>
  [ { status: 'fulfilled', value: 1 },
  { status: 'fulfilled', value: 2 }...]
```javascript
let a = [
  new Promise(resolve => {
    setTimeout(() => {
      resolve(1);
    })
  }),
  Promise.resolve(2),
  Promise.reject(3)
];
console.log(await Promise.allSettled(a));
// 输出
// [ { status: 'fulfilled', value: 1 },
//   { status: 'fulfilled', value: 2 },
//   { status: 'rejected', reason: 3 } ]
```


- Promise.any
  返回最先fulfilled的值,当所有都是rejected时返回Uncaught AggregateError: All promises were rejected
```javascript
let a = [
  new Promise(resolve => {
    setTimeout(() => {
      resolve(1);
    })
  }),
  Promise.reject(3),
  Promise.resolve(2)
];
console.log(await Promise.any(a));
// 输出 2
```


## 参考
- [MDN Promise](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Promise/A+](https://promisesaplus.com/)
- [ECMA Promise](https://tc39.es/ecma262/#sec-promise-objects)
