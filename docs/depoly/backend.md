# 后端部署

配置 `src/main/resources/config/application.yml` 里面的配置信息:

::: code-group
```yml [application.yml]
server:
  port: 8081 # 后端端口

handsock:
  port: 5120 # 通信端口
  host: 192.168.0.101 # 通信主机
  origin: http://192.168.0.101:5173 # 跨域设置
  openapi: ... # 开放接口密钥 https://doc.handsock.xiaokolomi.cn/depoly/openapi.html
  secretKey: ... # 服务保护密钥（配置为16位长度的字符串）

ai:
  url: https://api.ppinfra.com # AI接口
  path: /v3/openai/chat/completions # AI接口路径
  model: deepseek/deepseek-r1/community # AI模型
  token: ... # AI Token https://ppinfra.com/user/register?invited_by=UUC4HY

spring:
  data:
    redis:
      port: 6379 # Redis端口
      host: localhost # Redis主机
      url: redis://localhost:6379 # Redis连接URL

  servlet:
    multipart:
      max-file-size: 5MB # 文件上传最大大小
      max-request-size: 5MB # 网络请求最大大小
  datasource:
    username: root #数据库用户
    password: 12345678 # 数据库密码
    url: jdbc:mysql://localhost:3306/handsock?useSSL=false&serverTimezone=UTC # 数据库连接URL（handsock为数据库名，必须为handsock）
```
:::

申请DeepSeek大模型密钥：https://ppinfra.com/user/register?invited_by=UUC4HY

其中 `192.168.0.1` 请替换为实际的IP地址或域名，数据库名称暂时只能使用 `handsock`，`origin` 这一项请跟前端的地址一致，否则将导致无法连接（很多人在这里踩了坑）。