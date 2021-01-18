# vue3入门

[TOC]

## 1.[slot语法更简短](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0002-slot-syntax-shorthand.md)
### 统一成v-slot,包括局部作用域
```html
<foo>
  <template v-slot:header="{ msg }">
    {{ msg }}
  </template>
</foo>
```
### #号简写
```html
<foo>
  <template #header="{ msg }">
    Message from header: {{ msg }}
  </template>

   <template #footer>
    A static footer
  </template>
</foo>
```

## 2.[动态指令参数](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0003-dynamic-directive-arguments.md)
```html
<div :[key]="value"></div>
<div @[event]="handler"></div>
```

## 3.[树摇](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0004-global-api-treeshaking.md)

### 变化
Currently in 2.x, all global APIs are exposed on the single Vue object:
```js
import Vue from 'vue'
Vue.nextTick(() => {})
const obj = Vue.observable({})
```

In 3.x, they can only be accessed as named imports:
```js
import Vue, { nextTick, observable } from 'vue'
Vue.nextTick // undefined
nextTick(() => {})
const obj = observable({})
```

### Affected 2.x APIs
- `Vue.nextTick`
- `Vue.observable`
- `Vue.version`
- `Vue.compile` (only in full builds)
- `Vue.set` (only in compat builds)
- `Vue.delete` (only in compat builds)

## 4.[增强v-model](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0005-replace-v-bind-sync-with-v-model-argument.md)
Instead of:
```html
<MyComponent v-bind:title.sync="title" />
```

the syntax would be:
```html
<MyComponent v-model:title="title" />
```

## 5.[全局方法改成实例方法](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0009-global-api-change.md)
### Before
```javascript
import Vue from 'vue'
import App from './App.vue'

Vue.config.ignoredElements = [/^app-/]
Vue.use(/* ... */)
Vue.mixin(/* ... */)
Vue.component(/* ... */)
Vue.directive(/* ... */)

Vue.prototype.customProperty = () => {}

new Vue({
  render: h => h(App)
}).$mount('#app')
```
### After
```javascript
import { createApp } from 'vue'
import App from './App.vue'

const app = createApp(App)

app.config.isCustomElement = tag => tag.startsWith('app-')
app.use(/* ... */)
app.mixin(/* ... */)
app.component(/* ... */)
app.directive(/* ... */)

app.config.globalProperties.customProperty = () => {}

app.mount(App, '#app')
```
## 6.[自定义指令](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0012-custom-directive-api-change.md)

### 动机

自定义指令钩子名称和组件生命周期钩子名称一致

### Before

```
const MyDirective = {
  bind(el, binding, vnode, prevVnode) {},
  inserted() {},
  update() {},
  componentUpdated() {},
  unbind() {}
}
```

### After

```
const MyDirective = {
  beforeMount(el, binding, vnode, prevVnode) {},
  mounted() {},
  beforeUpdate() {},
  updated() {},
  beforeUnmount() {}, // new
  unmounted() {}
}
```

## 7.[composition api](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0013-composition-api.md)
```html
<template>
  <button @click="increment">
    Count is: {{ state.count }}, double is: {{ state.double }}
  </button>
</template>

<script>
import { reactive, computed } from 'vue'

export default {
  setup() {
    const state = reactive({
      count: 0,
      double: computed(() => state.count * 2)
    })

    function increment() {
      state.count++
    }

    return {
      state,
      increment
    }
  }
}
</script>
```

## 8.[移除filter](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0015-remove-filters.md)
### 移除动机 
- filter操作符|和逻辑或冲突
- 创造了js不支持的新语法
- 可以被方法和计算属性代替
- 增加实现成本和框架复杂度
```html
<!-- before -->
{{ msg | format }}
<!-- after -->
{{ format(msg) }}
```

## 9.[移除keycode](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0015-remove-filters.md)
### 移除动机 
-  KeyboardEvent.keyCode可以用KeyboardEvent.key替代
```html
<input @keyup.page-down="onArrowUp">
```

## 10.[移除inline-template](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0016-remove-inline-templates.md)
### 移除动机 
-  inline-template让模板作用域不一致
```html
<!-- before -->
<my-comp inline-template :msg="parentMsg">
  {{ msg }} {{ childState }}
</my-comp>

<!-- after -->
<my-comp v-slot="{ childState }">
  {{ parentMsg }} {{ childState }}
</my-comp>
```

## 11.[vue实例上移除事件方法](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0020-events-api-change.md)
Remove $on, $off and $once instance methods.
### 移除动机 
- event emitter API不是组件数据流的一部分


## 12.[移除inline-template](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0023-scoped-styles-changes.md)
Remove $on, $off and $once instance methods.
### 移除动机 
- 保持和css命令一致
```html
<style scoped>
/* deep selectors */
::v-deep(.foo) {}
/* shorthand */
:deep(.foo) {}

/* targeting slot content */
::v-slotted(.foo) {}
/* shorthand */
:slotted(.foo) {}

/* one-off global rule */
::v-global(.foo) {}
/* shorthand */
:global(.foo) {}
</style>
```
### 13.data对象声明
```javascript
import { createApp, h } from 'vue'

createApp().mount({
// 这里只能用函数
  data() {
    return {
      counter: 1,
    }
  }
})
```

## 参考

- [rfcs](https://github.com/vuejs/rfcs/tree/master/active-rfcs)
