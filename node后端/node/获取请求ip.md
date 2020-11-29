### 怎么拿

```js
import {Req} from '@nestjs/common';
import {Request} from "express";
getIp(@Req() req: Request){
	console.log(req.ip);
}
```

### 输出

`::ffff:ip`

### 代理问题

- 当通过nginx代理来转发请求时，拿到的是nginx的IP

### 处理办法

- nginx里添加配置

```nginx
server {
    listen       8080;
    server_name  localhost;
  
    location /v2/ {
        proxy_set_header  Host  $host;
        proxy_set_header   X-Real-IP $remote_addr;  
        proxy_set_header   x-forwarded-for $proxy_add_x_forwarded_for;
        proxy_pass  http://127.0.0.1:3000/v2/;
    }
}
```

- nest后端

```ts
import {Headers} from '@nestjs/common';
getIp(@Headers("X-Real-IP") ip:string){
	console.log(ip);
}
```

  

### 参考

- [nginx指令](https://nginx.org/en/docs/dirindex.html)

- [nginx内置变量](https://nginx.org/en/docs/varindex.html)




