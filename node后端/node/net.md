## net模块

## server
```js
let net = require('net')

let server = net.createServer(function(socket){
  socket.on('data',function(data){
    socket.write('hello')
  })
  socket.on('end',function(data){
    socket.write('break')
  })
  socket.write('welcome')

})

server.listen(8000,function(e){
  console.log('server bound',e);
})
```


## client
```js
let net = require('net')

let client = net.connect({port:8000},function(){
  console.log('client connected');
  client.write('world!\r\n');
});

client.on('data',function(data){
  console.log(data.toString());
  client.end();
})

client.on('end',function(data){
  console.log('client disconnected');
})

```


## 常用文件操作


