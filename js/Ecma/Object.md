[TOC]
## Object原型
![image-20210121145123878](https://tva1.sinaimg.cn/large/008eGmZEgy1gmvimsnysvj30cx0jcq5s.jpg)

## 使用示例

```javascript
let obj = { name: 'tony', age: 20 };
console.log(Object.assign({}, obj));
console.log(Object.defineProperties(obj, {
  gender: {
    configurable: true,
    enumerable: true,
    value: 'man',
    writable: true
  }
}));
console.log(Object.defineProperty(obj,
  'gender', {
    configurable: true,
    enumerable: true,
    value: 'man',
    writable: true
  }));
console.log(Object.entries(obj));
console.log(Object.freeze(obj));
console.log(Object.fromEntries([['name', 'tony']]));
console.log(Object.getOwnPropertyDescriptor(obj, 'name'));
console.log(Object.getOwnPropertyDescriptors(obj));
console.log(Object.getOwnPropertyNames(obj));
console.log(Object.getPrototypeOf(obj) === Object.prototype);
console.log(Object.is('', ''));
console.log(Object.isExtensible(obj));
console.log(Object.isFrozen(obj));
console.log(Object.isSealed(obj));
console.log(Object.keys(obj));
console.log(Object.preventExtensions(obj));
console.log(Object.seal(obj));
console.log(Object.setPrototypeOf({}, Array.prototype));
console.log(Object.values(obj));
// Object.prototype上面的方法
console.log(({ name: 'feng' }).hasOwnProperty('name'));
console.log(Object.prototype.isPrototypeOf({}));
console.log(({ name: 'feng' }).propertyIsEnumerable('name'));
console.log(({ name: 'feng' }).toLocaleString());
console.log(({ name: 'feng' }).toString());
console.log(({ name: 'feng' }).valueOf());
```
## 运行截图
![image-20210121185653581](https://tva1.sinaimg.cn/large/008eGmZEgy1gmvimm34fhj30uq0njtef.jpg)

## PropertyDescriptor
```javascript
interface PropertyDescriptor {
    configurable?: boolean;
    enumerable?: boolean;
    value?: any;
    writable?: boolean;
    get?(): any;
    set?(v: any): void;
}
```
### 字段解释
- configurable 可否修改属性描述
- enumerable 可否 for in属性
- value 属性值（不能和 get set同时出现）
- writable 属性值可否修改
- get 去属性值时调用
- set 修改属性值时调用


## Object.getOwnPropertyDescriptor

对象属性描述方法Object.getOwnPropertyDescriptor(o: any, p: PropertyKey): PropertyDescriptor | undefined;
返回定义在这个对象自己身上的属性（而不是继承来的属性）描述

```js

var obj = {
    x: 1,
    foo() {
        console.log(1);
    }
}
console.log(Object.getOwnPropertyDescriptor(obj,'x'));
console.log(Object.getOwnPropertyDescriptor(obj,'foo'));
console.log(Object.getOwnPropertyDescriptor(Array,'prototype'));

```
打印
```out
{ value: 1, writable: true, enumerable: true, configurable: true }
{
  value: [Function: foo],
  writable: true,
  enumerable: true,
  configurable: true
}
{value: Array(0), writable: false, enumerable: false, configurable: false}
```
### 字段的含义
- value<br/>
对象的值
- writable<br/>
属性值是否可以被修改,为true可以修改，为false此时修改无效
```js
const obj = {x:1}
console.log(Object.getOwnPropertyDescriptor(obj,'x'));
Object.defineProperty(obj,'x',{writable:false})
console.log(Object.getOwnPropertyDescriptor(obj,'x'));
obj.x = 2;
console.log(obj)

```
输出
```js
{value: 1, writable: true, enumerable: true, configurable: true}
{value: 1, writable: false, enumerable: true, configurable: true}
{x: 1}
```
- enumerable<br/>
属性值是否可以被for in拿到
```js
for(let key in Array.prototype){
    console.log(key);
}
```
什么都不会打印，为什么什么都不打印,不是有forEach,map,reduce这些方法吗？查看下原型上方法的属性描述
`console.log(Object.getOwnPropertyDescriptor(Array.prototype,'forEach'));`
输出
`{writable: true, enumerable: false, configurable: true, value: ƒ}`
其中enumerable为false,表示该属性不能被for in遍历，修改enumerable为true,这样forEach方法就遍历出来

```js
Object.defineProperty(Array.prototype,'forEach',{enumerable:true})
for(let key in Array.prototype){
    console.log(key);
}
// 打印`forEach`
```

- configurable<br/>
属性描述是否可以修改

执行Object.freeze(obj)就会将对象obj上面的属性描述configurable改成false
此时在定义Object.defineProperty(Obj,'x',{value:2})将会报错
```js
const obj = {x:1}
Object.freeze(obj)
Object.defineProperty(obj,'x',{value:2})

```

报错`Uncaught TypeError: Cannot redefine property: x`

下面这样定义时会报错

```
Object.defineProperty(data, 'name', {
	value: data.name,
    get() {
        return value;
    },
    set(val) {
        if (val !== value) {
            console.log('update')
            value = val;
        }
    },
});
```

TypeError: Invalid property descriptor. Cannot both specify accessors and a value or writable attribute,

## 参考
- [MDN-JavaScript标准内置对象-Object](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object)
- [ECMA-Object实现规范](https://tc39.es/ecma262/#sec-object-objects)

