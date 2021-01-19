[TOC]
## 影子dom例子

## template
## slot
## customElements.define('element-details',...)
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>
<template id="element-details-template">
  <style>
    details {
      font-family: "Open Sans Light", Helvetica, Arial
    }

    .name {
      font-weight: bold;
      color: #217ac0;
      font-size: 120%
    }

    h4 {
      margin: 10px 0 -8px 0;
    }

    h4 span {
      background: #217ac0;
      padding: 2px 6px 2px 6px
    }

    h4 span {
      border: 1px solid #cee9f9;
      border-radius: 4px
    }

    h4 span {
      color: white
    }

    .attributes {
      margin-left: 22px;
      font-size: 90%
    }

    .attributes p {
      margin-left: 16px;
      font-style: italic
    }
  </style>
  <details>
    <summary>
      <span>
        <code class="name">&lt;<slot name="element-name">NEED NAME</slot>&gt;</code>
        <i class="desc"><slot name="description">NEED DESCRIPTION</slot></i>
      </span>
    </summary>
    <div class="attributes">
      <h4><span>Attributes</span></h4>
      <slot name="attributes"><p>None</p></slot>
    </div>
  </details>
  <hr>
</template>

<element-details>
  <span slot="element-name">slot</span>
  <span slot="description">A placeholder inside a web
    component that users can fill with their own markup,
    with the effect of composing different DOM trees
    together.</span>
  <dl slot="attributes">
    <dt>name</dt>
    <dd>The name of the slot.</dd>
  </dl>
</element-details>

<element-details>
  <span slot="element-name">template</span>
  <span slot="description">A mechanism for holding client-
    side content that is not to be rendered when a page is
    loaded but may subsequently be instantiated during
    runtime using JavaScript.</span>
</element-details>
<script>
  customElements.define('element-details',
    class extends HTMLElement {
      constructor() {
        super();
        var template = document
          .getElementById('element-details-template')
          .content;
        const shadowRoot = this.attachShadow({mode: 'open'})
          .appendChild(template.cloneNode(true));
      }
    })
</script>
</body>
</html>
```

## template demo

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>
<table id="producttable">
  <thead>
  <tr>
    <td>UPC_Code</td>
    <td>Product_Name</td>
  </tr>
  </thead>
  <tbody>
  <!-- 现有数据可以可选地包括在这里 -->
  </tbody>
</table>

<template id="productrow">
  <tr>
    <td class="record"></td>
    <td></td>
  </tr>
</template>

<script>
  // 通过检查来测试浏览器是否支持HTML模板元素
  // 用于保存模板元素的内容属性。
  if ('content' in document.createElement('template')) {

    // 使用现有的HTML tbody实例化表和该行与模板
    let t = document.querySelector('#productrow'),
      td = t.content.querySelectorAll("td");
    td[0].textContent = "1235646565";
    td[1].textContent = "Stuff";

    // 克隆新行并将其插入表中
    let tb = document.getElementsByTagName("tbody");
    let clone = document.importNode(t.content, true);
    tb[0].appendChild(clone);

    // 创建一个新行
    td[0].textContent = "0384928528";
    td[1].textContent = "Acme Kidney Beans";

    // 克隆新行并将其插入表中
    let clone2 = document.importNode(t.content, true);
    tb[0].appendChild(clone2);

  } else {
    // 找到另一种方法来添加行到表，因为不支持HTML模板元素。
  }
</script>
</body>
</html>
```

## 参考
- [Web components](https://developer.mozilla.org/zh-CN/docs/Web/Web_Components)
