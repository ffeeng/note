### react入门

函数式组件
```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
类组件 
```js
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

受控组件、非受控组件

纯函数

**所有 React 组件都必须像纯函数一样保护它们的 props 不被更改。**

####  更新已渲染的元素

React 元素是[不可变对象](https://en.wikipedia.org/wiki/Immutable_object)。一旦被创建，你就无法更改它的子元素或者属性。一个元素就像电影的单帧：它代表了某个特定时刻的 UI。

根据我们已有的知识，更新 UI 唯一的方式是创建一个全新的元素，并将其传入 [`ReactDOM.render()`](https://react.docschina.org/docs/react-dom.html#render)。

```
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);
```

安装react调试工具 React Developer Tools(谷歌浏览器插件)

[react调试工具]: https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi

热部署

```
//在index.js中加入
if (module.hot) {
    module.hot.accept();
}
```

