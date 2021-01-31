[TOC]

## 管理接口文档
比较简单略

## 设置环境变量
- 全局变量
- 环境变量
- 取值{{url}}
![image-20210127174523737](https://tva1.sinaimg.cn/large/008eGmZEgy1gn2ea4xfbfj30ud0jrjsy.jpg)

## 发请求
- Get
- Post
- Put
- Delete

## mock服务器
- 创建mock服务器
- 拿到服务器地址 https://424d6056-10c3-41ae-9534-3f7bdc49a5f1.mock.pstmn.io
- 设置请求响应内容

## 自动化测试
### 单个接口测试
执行顺序： pre-request->request->test
- pre-request scripts
pm.body={
  "id": 1,
  "content": "content",
  "pushType": 2,
  "displayType": 1,
  "isPush": true
}
- request
- test
pm.test("Status code name has string", function () {
    console.log(pm.response)
    pm.expect(pm.response.code).to.be.eq(200,'!=200')
    pm.response.to.have.status("OK");
});
pm.test("Response time is less than 200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(200);
});

### 集合测试
排序顺序:接口排列顺序，由上往下执行

## 查看http报文
![image-20210127173910873](https://tva1.sinaimg.cn/large/008eGmZEgy1gn2e3o7w5tj312p0codip.jpg)
## 查看各语言版的请求
![image-20210120194501601](/Users/zego/Library/Application Support/typora-user-images/image-20210120194501601.png)
## 不会查帮助
![image-20210127174125445](https://tva1.sinaimg.cn/large/008eGmZEgy1gn2e5xiibtj30u90mywhp.jpg)


## 参考
[官方文档](https://learning.postman.com/docs/writing-scripts/pre-request-scripts/)
