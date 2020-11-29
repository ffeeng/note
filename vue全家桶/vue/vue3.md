[TOC]

## 1.去掉.sync修饰符

### 2.x

`<MyComponent v-bind:title.sync="title" />` 

### 3.x

`<MyComponent v-model:title="title" />` 

```html
<input v-model="xxx">

<!-- would be shorthand for: -->
<input
  :model-value="xxx"
  @update:model-value="newValue => { xxx = newValue }"
>

<MyComponent v-model:aaa="xxx"/>

<!-- would be shorthand for: -->
<MyComponent
  :aaa="xxx"
  @update:aaa="newValue => { xxx = newValue }"
/>
```

## 2.动态指令参数

```html
<div v-bind:[key]="value"></div>
<div v-on:[event]="handler"></div>
```



## 创建vue3项目

As of v4.5.0, `vue-cli` now provides built-in option to choose Vue 3 preset when creating a new project.

vue-cli 4.5.0以后的版本支持创建vue3项目