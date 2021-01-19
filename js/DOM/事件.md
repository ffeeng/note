[TOC]

## 事件转发和事件流
1. 捕获阶段 window->target过程
2. 事件阶段 事件执行
3. 冒泡阶段 target->window过程
![事件流](../../images/js/eventflow.svg)



## 默认行为和可取消事件
```js
let event = MouseEvent();
//停止传播
event.stopPropagation();
//阻止默认行为  例如：表单提交和重置，链接跳转，单选框复选框勾选
event.preventDefault(); defaultPrevented
```
## 同步事件和异步事件

## 信任事件

## 激活触发事件
快捷键 热键  enter alt ctrl之类

## 自定义事件



## 参考
[DOM3规范](https://www.w3.org/TR/DOM-Level-3-Events/#dom-event-architecture)
[UI Event规范](https://www.w3.org/TR/DOM-Level-3-Events/#ui-events-intro)

