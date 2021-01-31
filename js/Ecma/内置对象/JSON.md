[TOC]

## JSON.stringify

### 序列化
- 对象转字符串
```javascript
console.log(JSON.stringify({a: 12, b: '2'}));
// 输出 {"a":12,"b":"2"} 
// 自定返回字段 a b 
console.log(JSON.stringify({a: 12, b: '2', c: 3}, ['a','b'], ''))
// 输出 {"a":12,"b":"2"} 

// 自定返回字段 a b 
console.log(JSON.stringify({a: 12, b: '2', c: 3}, null, '\n'))
// 输出 {"a":12,"b":"2"} 
```

## JSON.parse




## 参考

- [MDN JSON](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)
- [ECMA JSON](https://262.ecma-international.org/6.0/#sec-json.stringify)
