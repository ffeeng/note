[TOC]

# http协议历史
## HTTP/0.9 – 单行协议
```bash
GET /mypage.html

<HTML>
这是一个非常简单的HTML页面
</HTML>
```
## HTTP/1.0 – 构建可扩展性
- 加了 Method StatusCode headers
```bash
GET /mypage.html HTTP/1.0
User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)

200 OK
Date: Tue, 15 Nov 1994 08:12:31 GMT
Server: CERN/3.0 libwww/2.17
Content-Type: text/html
<HTML>
一个包含图片的页面
  <IMG SRC="/myimage.gif">
</HTML>
```

## HTTP/1.1 – 标准化的协议
- keep-alive连接复用
- 缓存机制etag lastModified
- 内容协商
- host
- ...

## http/2
- 二进制协议
- 多路复用
- headers压缩
- 服务器推送

## http/3
- QUIC


# http方法 restful
# http状态吗
# header 
## content-type
# 跨域
# 缓存
304
# 重定向
location + 302
# 认证
# https
# 负载均衡
