## 类数组

arguments是类数组

```javascript
{
  0: 1,
  1: 2,
  length: 2
}
```

## 数组

```javascript
[1,2]
//底层内部实现是类数组结构
{
  0: 1,
  1: 2,
  length: 2
}
new Array(2)
//返回
{
  length: 2
}
Object.keys(new Array(2))== []
Object.keys([1,2])== [0,1]
```

## 空坑问题

![image-20210330164753153](/Users/zego/Library/Application Support/typora-user-images/image-20210330164753153.png)

数组中空坑元素不会被`forEach map some every find reduce`遍历到

## 参考

- [Array构造的数组使用map为何失效？](https://cloud.tencent.com/developer/article/1563458)