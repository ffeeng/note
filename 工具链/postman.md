# postman

## 管理接口文档
比较简单略

## 设置环境变量
- 全局变量
- 环境变量
- 取值{{url}}

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
- 单个接口测试
### pre-request scripts
pm.body={
  "id": 1,
  "content": "content",
  "pushType": 2,
  "displayType": 1,
  "isPush": true
}

### test
pm.test("Status code name has string", function () {
    console.log(pm.response)
    pm.expect(pm.response.code).to.be.eq(200,'!=200')
    pm.response.to.have.status("OK");
});
pm.test("Response time is less than 200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(200);
});
- 流程测试
### 执行顺序

## 参考
[文档](https://learning.postman.com/docs/writing-scripts/pre-request-scripts/)
