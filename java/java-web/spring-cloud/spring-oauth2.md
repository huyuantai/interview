https://segmentfault.com/a/1190000013467122
https://zhuanlan.zhihu.com/p/30720675

授权许可
在第一张授权流程图中，前四步包含了获取授权许可获取 access token ,授权许可有四种类型，服务端返回哪种类型取决于客户端在请求链接中构建的 response_type 参数。四种类型的授权许可有不同的应用场景：

- 授权码：通过授权码，服务端通过 Ajax 把 access token 返回给客户端
- 隐式：用于移动 APP 或 web 应用（应用运行在用户的设备上）
- 用户密码凭证：同一个公司不同系统之间内部账户互联互通，比如国内某社区的代码托管系统通过社区的账户也可以登录。
- 客户端凭证：第三方应用自身服务访问提供 OAuth2 服务提供的平台资源


## 代码学习
http://blog.didispace.com/spring-security-oauth2-xjf-1/
http://www.spring4all.com/article/885