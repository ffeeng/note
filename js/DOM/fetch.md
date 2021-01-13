## fetch


## 请求库
### 浏览器端使用
- XMLHttpRequest
- axios 
- fetch
### node中使用
- [axios](https://github.com/axios/axios) 
- [node-fetch](https://github.com/node-fetch/node-fetch)
- [request](https://github.com/request/request)

1. 浏览器自带fetch，浏览器上使用有跨域问题
2. node需安装node-fetch,没有跨域问题

## fetch vs XMLHttpRequest
- fetch使用 Promise,不适用回调、写代码简洁
- fetch采用模块化设计,API分散在Response对象、Request对象、Headers对象,设计更合理
- fetch通过数据流处理数据，分块读取，有利于提高网站性能表现，减少内存占用,对于请求大文件或者网速慢的场景相当有用)

### get请求

- fetch
```javascript
let param = new URLSearchParams({
  roomId:1,
  uid:'1',
})
let url = 'http://localhost:3000/v3/checkin'+'?'+param.toString();
fetch(url).then(response => response.json())
  .then(data => console.log(data));
```

- axios
```javascript
let url = 'http://localhost:3000/v3/checkin';
axios.request( {
    url,
    method: 'GET', 
    params:{
       roomId:1,
       uid:'1',
    },
}).then(response => response.data)
```

### Post、Put请求
- fetch
```javascript
let url = 'http://localhost:3000/v3/checkin';
fetch(url, {
    headers: {
      'Content-Type': 'application/json',
    },
    method: 'PUT', body:JSON.stringify({
           'roomId': 1,
           'uid': '1',
           'info': '{name:"xx",age:2}',
    }),
}).then(response => response.json())
    .then(data => console.log(data));
```
注意Body类型<br>
Body = Blob | BufferSource | FormData | URLSearchParams | ReadableStream<Uint8Array> | string;<br>
Body不能为对象,需用 JSON.stringify(data)

- axios
```javascript
let url = 'http://localhost:3000/v3/checkin';
axios.request( {
    url,
    method: 'POST', 
    data:{
        'roomId': 1,
        'uid': '1',
        'info': '{name:"xx",age:2}',
    },
}).then(response => response.data)
```


### Post formData
- fetch
```javascript
let url = 'http://localhost:3000/v3/checkin';
const formData = new FormData();
form.append('moduleName', 'test');
form.append('img', fs.createReadStream(__dirname + '/1.jpg'));
fetch(url, {
    method: 'POST', body:formData
}).then(response => response.json())
  .then(data => console.log(data));
```
- axios
```javascript
let url = 'http://localhost:3000/v3/checkin';
const formData = new FormData();
form.append('moduleName', 'test');
form.append('img', fs.createReadStream(__dirname + '/1.jpg'));
axios.request( {
    url,
    method: 'POST', data:formData,
    headers:formData.getHeaders()
}).then(response => response.data)
```
- 有formData时不需要设置content-type



## 关于formData
- formData流处理注意 流只能读一次，重置读要做处理
- formData.append('img', fs.createReadStream(__dirname + '/1.jpg'));


## 参考文件
- [Fetch API 教程](http://www.ruanyifeng.com/blog/2020/12/fetch-tutorial.html)
- [axios](https://github.com/axios/axios) 
- [node-fetch](https://github.com/node-fetch/node-fetch)
- [request](https://github.com/request/request)
- [FormData](https://github.com/form-data/form-data#buffer-getbuffer)
