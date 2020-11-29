## 问题

- node在安装node-gyp时因为版本太高不支持导致安装失败

![image-20200805175601586](/Users/zego/Library/Application Support/typora-user-images/image-20200805175601586.png)

### 解决方案

- 安装node版本管理模块n

```bat
sudo npm install n -g
```
- 查看目前安装了哪些版本的node

```bat
n ls
```
- 安装最新版本
```bat
n latest
```
- 安装指定版本
```bat
n 10.8.0
```
- 切换版本

```bat
n 10.8.0
```

