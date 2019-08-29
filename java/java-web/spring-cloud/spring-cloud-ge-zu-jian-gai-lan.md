Eureka, nacos 注册中心
Ribbon, 负载均衡
Hystrix, 降级 熔断
Feign, 代理底层网络通信
Zuul, spring-cloud-gateway  网关，统一鉴权，负载均衡，路由等，做各个服务共同的事情，因为服务互相独立

Config, 分布式配置
Bus 消息总线

为什么用 spring-cloud-gateway？
https://blog.csdn.net/qq_40650378/article/details/83061160


-------------------------------------------------------------

zuul 网关熔断
阿里分布式 事务 框架
rabbitmq  管道 topic
唯一标识
rabbitmq 通讯 负载均衡 socket

-------------------------------------------------------------

SpringCloud是一套目前比较网站微服务框架了，整合了分布式常用解决方案遇到了问题注册中心Eureka、负载均衡器Ribbon ，客户端调用工具Rest和Feign，分布式配置中心Config，服务保护Hystrix，网关Zuul Gateway ，服务链路Zipkin，消息总线Bus等。
 
从架构上分析
Dubbo内部实现功能没有SpringCloud强大（全家桶），只是实现服务治理，缺少分布式配置中心、网关、链路、总线等，如果需要用到这些组件，需要整合其他框架。

spring cloud的不同版本的选择
https://www.liangzl.com/get-article-detail-40511.html

