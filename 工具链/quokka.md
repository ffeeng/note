[TOC]

## jsDom
```javascript
({
  plugins: ['jsdom-quokka-plugin'],
  jsdom: {html: `<div id="testDiv">Hello</div>`}
})

const testDiv = document.getElementById('testDiv');

console.log(testDiv.innerHTML);
```



## 参考
- [quokka](https://quokkajs.com/)
- [git flow](https://www.cnblogs.com/cnblogsfans/p/5075073.html)
