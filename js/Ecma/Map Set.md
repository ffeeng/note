[TOC]

# Map
## Map和Object的区别
- Map有序是插入顺序
- Map的健是任意类型，Object的健是String或Symbol
- Map属性个数Size拿到，Object要用其他方法

## 原型对象

<img src="https://tva1.sinaimg.cn/large/008eGmZEgy1gmyvf4jrkvj30p00nqn0u.jpg" alt="image-20210124163337785" style="zoom:67%;" />

## 常用示例
```javascript
let m = new Map([['a','a val']])
console.log(new Map(m))
console.log(m.set('a', 'a val'))
console.log(m.set('b', 'c val'))
console.log(m.has('b'))
console.log(m.get('a'))
console.log(m.forEach((value, key, map) =>
  console.log(value, key, map)))
console.log(m.size)
console.log([...m])
console.log([...m.entries()])
console.log([...m.keys()])
console.log([...m.values()])
console.log(m.clear())
```

## 运行截图
![image-20210125102408905](https://tva1.sinaimg.cn/large/008eGmZEgy1gmzqaaqdsdj317s0gi78o.jpg)

## WeakMap WeakSet
持有每个健对象的弱引用，在没有其他引用存在时垃圾回收能正确进行

# Set

set和map原理基本相同，采用hash算法，桶+链表的实现方式，set是一列，map是两列。

## 常用示例
```javascript
let s = new Set(['a','b'])
console.log(s.add('a'))
console.log(s.add('b'))
console.log(s.has('a'))
console.log(s.forEach((value, key, s) =>
  console.log(value, key, s)))
console.log(s.size)
console.log([...s])
console.log([...s.entries()])
console.log([...s.keys()])
console.log([...s.values()])
console.log(s.clear())
```
## 运行截图
![image-20210125101529507](/Users/zego/Library/Application Support/typora-user-images/image-20210125101529507.png)






# 参考
- [MDN Map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map)
- [MDN WeakMap](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)

