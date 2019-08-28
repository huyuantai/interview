
https://my.oschina.net/bochs/blog/2248956
Spring Cloud下的微服务权限怎么管？怎么设计比较合理？从大层面讲叫服务权限，往小处拆分，
分别为三块：用户认证、用户权限、服务校验。
微服务架构相关概念：服务注册、服务发现、API 网关
身份认证和用户授权：SSO、CAS、OAuth2、JWT

后台需要需要权限控制
app h5 只需要登录
有些需要限流

网关
https://blog.csdn.net/u010963948/article/details/85016359

不了解项目的auth2 jwt 

auth2 + token  ： token其实就是像session一样，由服务端维护，就像如果客户端禁用了Cookie，我们也可以用在请求添加token，来实现session的效果，这里的token就是这个原理

auth2 + jwt 