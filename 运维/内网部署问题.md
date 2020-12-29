## 端口占用问题处理方式
- 端口问题

1. 开启端口

2. 验证端口

```shell script
telnet 127.0.0.1 3000

nc -l 3000 # 开启端口3000服务
nc 127.0.0.1 3000 #客户端连上改服务
# 客户端输入的数据都会原样显示在服务器上
```

3. 查看端口
```shell script
#mac 查看端口被那个进程占用 port:8000
lsof -i:8000  
# pid:871
kill 871 

#windows 查看端口被那个进程占用 port:8000
netstat -aon|findstr "8000"
# pid:871
taskkill /T /F /PID 871 
```


- 网络问题

1. 网络链路
2. 外网进入内网
3. 内网出外网


- 证书问题

```js
https 证书
```

- nginx代理问题

