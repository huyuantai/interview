https://mp.weixin.qq.com/s/3TSkT9AYZduJ2CEfAIx7vg?tdsourcetag=s_pcqq_aiomsg
spring boot 项目

# spring boot 启动原理
- 1.起步依赖分析
- 2.自动配置原理


#### 自动配置原理
Spring Boot 的开启注解是：@SpringBootApplication，由下面组成
- @Configuration
- @ComponentScan
- @EnableAutoConfiguration

http://tengj.top/2017/03/09/springboot3/