`0.1+0.2!== 0.3`

js number 是 64位浮点数

原因是js 是用浮点数01二进制来表示0.1，它是个近似值

可以用  Number.toFixed(n) 指定进度来解决

- 参考 [JavaScript 浮点数运算的精度问题](https://www.css88.com/archives/7340#more-7340)

