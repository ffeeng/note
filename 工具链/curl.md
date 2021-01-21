[TOC]

## curl
和服务器进行传输数据的工具，支持的协议有：
- DICT, FILE, FTP, FTPS, GOPHER,
- HTTP, HTTPS, IMAP, IMAPS, LDAP,
- LDAPS, MQTT, POP3, POP3S, RTMP,
- RTMPS, RTSP, SCP, SFTP, SMB, 
- SMBS, SMTP, SMTPS, TELNET and TFTP

## get请求
```shell script
curl --location --request GET '127.0.0.1:3000/v3/util/userInfo?phone=15271854275' \
--header 'session: abcd'
```

## post json请求
```shell script
curl --location --request GET '127.0.0.1:3000/v3/util/userInfo?page=1&pageSize=10' \
--header 'session: abcd' \
--header 'Content-Type: application/json' \
--data-raw '{
    "phone":15271854275
}'
```

## post application/x-www-form-urlencoded请求
```shell script
curl --location --request POST '127.0.0.1:3000/v3/util/userInfo' \
--header 'session: abcd' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'name=feng' \
--data-urlencode 'age=10'
```

## post formData请求
```shell script
curl --location --request POST 'http://127.0.0.1:3000/v3/public/upload_file' \
--form 'img=@"/Users/zego/Pictures/11.png"' \
--form 'moduleName="room"'
```
## put请求
```shell script
curl --location --request PUT '127.0.0.1:3000/v3/util/userInfo'
```

## delete请求
```shell script
curl --location --request DELETE '127.0.0.1:3000/v3/util/userInfo'
```

## 生成curl工具
- chrome devtool
![image-20210120194544993](https://tva1.sinaimg.cn/large/008eGmZEly1gmuefwv9zsj30j40bmtes.jpg)
- postman
![image-20210120194352840](https://tva1.sinaimg.cn/large/008eGmZEly1gmuefukxaxj310309twfj.jpg)
![image-20210120194501601](/Users/zego/Library/Application Support/typora-user-images/image-20210120194501601.png)

## 参考
- [curl tutorial](https://curl.se/docs/manual.html)
- [curl docs](https://curl.se/docs/)
- [curl everything](https://everything.curl.dev/http/post)
