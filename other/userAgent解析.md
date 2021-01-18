## 1.UAParser.js

[npm地址](https://www.npmjs.com/package/ua-parser-js)
[github地址](https://github.com/faisalman/ua-parser-js)

### 浏览器中使用

```javascript
<script type="text/javascript" src="dist/ua-parser.min.js"></script>
<script type="text/javascript">
    var parser = new UAParser();
    var result = parser.getResult();
    
    console.log(result.browser);        
    console.log(result.device);         
    console.log(result.os);             
    console.log(result.os.version);   
    console.log(result.engine.name);   
    console.log(result.cpu.architecture);   
</script>    
```

### nodejs中使用

安装

```javascript
$ npm install ua-parser-js
```

使用

```javascript
var http = require('http');
var parser = require('ua-parser-js');

http.createServer(function (req, res) {
    var ua = parser(req.headers['user-agent']);
    res.end(JSON.stringify(ua, null, '  '));
})
.listen(1337, '127.0.0.1');
console.log('Server running at http://127.0.0.1:1337/');
```

## 2.mobile-detect.js

[npm地址](https://www.npmjs.com/package/mobile-detect)
[github地址](https://github.com/hgoebl/mobile-detect.js)

```js
var MobileDetect = require('mobile-detect'),
var md = new MobileDetect(
    'Mozilla/5.0 (Linux; U; Android 4.0.3; en-in; SonyEricssonMT11i' +
    ' Build/4.1.A.0.562) AppleWebKit/534.30 (KHTML, like Gecko)' +
    ' Version/4.0 Mobile Safari/534.30');
 
// more typically we would instantiate with 'window.navigator.userAgent'
// as user-agent; this string literal is only for better understanding
 
console.log( md.mobile() );          // 'Sony'
console.log( md.phone() );           // 'Sony'
console.log( md.tablet() );          // null
console.log( md.userAgent() );       // 'Safari'
console.log( md.os() );              // 'AndroidOS'
console.log( md.is('iPhone') );      // false
console.log( md.is('bot') );         // false
console.log( md.version('Webkit') );         // 534.3
console.log( md.versionStr('Build') );       // '4.1.A.0.562'
console.log( md.match('playstation|xbox') ); // false
```


## 3.ua-device

- Ua-device是由Baidu WebFE(FEX)团队开发的一个用于解析UA来得到用户终端信息的JS框架

[npm地址](https://www.npmjs.com/package/ua-device)
[github地址](https://github.com/fex-team/ua-device)

```
var UA = require('ua-device');
var input = 'Mozilla/5.0 (iPhone; U; CPU iPhone OS 5_1_1 like Mac OS X; en) AppleWebKit/534.46.0 (KHTML, like Gecko) CriOS/19.0.1084.60 Mobile/9B206 Safari/7534.48.3';
 
var output = new UA(input);
console.log(output);
```

