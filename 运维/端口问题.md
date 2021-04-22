## 查看开启的端口

### liunx

```bash
netstat -nlut
```



## 端口占用

### mac
```shell script
# 查看端口被那个进程占用 port:8000
lsof -i:8000  
# pid:871
kill -9 871 
```

### windows
```shell script
# 查看端口被那个进程占用 port:8000
netstat -ano|findstr "8000"
# pid:871
taskkill /T /F /PID 871 
```
## telnet的作用

- 远程登录主机
```shell script
telnet 127.0.0.1
# 输入账号 密码 登录主机
```

- 判断端口是否开启 
- 建立tcp连接和通信 
```shell script
telnet 172.0.0.1 8000
```

- nc
```js
nc -l 3000 # 开启端口3000服务
nc 127.0.0.1 3000 #客户端连上改服务
# 客户端输入的数据都会原样显示在服务器上
```
