[TOC]
## 常用方法
![image-20210120163827786](https://tva1.sinaimg.cn/large/008eGmZEgy1gnxgwdrbx7j30mf0mljuu.jpg)

### Array.prototype[@@unscopables]
- 表示不能用到 `with` 语句的作用域内。
- 示例代码
```javascript
console.log([][Symbol.unscopables]);
with(Array.prototype) {
  console.log(forEach);
  console.log(fill);
}
```
![image-20210121140613760](https://tva1.sinaimg.cn/large/008eGmZEgy1gnxgwlsnpdj30id07e3zc.jpg)

## 常用示例
```javascript
Array.from({ 0: 'a', 1: 'b', length: 2 });
Array.isArray([]);
Array.of(1, 2);
[1].concat([2]);
new Array(1, 2);
new Array(2);
[1, 2, 3, 4].copyWithin(1, 0);
[1, 2].entries();
[1, 2].every(i => i > 0);
[0, 0].fill(2);
[0, 1].filter(i => i % 2);
[0, 1].find(i => i == 1);
[0, 1].findIndex(i => i == 1);
[0, [1]].flat();
[0, [1]].flatMap(i => i + 1);
[0, 1].forEach(i => i));
[0, 1].includes(1);
[0, 1].indexOf(1);
[0, 1].join();
[0, 1].keys();
[0, 0].lastIndexOf(0);
[0, 1].map(i => i * 2);
[0, 1].pop();
[0, 1].push(1);
[0, 1, 2].reduce((pre, cur) => pre + cur);
[0, 1, 2].reduceRight((pre, cur) => pre + cur);
[0, 1, 2].reverse();
[0, 1].shift();
[0, 1, 2].slice(1);
[0, 1, 2].some(i => i > 1);
[1, 0, 2].sort();
[0, 1, 2].splice(2, 1);
[0, 1, 2].toString();
[1, 0].unshift(1);
[1, 0].values();
```

### 运行截图

![image-20210121115111132](https://tva1.sinaimg.cn/large/008eGmZEgy1gnxgwomatoj30fr0kh41m.jpg)

## 实现常用的Array函数
- [实现规范参考ECMA规范](https://tc39.es/ecma262/#sec-properties-of-the-array-prototype-object)
```js
class MyArray {
    MyArray() {

    }
    // fn:(value: T, index: number, array: T[]) => void,
    _forEach(fn) {
        for (let i = 0; i < this.length; i++) {
            fn(this[i], i, this);
        }
    }
    // fn:(value: T, index: number, array: T[]) => U,
    _map(fn) {
        let res = [];
        for (let i = 0; i < this.length; i++) {
            res.push(fn(this[i], i, this));
        }
        return res;
    }
    // fn:(previousValue: T, currentValue: T, currentIndex: number, array: T[]) => T
    _reduce(fn, initValue) {
        let pre = initValue;
        for (let i = 0; i < this.length; i++) {
            // let pre = fn() previousValue: U, currentValue: T, currentIndex: number, array: T[]) => U, initialValue: U
            pre = fn(pre, this[i], i, this);
        }
        return pre;
    }
    // fn:(value: T, index: number, array: T[]) =>boolean
    _filter(fn) {
        let res = [];
        for (let i = 0; i < this.length; i++) {
            if (fn(this[i], i, this))
                res.push(this[i]);
        }
        return res;
    }
    // fn:(value: T, index: number, array: T[]) =>boolean
    _some(fn) {
        for (let i = 0; i < this.length; i++) {
            if (fn(this[i], i, this)) return true;
        }
        return false;
    }
    // fn:(value: T, index: number, array: T[]) =>boolean
    _every(fn) {
        for (let i = 0; i < this.length; i++) {
            if (!fn(this[i], i, this)) return false;
        }
        return true;
    }
}
```

### 注意
for in遍历拿不到原型上的属性和方法。
```javascript
// 执行下面代码没有输出
for(let key in Array.prototype){
    console.log(key,Array.prototype[key])
}
```
采用Object.getOwnPropertyNames(MyArray.prototype)来拿到原型上的键,<br/>
将MyArray中的函数挂载到Array.prototype上

```javascript
const keys = Object.getOwnPropertyNames(MyArray.prototype);
keys.forEach(key => {
    if(key!=='constructor'){
        Array.prototype[key]=MyArray.prototype[key];
    }
});

[1,2,3]._forEach(i=>console.log(i))
```

### polyfill补丁实现
```javascript
// 存在就使用，没有加打补丁
Array.prototype.forEach=Array.prototype.forEach||function(fn){
    for (let i = 0; i < this.length; i++) {
      fn(this[i], i, this);
    }
}
```

## 参考
- [MDN-JavaScript标准内置对象Array](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [Ecma-Array Objects](https://tc39.es/ecma262/#sec-properties-of-the-array-prototype-object)

